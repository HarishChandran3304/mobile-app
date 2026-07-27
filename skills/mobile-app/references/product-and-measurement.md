# Product and Measurement

Use this reference to turn an app idea or feature request into an evidence-seeking product plan.

## Contents

1. Product spine
2. Evidence and discovery
3. Design acquisition and distribution
4. MVP slicing
5. Feature contract
6. Measurement tree
7. Experiment card
8. Prioritization and decisions

## 1. Product spine

Complete this before expanding the feature list:

```text
Audience:
Situation and trigger:
Struggle or unmet job:
Desired real-world outcome:
Current alternative:
Promise:
Mechanism:
Existing workflow and entry surface:
Acquisition promise:
Distribution surface:
Product interaction principle:
First value event:
Repeat value event:
Reason to return:
Business model:
User-outcome metric:
Business metric:
Trust/harm/accessibility countermetric:
Constraints:
Non-goals:
```

Distinguish the **value event** from an interface event. “Created an account” is not value; “received an accurate plan they can use” may be. “Opened the app seven days” is not retention; “completed the beneficial action in a later need cycle” may be.

Model a return loop without manufacturing need:

```text
real context or chosen cue
  -> smallest meaningful action
  -> immediate proof of value
  -> lasting progress or saved effort
  -> user-controlled return cue
```

Require the repeat event to remain useful if all points, streaks, badges, notifications, and animation are removed.

## 2. Evidence and discovery

Separate facts, signals, assumptions, and decisions.

| Level | Evidence | Use |
| --- | --- | --- |
| Strong | Observed behavior, support themes, usability sessions, product data, controlled tests | Make or validate product decisions |
| Medium | Interviews tied to real past behavior, comparable workflows, domain expert input | Form and prioritize hypotheses |
| Weak | Stated future intent, competitor popularity, unverified anecdote, analogy | Generate questions, not conclusions |

For important assumptions, record:

```text
Assumption:
Why it matters:
Current evidence:
Fastest disconfirming test:
Decision if true:
Decision if false:
Owner and review date:
```

Research the problem before preferences:

- Ask about the last real occurrence, not an imagined future.
- Observe current tools, workarounds, handoffs, delays, and failure recovery.
- Identify who experiences the problem, who chooses, who pays, and who bears risk.
- Look for nonconsumption and manual work, not only direct competitors.
- Recruit across ability, device quality, language, connectivity, and experience levels.
- Treat sensitive-domain claims as needing qualified domain review.

Study comparable products to extract a pattern, not a skin. For several relevant flows—normally at least three when meaningful evidence exists—record:

- source, capture date, app version, platform, and market;
- intended user, problem, and entry context;
- acquisition promise and prerequisites;
- sequence, information hierarchy, states, recovery, and exit;
- price, permissions, data use, and likely business incentive;
- what is directly observed versus inferred;
- likely tradeoff, transfer conditions, and what should not be copied.

Pattern frequency shows convention, not effectiveness. Designer saves, awards, rankings, funding, revenue, and popularity do not establish user benefit or causality. Include adjacent alternatives and current workarounds so research does not collapse into copying category leaders.

Challenge a category convention only through an audience need:

```text
Category convention:
User constraint the convention assumes:
Evidence it fits this audience:
Evidence it excludes or harms this audience:
First-principles alternative:
New accessibility, safety, and trust risks:
Smallest disconfirming prototype:
Competitive implication, labeled as hypothesis:
```

Retain operating-system behavior, accessibility semantics, and familiar safety controls unless direct evidence supports a compatible alternative. Question the category workflow, not basic usability for novelty.

## 3. Design acquisition and distribution

Treat discovery through first value as one promise chain:

```text
source, referral, integration, or search
  -> claim and audience
  -> store listing, landing page, or deep link
  -> first screen and prerequisites
  -> first value
  -> repeat beneficial outcome
```

Keep the advertised outcome, screenshots, preview, free/paid boundary, permissions, setup effort, and actual first-run behavior consistent. Use representative product states and data. Do not use simulated capabilities, bait-and-switch creative, or a polished listing that hides a materially different product.

Design each entry for its context:

- land a deep link on the promised object or task, with understandable back behavior;
- preserve referral or shared-artifact context without exposing private data;
- localize and accessibility-review store text, screenshots, captions, and preview media;
- show prerequisites or regional/device limitations before installation when material;
- provide a useful fallback when the destination moved, expired, or requires authentication.

Measure the whole chain by acquisition promise and source: qualified impression, listing visit, install or open, first value, repeat value, payment quality, refund, complaint, and deletion. A higher listing conversion is not a win when qualified activation, retained outcome, comprehension, or trust worsens.

Product-led distribution must first benefit the current user. A share artifact, collaboration invite, integration, widget, shortcut, notification action, or companion surface should complete or extend a real job; it must not merely force another open. Let recipients understand what was shared before sign-up. Never require contacts access, invitations, reviews, or public posting to unlock core value.

## 4. MVP slicing

Define MVP as the smallest trustworthy proof of an outcome, not the smallest number of screens.

Choose a thin slice that:

- serves one specific audience and situation;
- completes one valuable journey end to end;
- uses real or production-shaped data boundaries;
- handles the most likely failure and recovery;
- includes necessary accessibility, privacy, security, analytics, and support;
- can teach whether the promise is true.

Defer breadth, automation, customization, secondary roles, and edge integrations before deferring trust or recovery.

Use this slice sequence when appropriate:

1. Manual or concierge proof of the outcome.
2. Single-user end-to-end happy path with honest limitations.
3. Failure, recovery, accessibility, and instrumentation.
4. Repeat use and saved progress.
5. Monetization after value is demonstrable.
6. Scale, automation, and secondary journeys.

Do not build a design system, backend platform, or personalization engine beyond what the first complete slice exercises. Do establish semantic primitives and stable boundaries that prevent obvious rework.

## 5. Feature contract

Write this before implementing a material feature:

```text
Target outcome:
User and entry context:
Preconditions:
Main scenario:
Alternate and failure scenarios:
State inventory:
Rules and invariants:
Data read, written, retained, exported, and deleted:
Permissions and sensitive capabilities:
Accessibility behavior:
Analytics and prohibited data:
Acceptance evidence:
Rollout and rollback:
Non-goals:
```

Describe acceptance as observable scenarios:

```text
Given [state and context]
When [user or system action]
Then [visible result and persisted effect]
And [recovery, accessibility, analytics, or safety condition]
```

Cover first use, returning use, interrupted use, denial, duplication, latency, stale data, and destructive action when relevant.

## 6. Measurement tree

Use a balanced tree:

- **User outcome:** Did the person achieve the beneficial result?
- **Activation:** Did a qualified new user reach first value within a useful window?
- **Repeat value:** Did an activated user achieve value again in a later need cycle?
- **Quality:** Was the result correct, fast, accessible, and recoverable?
- **Business:** Did the product create sustainable revenue or strategic value?
- **Trust guardrails:** Did pressure, confusion, complaints, refunds, privacy concerns, or harmful use rise?

Define every metric with an event, actor, denominator, eligibility rule, time window, and exclusions.

If no baseline exists, label proposed targets as provisional learning thresholds. Replace them with evidence-informed targets after discovery or the first trustworthy cohort; never present an invented threshold as an industry benchmark.

Prefer:

- time to first value over time to sign-up;
- task success over taps;
- activated-cohort retention over all-install retention;
- meaningful outcomes per activated user over raw sessions;
- retained outcome quality over notification-driven returns;
- voluntary sharing over share-sheet opens;
- comprehension, refund, complaint, and cancellation success alongside conversion.

Segment results by acquisition source, platform, version, device class, new/returning status, accessibility setting where privacy-safe, and other product-relevant cohorts. Never hide a harmed subgroup inside an average.

Keep analytics data-minimal. Do not send message contents, health details, credentials, precise location, contacts, user-generated text, or model prompts by default. Document purpose, retention, access, and deletion for every sensitive event property.

## 7. Experiment card

Use this for any meaningful product, onboarding, paywall, notification, gamification, or AI change:

```text
User problem and desired outcome:
Current evidence:
Hypothesis:
Control:
Variant:
Target segment and exclusions:
Exposure unit:
Primary user-outcome metric:
Business metric:
Quality metric:
Harm/accessibility/privacy countermetrics:
Minimum runtime or decision rule:
Qualitative follow-up:
Removal criterion:
Rollback condition:
```

Test large, honest differences before decorative micro-variants. A new value proposition, information sequence, or risk explanation usually teaches more than a button color.

Do not ship a winner when:

- the primary metric moved only for an unqualified cohort;
- outcome quality, accessibility, or recovery declined;
- complaints, refunds, accidental purchases, pressure, or regret rose materially;
- the result depends on deceptive framing;
- novelty is likely and no durable follow-up exists;
- instrumentation cannot distinguish actual value from repeated exposure.

## 8. Prioritization and decisions

Score opportunities on:

- user outcome magnitude;
- evidence strength;
- reach among the intended audience;
- strategic or revenue value;
- trust and safety risk;
- learning value;
- implementation and operating cost;
- reversibility.

Do not let a numerical score make the decision. Record the tradeoff and why now.

Maintain a short decision log for choices that are expensive, risky, or hard to reverse. Revisit a decision when its assumption, platform policy, business model, or observed outcome changes.
