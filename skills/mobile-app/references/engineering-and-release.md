# Engineering and Release

Use this reference for stack choice, architecture, state, data, offline behavior, privacy, security, performance, lifecycle, testing, observability, and release.

## Contents

1. Select the implementation strategy
2. Define architecture and state ownership
3. Design data, sync, and offline behavior
4. Protect privacy and security
5. Budget and measure performance
6. Survive the mobile lifecycle
7. Test the product in layers
8. Prepare, release, and operate
9. Apply the definition of done

## 1. Select the implementation strategy

Choose native, cross-platform, or shared-domain architecture from constraints rather than fashion.

Record:

```text
Target platforms and minimum/current OS:
Phone, tablet, foldable, watch, or other surfaces:
Platform APIs and hardware:
Background and offline requirements:
Interaction and performance sensitivity:
Accessibility requirements:
Team skills and hiring:
Existing code and services:
Release cadence:
Expected product lifetime:
Third-party SDK and library risk:
Build, test, debug, and store tooling:
```

Compare:

| Strategy | Prefer when | Cost to examine |
| --- | --- | --- |
| Separate native apps | Deep platform integration, demanding interaction, independent platform experiences | Duplicate product/domain work and staffing |
| Shared UI/runtime | Similar cross-platform experience, small team, mature needed integrations | Native escape hatches, upgrades, bundle/runtime cost, platform fidelity |
| Shared domain/data with native UI | Shared rules are substantial but platform experience matters | Boundary design, interop, debugging, build complexity |
| Mobile web/PWA | Distribution and instant access dominate; device needs are modest | Platform capability, background behavior, store presence, offline limits |

Prototype the highest-risk dependency before committing: background execution, media, maps, Bluetooth, health, camera, payments, passkeys, widgets, accessibility, large lists, animation, or an immature SDK.

Prefer maintained platform and ecosystem components. Verify release cadence, issue health, license, binary impact, platform support, accessibility, security history, and exit cost before adopting a dependency.

Do not introduce a framework-wide abstraction to avoid writing a small amount of platform-specific code.

## 2. Define architecture and state ownership

Use clear boundaries:

```text
UI and navigation
    -> presentation/state holder
        -> domain rules/use cases where needed
            -> repositories/data interfaces
                -> local, remote, and platform implementations
```

Keep the dependency direction inward. Platform, network, database, analytics, billing, and model providers implement boundaries; domain rules do not import them.

Do not add a layer with no independent responsibility. A small feature may need a view state and repository, not a ceremonial use-case class for every function.

Establish:

- one authoritative owner for each state;
- immutable or predictably observable state;
- explicit events/actions;
- one-way state flow;
- derived state rather than duplicated flags;
- structured concurrency and cancellation;
- typed domain failures;
- dependency injection at external boundaries;
- versioned contracts between app and backend.

Model mutually exclusive states within each axis, then compose them:

```text
content: idle | loading(previous?) | empty | ready(data) | error(kind, previous?)
connectivity: online | offline | reconnecting
freshness: unknown | current(asOf) | stale(asOf)
mutation: idle | pending(intent) | failed(retry?) | outcomeUnknown(attempt)
```

Define allowed transitions and cross-axis invariants. Connectivity, freshness, content, indexing, and a pending mutation can legitimately coexist; do not flatten every combination into one giant enum. Avoid independent booleans such as `isLoading && hasError && isEmpty` that allow impossible state.

Define navigation from state and intent without putting mutable business state inside route strings. Validate every deep link and reconstruct a plausible, authorized task stack.

Treat each external integration or companion surface as a product and reliability boundary:

```text
Host workflow and user job:
Entry surface and return path:
System of record and data ownership:
Permission and data scope:
Authentication, refresh, and revocation:
Latency, offline, and version mismatch:
Duplicate, partial failure, and fallback:
Deep-link, back, and restoration behavior:
Observability, rate/cost limits, and support:
Provider dependency, degradation, and exit plan:
```

For mobile, consider the smallest useful surface: share sheet, widget, OS intent or shortcut, notification action, deep link, wearable, companion device, or provider workflow. Preserve context when the full app is needed. Optimize completion of the beneficial job, not forced full-app opens.

Assume an extension or companion surface can start cold, in another process, while the device is locked, without the main app's current session, and at a different schema version. Use a minimal versioned shared-container schema, narrow key/access groups, no long-lived privileged credential in shared storage, privacy-safe timestamped snapshots, idempotent low-risk actions, and migration/corruption recovery. Hand consequential work to the authenticated app for fresh review.

Wrap provider-specific models and SDKs at an owned boundary. Pin and test supported versions, verify webhook or callback authenticity, tolerate delayed and duplicated events, expose degraded state, and keep a migration or disablement path when the provider changes or fails.

Keep UI-thread work small. Run I/O, parsing, image processing, cryptography, database migration, and model inference off the main thread. Cancel work when its result is no longer relevant.

Make analytics observe product events; do not let analytics calls control business logic or navigation.

## 3. Design data, sync, and offline behavior

Name the source of truth for every entity and operation.

Use local-first or offline-first behavior only when it solves a real need. Define:

```text
Readable offline:
Writable offline:
Freshness rule:
Pending representation:
Queue ordering:
Retryable failures:
Idempotency key:
Conflict policy:
User-visible recovery:
Storage and eviction:
```

Choose conflict behavior deliberately: server wins, client wins, field merge, append-only merge, or user resolution. Never silently discard work.

For mutations:

- persist user-critical intent before presenting success;
- use stable client-generated identifiers where useful;
- make create, send, upload, payment, and tool actions idempotent;
- show pending, failed, and synced states;
- retry only transient failures with bounded backoff and jitter;
- prevent duplicate execution after timeout or process restart;
- provide cancel or undo where the domain supports it.

Distinguish a known rejection or pre-submission failure from an unknown outcome after a request may have reached the authoritative system. Persist the attempt and idempotency key, reconcile by that identity, show “checking status,” and block blind resubmission until the original outcome is resolved.

For payments, publication, sending, deletion, permission changes, and other high-consequence work, allow an offline draft but do not queue the authorization itself for automatic execution. On reconnect, refresh material state and require fresh confirmation.

For money, paid units, credits, entitlements, or other conserved balances, keep a server-authoritative ledger:

- create immutable, idempotent entries for grants, holds, spends, settlement, refunds, reversals, expiry where permitted, and corrections;
- derive balances from reconciled entries instead of trusting a client-maintained total;
- make pending, settled, failed, reversed, and corrected states explicit;
- use compensating entries rather than rewriting history;
- reconcile provider events, duplicate or delayed callbacks, and balance drift;
- retain an access-controlled audit trail and user-visible transaction history;
- treat the mobile balance as a timestamped cache, never spending authority.

Cache with a purpose and freshness contract. Show stale data honestly. Bound memory and disk caches by count/size/age, and avoid caching sensitive data that the product does not need offline.

Design migrations before shipping schema changes:

- make them transactional and restart-safe;
- test from every supported production version;
- preserve forward/backward compatibility during staged app/backend rollout;
- back up or validate critical data;
- define recovery when migration fails or storage is full.

Treat time, timezone, locale, calendar, daylight-saving changes, and clock skew as data concerns. Store canonical instants plus the context needed to render or repeat a local schedule correctly.

## 4. Protect privacy and security

Threat-model with the current OWASP MASVS and applicable backend standard. Cover storage, cryptography, authentication, network, platform interaction, code, resilience, and privacy.

Assume the binary and device are attacker-controlled:

- never ship server credentials, administrator secrets, or master keys;
- never trust a client-side entitlement, role, price, limit, or authorization decision;
- authorize every resource and action on the server;
- validate inputs again at each trust boundary;
- rotate and revoke credentials;
- minimize offline authority.

Store session secrets and private keys in platform secure storage such as Keychain or Keystore-backed facilities with the narrowest compatible access. Clear appropriate credentials at logout and account deletion.

Require secure transport. Do not ship trust-all certificate logic, hostname bypasses, or broad transport exceptions. If pinning is justified, include backup pins and a tested rotation/recovery plan.

Harden platform entry points:

- default components and intents to non-exported/private;
- allowlist deep-link schemes, hosts, routes, and parameters;
- validate caller identity, file/URI grants, and shared content;
- use platform selectors and share sheets;
- avoid WebViews for sensitive work;
- if a WebView is necessary, allowlist origins/navigation and disable unnecessary script, file, bridge, and mixed-content capability.

Maintain one data inventory across app, backend, analytics, crash reporting, advertising, attribution, support, and every SDK:

```text
Data:
Sensitivity and data class:
Source:
Purpose:
Recipient/processor:
Retention:
Local storage, file protection, and key owner:
OS-device backup eligibility:
Service backup, restore, and deletion:
Transport:
Consent or other basis:
Logout and account-switch behavior:
User access/export/deletion:
Store disclosure:
```

Initialize collection only after applicable choice. Generate store privacy disclosures from this inventory. Reconcile what SDKs actually collect, not only what their marketing pages claim.

Exclude credentials, tokens, private prompts, message contents, financial/health details, and unnecessary identifiers from logs, analytics, crash reports, clipboard, and notifications by default. Redact app-switcher previews and product-generated support/store captures; use platform capture controls where justified, but do not promise that all user screenshots can be prevented.

Decide OS-device backup eligibility per data class. Encrypt and access-control any necessary service backup separately, with tested restore, key rotation, retention, account binding, and deletion. Clear account-scoped local data on logout or account switch unless an explicit safe offline model requires otherwise.

Keep a dependency/SDK inventory, update policy, vulnerability response process, and preferably an SBOM. Remove SDKs whose value does not justify their data, security, binary, and startup cost.

If accounts exist, implement actual account deletion and associated data handling, not a local “deactivated” flag. Explain lawful retention and subscription cancellation separately. Recheck current store requirements before release.

## 5. Budget and measure performance

Set budgets from important journeys and representative devices:

```text
Cold start: first visible frame and fully usable state
Input feedback and action completion
Scroll/animation frame stability
Network payload and p95 latency
Memory peak and retained memory
Battery/thermal use
Disk and cache growth
Download/install size
Background work
```

Measure both perceived and actual completion. A fast splash followed by a blocked home screen is not a fast launch.

On Android, measure time to initial display and time to fully drawn. On Apple platforms, inspect launch, hangs, responsiveness, memory, disk, and energy with current Xcode tooling. Use the platform's production telemetry as well as local profiling.

Profile:

- signed/optimized release builds;
- cold and warm states;
- lower-end physical devices;
- large realistic datasets;
- poor, lossy, and reconnecting networks;
- low storage, low battery, and thermal pressure;
- accessibility settings and large text;
- background/foreground and process recreation.

Lazy-initialize nonessential SDKs and services. Avoid blocking initial render on data that can arrive progressively. Decode and resize images for their rendered use, paginate/bound lists, and cancel obsolete requests.

Track crash-free use, hangs/ANRs, frozen or slow frames, startup, memory, energy, payload, and failed core journeys by version and device class. Query current platform/store thresholds rather than freezing them in the skill.

Never use animation to hide unbounded latency. Provide truthful status, cancellation, retry, and background completion when suitable.

## 6. Survive the mobile lifecycle

Assume the process can disappear without a cleanup callback.

Persist durable user intent when it occurs. Use lightweight saved state for navigation keys and in-progress UI; use durable storage for large or critical content.

Test:

- background and immediate return;
- background eviction/process death;
- configuration and window-size change;
- OS reclaiming memory;
- authentication expiry;
- permission revocation while absent;
- network handoff and reconnect;
- deep link or notification into a cold app;
- app update and data migration;
- device reboot during scheduled work.

Do not perform critical durable work only in a pause, disappear, termination, or destructor callback.

Make background work:

- justified by user value;
- scheduled through supported platform APIs;
- idempotent and uniquely identified where needed;
- cancellable;
- constrained by power, connectivity, and policy;
- safe when it runs much later than requested;
- resumable or compensatable after expiration.

Design notifications and deep links to revalidate current state. A stale notification must not repeat a purchase, send, approval, or destructive action.

Handle limited storage, corrupted cache, missing files, database failure, and unsupported server versions. Preserve recoverable user data and offer a safe reset only after other recovery fails.

## 7. Test the product in layers

Use the smallest layer that proves each behavior:

- pure unit tests for domain rules, reducers, parsers, schedules, and conflict logic;
- repository/database/network tests for caching, retry, migration, and contracts;
- component tests for state rendering, semantics, focus, and interaction;
- integration tests for platform services, auth, billing, notifications, and deep links;
- end-to-end tests for a few critical journeys;
- exploratory and usability testing for behavior automation cannot judge.

Contract-test mobile/backend compatibility and tolerate the version skew created by staged releases.

Derive dynamic security tests from the threat model. Proportionally cover object/tenant authorization, local storage extraction and account-switch leakage, deep-link/intent/URI/WebView abuse, webhook or callback forgery, replay/tampering, transport configuration, credential revocation, and high-risk penetration testing.

Run signed optimized builds. Debug builds can hide optimizer, permission, timing, network-security, and configuration defects.

Cover a release matrix proportional to the product:

- minimum and current OS versions;
- phone, tablet, foldable, compact/expanded windows;
- portrait, landscape, split-screen, and resize;
- light, dark, increased contrast, maximum text;
- screen reader, voice, switch, and keyboard input;
- locales, RTL, long translation, calendar, timezone, 12/24-hour time;
- offline, slow, lossy, captive, and reconnecting networks;
- permission grant, limited, denial, “don't ask again,” and revocation;
- low storage/memory, interruption, auth expiry, deep-link entry;
- fresh install, upgrade, migration, reinstall, and account switch;
- purchase, pending, retry, renewal, grace, expiry, refund, revocation, restore, and cancellation.

Test service-backup restoration, data corruption, key rotation, provider outage, and declared recovery objectives when the architecture relies on them.

Use platform automated accessibility checks, pre-launch/device reports, beta distribution, and crash tooling as supplements. Manually complete common tasks with assistive technology and on physical devices.

## 8. Prepare, release, and operate

Before release:

- freeze a production-shaped release candidate;
- run lint, static analysis, unit/integration/UI tests, dependency and secret checks;
- validate signing, environments, feature flags, and production endpoints;
- verify store metadata, screenshots, age/content rating, support, privacy, and data declarations;
- provide review credentials or full demo mode plus non-obvious instructions;
- test account deletion, export, restore purchase, subscription lifecycle, and support links;
- symbolize/obfuscation-map crash reports;
- verify analytics without sensitive payloads;
- load-test or capacity-test the backend where risk warrants;
- rehearse migration, rollback, and incident response.

Use server-compatible feature flags and kill switches for risky features. A mobile rollback is slow; the server must tolerate the previous and new client during rollout.

Roll out gradually. Monitor by app version, platform, device, country, and relevant cohort:

- activation and beneficial outcome;
- core-journey failure;
- crash, hang/ANR, startup, frame, memory, and network;
- authentication and sync;
- purchase and entitlement;
- complaint, refund, privacy, safety, and accessibility signals.

Define stop/rollback thresholds before rollout. Pausing a staged rollout does not remove a bad binary already installed, so disable the affected server capability or provide a forward fix when necessary.

Maintain an operational owner, dashboards, alerts, support playbook, status communication, and post-incident learning. Do not collect sensitive payloads merely to make debugging easier.

Apply a policy freshness gate before architecture decisions that depend on rules and again before release:

1. Identify platforms, storefronts/countries, app category, account model, child-directed status, regulated-domain status, data classes, permissions, payment model, SDKs, and AI behavior.
2. Recheck the current Apple App Review Guidelines and upcoming requirements.
3. Recheck Google Play policy deadlines, target API requirements, billing/payment rules, and regional programs.
4. Recheck privacy forms/manifests, account deletion, accessibility labels, subscription disclosures, and high-risk permissions.
5. Cite the pages and access date in the project decision record.

Do not hard-code SDK deadlines, billing exceptions, regional eligibility, review workarounds, privacy schemas, or store quality thresholds.

## 9. Apply the definition of done

A mobile slice is done only when the relevant evidence exists:

```text
[ ] Acceptance scenarios pass
[ ] Loading, empty, partial, offline, error, success, and recovery states work
[ ] Back, deep link, interruption, and process recreation behave correctly
[ ] Accessibility semantics and manual task tests pass
[ ] Text scaling, contrast, reduced motion, locale, and RTL are handled
[ ] Permissions and denial paths are contextual and usable
[ ] Sensitive data and logs match the data inventory
[ ] Authorization and security boundaries are verified
[ ] Performance budgets pass on representative physical hardware
[ ] Analytics prove value/failure without unnecessary personal data
[ ] Unit, integration, and critical journey tests pass in a release build
[ ] Migration, feature flag, monitoring, and rollback are ready
[ ] Current platform and store requirements were checked
[ ] Tradeoffs and remaining risks are recorded
```

Tailor the list to risk. Do not waive trust, accessibility, security, or recovery merely because a feature is labeled MVP.
