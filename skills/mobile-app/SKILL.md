---
name: mobile-app
description: "Plan, design, build, audit, and improve trustworthy mobile apps for iOS, Android, and cross-platform stacks. Use for mobile product strategy, category research, acquisition, store presence, and MVP scoping; user journeys, navigation, search, dashboards, screens, design systems, motion, and accessibility; onboarding, permissions, notifications, retention, gamification, paywalls, subscriptions, consumables, and virtual currency; mobile architecture, integrations, state management, offline behavior, security, performance, testing, analytics, store readiness, and release; or AI-assisted and agentic mobile experiences. Also use when reviewing an existing mobile app or repository for product, UX, engineering, growth, or trust problems."
---

# Mobile App

## Follow the doctrine

Build the smallest coherent product that repeatedly produces a beneficial user outcome.

Apply these priorities in order:

1. Foundation before finish.
2. Outcome before screen.
3. Clarity before compulsion.
4. Agency before retention.
5. Evidence before confidence.

Treat utility, craft, emotion, growth, and monetization as one system. Never let polish conceal weak value, let engagement replace user benefit, or let conversion override informed choice.

## Route the request

Load only the references needed for the current work:

| Work | Read |
| --- | --- |
| New concept, category research, product brief, acquisition/store promise, MVP, roadmap, prioritization, analytics, or experiment | [product-and-measurement.md](references/product-and-measurement.md) |
| User flows, information architecture, navigation, search, dashboards, screens, forms, visual hierarchy, interaction, motion, design systems, or accessibility | [experience-and-interface.md](references/experience-and-interface.md) |
| First run, sign-up, personalization quiz, permissions, trial, paywall, subscription, purchase, consumable, virtual currency, or cancellation | [onboarding-and-monetization.md](references/onboarding-and-monetization.md) |
| Retention, notifications, habits, progress, streaks, rewards, competition, social proof, sharing, or referrals | [engagement-and-ethics.md](references/engagement-and-ethics.md) |
| Stack choice, architecture, integration, companion surface, implementation, data, offline behavior, security, performance, testing, observability, or release | [engineering-and-release.md](references/engineering-and-release.md) |
| AI generation, recommendations, personalization, assistants, agents, tool use, or autonomous actions | [ai-and-agentic.md](references/ai-and-agentic.md) |

For an early concept or product plan, read product and measurement first and add experience and interface when shaping journeys or screens. When the request includes implementation or architecture, read product and measurement, then experience and interface, then engineering and release. Add the other conditional references only when the product uses those capabilities.

## Run the working loop

### 1. Inspect before prescribing

Inspect the repository, current product artifacts, platform targets, stack, design system, analytics, tests, release setup, and existing conventions. Preserve sound decisions already present.

For an unstarted product, establish or explicitly assume:

- target user and use context;
- problem, desired outcome, and current alternative;
- platform and device scope;
- business model and launch constraint;
- sensitive data, safety, legal, or accessibility stakes;
- team capabilities and delivery horizon.

Ask only questions whose answers materially change the result. Otherwise state a reversible assumption and continue.

### 2. Define the product spine

Write a one-sentence promise:

> For [user] in [situation], the app helps them [outcome] by [mechanism], unlike [current alternative].

Then define:

- the first value event;
- the repeatable beneficial outcome;
- the smallest action that produces evidence of that outcome;
- why a user would deliberately return;
- one user-outcome metric;
- one business metric;
- one trust, harm, or accessibility countermetric;
- explicit non-goals.

Do not use app opens, session length, screen count, or notification opt-in as primary proof of value.

### 3. Classify risk before removing friction

Classify each important flow by:

- utility versus experience;
- repetitive versus judgment-heavy;
- low versus high consequence;
- reversible versus irreversible;
- ordinary versus sensitive data;
- deterministic versus uncertain output.

Automate repetitive, low-risk, reversible work when the user's intent is established, the result is predictable, status is visible, and undo is easy. Add preview, explanation, confirmation, auditability, and recovery as consequence or uncertainty rises. Keep interaction when participation is part of the value.

### 4. Map the shortest ethical journey

Map entry, first value, repeat value, payment if any, recovery, and exit. Include:

- happy path;
- loading and long-running work;
- empty and no-results states;
- partial or stale data;
- offline and reconnecting behavior;
- denied or revoked permissions;
- recoverable and terminal errors;
- interruption, backgrounding, process death, and return;
- destructive actions, undo, and restoration;
- accessibility and localization variants.

Remove steps that serve only internal metrics. Preserve effort that creates value, improves safety, or enables informed choice.

### 5. Decide before building

Record material decisions with:

```text
Decision:
Target user outcome:
Evidence or assumption:
Affected states:
Implementation implications:
Primary metric:
User-harm guardrail:
Accessibility/privacy considerations:
Rollback condition:
```

Select the stack and architecture from product constraints, device capabilities, team ownership, quality needs, and lifecycle cost. Do not choose from trend or familiarity alone.

### 6. Build vertical slices

Deliver one end-to-end outcome at a time: interface, state, domain rule, data boundary, analytics, accessibility, tests, and failure handling together.

For each slice:

1. State the acceptance scenarios and non-goals.
2. Model all meaningful states explicitly.
3. Establish one source of truth and clear ownership.
4. Implement the simplest complete path.
5. Add semantic accessibility and platform behavior during implementation.
6. Instrument the value event and failure points without collecting unnecessary personal data.
7. Verify on representative physical devices and adverse conditions.
8. Record tradeoffs and follow-ups.

Avoid horizontal construction that produces a polished shell with no complete user outcome.

### 7. Pass the quality gates

Do not call work complete until it passes the relevant gates:

- **Value:** Produce the promised outcome for the intended user.
- **Clarity:** Make the next action, system status, cost, and consequence understandable.
- **Agency:** Make optional actions optional; provide back, skip, pause, undo, cancel, export, reset, and delete where applicable.
- **Trust:** Minimize data, request permissions in context, secure boundaries, and state limitations honestly.
- **Inclusion:** Support assistive technology, text scaling, contrast, non-color cues, reduced motion, alternative input, and localization.
- **Resilience:** Handle latency, offline use, retries, interruption, duplication, stale state, migration, and recovery.
- **Performance:** Measure startup, responsiveness, frame stability, memory, battery, network, and app size on realistic hardware.
- **Observability:** Detect crashes, hangs, failed journeys, regressions, and harmful outcomes.
- **Policy:** Recheck current store, billing, privacy, accessibility, and regulated-domain rules from primary sources.

### 8. Learn without trapping

Turn behavioral patterns into testable hypotheses, not universal laws. Before an experiment, define the beneficial outcome, exposure unit, segment, primary metric, business metric, harm countermetrics, qualitative follow-up, stopping rule, and rollback condition.

Prefer improvements that increase repeat value, competence, confidence, or saved effort. Reject improvements that increase a metric by confusing, pressuring, shaming, exhausting, or locking in the user.

## Enforce the red lines

Do not design or implement:

- fake progress, activity, scarcity, urgency, personalization, testimonials, or social proof;
- hidden prices, disguised ads, unclear renewal, preselected consent, confirmshaming, or obstructed dismissal;
- harder cancellation, export, deletion, or account exit than the corresponding entry;
- threatened loss of earned value, punitive streaks, public shame, or paid relief from anxiety;
- variable-ratio monetization, disguised gambling, or celebration of risky financial behavior;
- forced contacts access, invitations, sharing, ratings, or notifications;
- identity labels presented as diagnostic truth;
- deliberate non-portability or hidden scoring intended to make departure painful;
- consequential AI actions without appropriate review, confirmation, recovery, and auditability.

When asked for one of these, explain the trust risk and propose an ethical mechanism that pursues the legitimate product goal.

## Calibrate evidence

Use this order of confidence:

1. Direct user evidence, product data, and repository behavior.
2. Current platform policy and official technical documentation.
3. Original research or controlled experiments applicable to the context.
4. Credible case studies and comparable-product evidence.
5. Design and practitioner heuristics, plus analogy.

Label inference and uncertainty. Never present a case-study correlation, an isolated statistic, or psychology shorthand as causal proof. Verify temporally unstable claims at task time.

## Shape the deliverable

Match the output to the request:

- For a **new product**, provide the product spine, key journey, MVP vertical slices, decision/risk register, and measurement plan.
- For a **feature**, provide scenarios, state model, implementation, analytics, accessibility, tests, and verification.
- For a **design**, explain hierarchy, behavior, states, platform adaptation, accessibility, and motion—not only the happy-path frame.
- For an **audit**, lead with severity-ranked findings, evidence, user/business impact, and concrete fixes.
- For an **experiment**, use the experiment card in product and measurement.
- For a **release**, report evidence for each relevant quality gate, remaining risks, monitoring, and rollback.

Lead with the recommendation or completed outcome. Keep generic checklists out of the response unless they directly evaluate the product at hand.
