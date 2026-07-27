# AI and Agentic Mobile Experiences

Use this reference when a mobile app generates content, recommends decisions, learns preferences, calls tools, or acts on a user's behalf.

## Contents

1. Classify the AI role and risk
2. Define the task contract
3. Design understandable control
4. Protect data and actions
5. Handle personalization without lock-in
6. Evaluate the whole system
7. Design mobile runtime states
8. Release and monitor safely

## 1. Classify the AI role and risk

Identify the role:

- **Generate:** Draft content for review.
- **Summarize or extract:** Transform supplied information.
- **Recommend:** Rank or advise while the user decides.
- **Assist:** Prepare a sequence of actions.
- **Act:** Mutate an external or local system.
- **Autonomously pursue:** Choose and execute multiple steps toward a goal.

Then classify:

```text
Consequence: low / medium / high
Reversibility: easy / costly / impossible
Data sensitivity: ordinary / personal / highly sensitive
Output uncertainty: bounded / material / safety-critical
Tool authority: read / draft / write / transact / publish
Affected party: user only / known collaborators / third parties / public
```

Remove intermediate screens for low-risk, reversible utility work. Retain comparison and direct manipulation when the interaction itself creates understanding or enjoyment. As risk rises, require clearer scope, preview, confirmation, provenance, audit, and recovery.

Before adding an AI-specific screen or chat, run the interface-necessity test:

```text
Could an assistant complete the mechanical job without opening this app?
If yes, what valuable participation remains?
- understanding or comparison
- direct manipulation or creation
- supervision and confirmation
- collaboration or genuine community
- provenance, audit, and recovery

If none remains, can the outcome be delivered safely through an existing
surface, OS intent/shortcut, widget, notification action, deep link, or API?
```

Do not manufacture a social feed, identity score, public competition, or extra interaction merely to create an agent-resistant moat.

## 2. Define the task contract

Before implementation, specify:

```text
User job and success:
Inputs and allowed sources:
Expected output or action:
Known limitations:
Latency and cost budget:
Freshness requirement:
Privacy and retention:
Tools and maximum authority:
Human review point:
Fallback:
Evaluation set:
Failure and rollback:
```

Use deterministic software for deterministic rules. Do not delegate authorization, money math, eligibility, safety limits, or irreversible state transitions solely to a probabilistic model.

Separate:

- model-generated proposal;
- deterministic validation;
- policy and authorization;
- actual side effect.

For a transactional or multi-tool run, keep a server-authoritative execution record:

```text
Run ID, owner, and status:
Versioned plan and canonical action set:
Authority scope and expiry:
Step, cost, and time limits:
Per-step idempotency keys:
Confirmed proposal hash or canonical parameters:
Checkpoint and resume policy:
Partial, outcome-unknown, and compensation state:
```

Bind confirmation to the exact proposal reviewed. A material change in input, scope, price, external facts, model/tool version, or canonical action parameters invalidates the confirmation and requires a fresh preview. Never resume merely from an untrusted client step index.

## 3. Design understandable control

Always make system status truthful:

- waiting for a model;
- searching or retrieving;
- drafting;
- using a named tool or data source;
- awaiting review;
- executing;
- partially complete;
- failed, canceled, or rolled back.

Do not use fake progress. For uncertain duration, show activity and the current phase without invented percentages.

Give users:

- clear scope before an action;
- editable inputs and instructions;
- preview and diff for material changes;
- explicit confirmation near the consequence;
- stop or cancel;
- undo or compensating action;
- history of what changed and why;
- correction and feedback;
- manual path or safe fallback.

Prefer improving an existing familiar interaction when it preserves comprehension, correction, and user control. Do not introduce a generic chat or separate “AI mode” when a ranked list, suggestion, draft, inline completion, or direct manipulation expresses the job more clearly. Disclose AI involvement, source, uncertainty, and controls whenever inference or consequence is material.

Batch confirmations only when the user can inspect the batch, understand its range, exclude items, and later audit each action. Reconfirm when scope or consequence changes.

Communicate uncertainty proportionally. Use sources, evidence, confidence ranges, alternatives, or a request for clarification when they help the decision. Do not add a generic disclaimer to unreliable output and call it safe.

Avoid deceptive anthropomorphism. A warm voice is acceptable; false claims of feelings, consciousness, certainty, professional qualification, or human review are not.

## 4. Protect data and actions

Treat model output, retrieved content, tool results, URLs, documents, and inbound messages as untrusted.

Enforce:

- server-side authentication and authorization for every action;
- least-privilege, short-lived, scoped credentials;
- tenant and user isolation;
- allowlisted tools and parameters;
- deterministic schema and business-rule validation;
- idempotency for retryable writes;
- transaction limits and rate/cost budgets;
- explicit boundaries between instructions and untrusted content;
- audit logs without secrets or unnecessary personal data;
- safe rendering and sanitization;
- prompt-injection and data-exfiltration tests;
- revocation, kill switch, and incident response.

Never place provider secrets or privileged tool credentials in the mobile client. Assume client code, local storage, traffic metadata, and prompts can be inspected.

Do not queue a consequential authorization for automatic execution after reconnect. Preserve a draft, then refresh the affected facts, permissions, limits, and external state and require fresh confirmation while online.

Minimize model inputs. Redact or transform data before sending it when possible. Disclose provider processing, retention, training use, region, and deletion accurately. Obtain meaningful consent before using highly sensitive data or a secondary purpose.

For generated or user-to-user content, add reporting, blocking, moderation, and appeal appropriate to the risk and store policy.

## 5. Handle personalization without lock-in

Cumulative personalization should make the product better, not make departure painful.

Provide:

- explanation of what the product learns and the benefit;
- opt-in where data or inference is sensitive;
- visible, editable preferences;
- feedback and correction history;
- a neutral cold-start/manual mode;
- raw-data export plus a useful representation of learned preferences;
- reset and deletion;
- portability where feasible;
- graceful behavior when personalization is absent or wrong.

Do not claim an output is deeply personalized when it is generic. Do not collect substantial data or effort before revealing a hidden price. Do not label inferred personality, health, ability, or identity as fact.

Measure improvement between new and established users through task quality and saved effort, not switching cost.

## 6. Evaluate the whole system

Create a versioned evaluation set from representative tasks, edge cases, languages, accessibility needs, adversarial input, and production failures. Keep sensitive production data out unless governance explicitly permits it.

Evaluate:

- task correctness and completeness;
- groundedness and source quality;
- consequential false positive and false negative rates;
- instruction following and scope adherence;
- unsafe, biased, or disallowed output;
- prompt injection and cross-tenant leakage;
- tool choice, arguments, and authorization;
- correction, override, undo, and recovery;
- latency, cancellation, energy, network, and cost;
- multilingual and assistive-technology experience;
- user comprehension, calibration, and trust.

Test the composed system, not only the base model. Retrieval, prompt, tool schema, policy, UI, caching, and retry changes can all alter behavior.

Set launch thresholds and rollback triggers before release. Never rely on “the model usually handles it.”

## 7. Design mobile runtime states

Handle:

- slow or unavailable network;
- backgrounding and process termination during generation;
- streaming interruption and resume;
- duplicate submission;
- stale context or model response;
- provider rate limit, refusal, timeout, and malformed output;
- partial tool completion;
- model/version change;
- offline or manual fallback;
- user cancellation at every safe boundary.

Persist enough task state to recover without persisting unnecessary sensitive content. Show partial results only when their incompleteness is obvious and safe.

Do not let streaming text move controls unpredictably, overwhelm screen readers, or trap focus. Announce meaningful updates at a usable cadence. Respect reduced motion and battery/network constraints.

## 8. Release and monitor safely

Use versioned prompts, model configuration, retrieval indexes, tool schemas, policies, and evaluation results.

Roll out with:

- internal adversarial testing;
- domain expert review for high-stakes use;
- a limited cohort;
- feature flags and server-side disablement;
- per-tool and per-action limits;
- outcome and harm dashboards;
- sampled privacy-safe traces;
- user reporting and support playbooks;
- rollback tested before expansion.

Monitor task success, material error, correction, override, cancel, undo, escalation, complaint, latency, cost, refusal, policy violation, and unsafe-action prevention. Re-evaluate on every material model, prompt, tool, data, or policy change.

Recheck current platform rules for generative AI, user-generated content, privacy disclosures, sensitive domains, and payments before release.
