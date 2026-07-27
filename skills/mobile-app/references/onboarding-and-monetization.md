# Onboarding and Monetization

Use this reference for first run, sign-up, personalization, permissions, trials, paywalls, subscriptions, purchases, upgrades, downgrades, win-back, and cancellation.

## Contents

1. Decide whether onboarding is needed
2. Reach first value
3. Ask for setup and personalization
4. Request permissions
5. Introduce accounts and identity
6. Choose a monetization model
7. Design the offer and paywall
8. Design consumables and virtual currency
9. Support the subscription lifecycle
10. Experiment on long-term value

## 1. Decide whether onboarding is needed

Onboarding is a bridge to value, not a mandatory slide deck.

Use this decision:

- If the core action is familiar and safe, open on that action.
- If learning is needed, teach one action in context.
- If setup is required, collect only prerequisites to the next value event.
- If personalization materially changes the result, ask the minimum useful questions and show what changed.
- If consent, identity, or safety must precede use, explain why and make the requirement clear.
- If the product can demonstrate value before account creation, preserve the result and ask for an account when saving or continuity becomes useful.

Default to no prerequisite tour. Make optional help findable later.

Optimize time and effort to first value, not screen count. A long flow may be justified when it contains real product use or necessary setup; sixty passive marketing screens are not justified because another app has a sixty-screen flow containing a lesson.

## 2. Reach first value

Define:

```text
First value event:
Minimum prerequisites:
Earliest safe interactive proof:
What can happen before sign-up:
What must persist:
Time-to-value target:
Drop-off points:
```

Sell the outcome by demonstrating it. Prefer:

- sample or real content;
- a safe interactive try;
- a small completed task;
- a preview generated from necessary input;
- a prepopulated home surface that reflects the user's choice.

Do not blur, lock, or hold hostage a result the user already created solely to force sign-up. If only part can be free, provide genuine standalone value and state what the account or plan adds.

Place education at the moment of use with inline guidance, validation, examples, checklists, or contextual tips. Do not require users to memorize features before seeing the product.

Instrument eligibility, each material step, first-value completion, median time and interaction count to value, error, abandonment, resume, and later repeat value.

## 3. Ask for setup and personalization

For every question, answer:

- Does the response change the experience now?
- Can the app infer it safely later?
- Is it sensitive?
- Can it be optional?
- Can the user inspect and edit the effect?
- Is the benefit worth the effort and data?

Do not force one mutually exclusive goal when real needs co-occur. Allow multiple intents and ask for priority only when it changes the next useful result.

Maintain an answer-to-effect map:

```text
Answer collected:
Why it is needed now:
Immediate visible change:
Downstream reuse:
System owner:
Edit and deletion path:
```

Do not ask a question whose effect cannot be shown or explained. Reuse an answer across sign-up, payment, and post-purchase flows instead of making the user repeat setup because different teams own the screens.

Make a justified longer flow:

- explain why each unusual or sensitive input matters;
- use plain, non-diagnostic language;
- show truthful progress and an estimated effort only when reliable;
- allow back, skip where optional, save/resume, edit, and delete;
- preserve answers across interruption;
- preview the actual personalization earned;
- avoid exact health, financial, or performance outcomes without valid evidence;
- disclose an essential paid gate before demanding substantial effort.

Do not treat completion as proof the flow was good. Sunk cost can inflate conversion while trust, refunds, or retention deteriorate.

Never use generic output disguised as a scientific or deeply personalized result. Make labels editable, rejectable, inclusive, and temporary. Do not turn personality or health inferences into identity pressure.

## 4. Request permissions

Request a protected capability when the user invokes the feature that needs it, unless the app's core function obviously cannot start without it.

Before the system prompt, add a custom explanation only when it gives new, concrete context:

```text
[Feature] uses [capability/data] to [specific user benefit].
[What is and is not collected or shared, when material.]
```

Keep it neutral. Do not imitate the system dialog, disable the refusal path, exaggerate consequences, or repeatedly intercept after denial.

For each permission:

- minimize scope and duration;
- use platform selectors or limited access when possible;
- write a specific purpose string;
- request separately at the moment of benefit;
- handle denial, limited access, and later revocation;
- provide a useful degraded path;
- link to system settings only after the user chooses a blocked feature;
- update visible status when access changes.

Do not request contacts, notifications, tracking, location, camera, microphone, photos, health data, or Bluetooth “for a better experience.” Name the feature and benefit.

Measure downstream feature success, not permission acceptance alone. High acceptance caused by pressure is not success.

## 5. Introduce accounts and identity

Require an account only when identity, sync, ownership, security, payment, collaboration, or regulation genuinely needs it.

Reduce account friction with:

- guest or local-first use where safe;
- platform credential and passkey support where applicable;
- correct password-manager and one-time-code integration;
- preserved anonymous work after sign-in;
- clear account-recovery and device-change behavior;
- no duplicate-account surprises across sign-in methods.

Explain what is saved and synced. Never imply that an account is required when a usable non-account path exists.

Treat sign-in, sign-out, session expiry, account switching, deletion, and reauthentication for sensitive actions as designed flows. Recheck current store rules for identity providers and account deletion before implementation.

## 6. Choose a monetization model

Choose from product economics and value delivery:

| Model | Fit | Main risk |
| --- | --- | --- |
| Free | Growth, public good, indirect business value | Unsustainable quality or hidden data monetization |
| One-time purchase | Durable bounded capability | Funding ongoing service and updates |
| Freemium | Useful free value, network effects, low marginal cost | Crippling free tier or constant upsell |
| Metered/credits | Usage has variable cost | Confusing units and spend anxiety |
| Subscription | Sustained, recurring value and ongoing service | Paying after value stops |
| Hard gate/trial | Value is already understood or marginal cost is high | No chance to verify fit |
| Contextual premium | Free core with paid high-intent features | Surprise at the moment of need |

Do not begin with a hard paywall because an unverified benchmark claims it converts better. Test whether users understand the value, marginal cost, activation loss, and long-term economics.

An onboarding-gated offer is appropriate only when setup materially creates the paid result and the paid expectation is clear before substantial effort.

For AI or other variable-cost features, consider a real sample, bounded free allowance, preview, slower tier, bring-your-own entitlement where appropriate, or clear metering before denying all value.

Choose plan cadence from the natural value cycle, service cost, likely endpoint, product maturity, brand trust, acquisition context, geography, affordability, and user preference. Evaluate direct purchase and trial cohorts separately. Compare retained outcome, revenue, cancellation, refund, regret, and support through the relevant renewal window. Never default to weekly, monthly, or annual because an observational benchmark says it “wins.”

## 7. Design the offer and paywall

Treat the paywall as one point in a lifecycle:

- after first value;
- at explicit premium intent;
- at a meaningful limit with preserved work;
- in settings or plan management;
- at renewal, upgrade, downgrade, recovery, or win-back.

Match the message to the current context. Do not repeatedly interrupt unrelated tasks.

Identify a premium-only capability before the user enters it when the gate would otherwise be a surprise after meaningful work. Preserve the user's input and provide a useful preview or safe return path when the offer appears.

Before purchase, show:

- the outcome and exact included benefits;
- what remains available without payment, if anything;
- each plan and meaningful difference;
- the actual amount charged and billing period prominently;
- introductory or trial length;
- exact charge timing or date when knowable;
- automatic renewal;
- how and where to cancel;
- eligibility and limitations;
- restore-purchase and manage-subscription paths;
- terms and privacy.

If showing a weekly or monthly equivalent for an annual plan, give the annual amount actually charged equal or greater prominence. Localize price, term, tax treatment, dates, and legal text.

Use a clear close/dismiss control when the offer is optional. Keep plan selection, consent, and purchase action visually unambiguous. When native store billing is used or required, let its purchase sheet be the authoritative final transaction surface.

When readable and platform-appropriate, make the primary action name its immediate consequence—such as starting a trial, paying an amount and interval, or upgrading—instead of a generic “Continue.” Nearby terms and the authoritative transaction surface still remain required.

Reduce legitimate risk with a truthful trial timeline, reminder only if reliably delivered, clear cancellation, useful preview, or plan that fits the need. Do not reduce “risk” through fake discounts, spin wheels, resetting countdowns, manufactured crossed-out prices, hidden toggles, or “I’ll risk it” dismissal copy.

Real reviews, ratings, savings, and scarcity still need applicable context and evidence. Never fabricate social proof or use a reference price that was not genuinely available.

## 8. Design consumables and virtual currency

Do not use intermediate units to hide real cost or make comparison difficult.

Prefer direct local-currency pricing unless intermediate units provide a demonstrated user benefit or a necessary, understandable product economy. “More engagement” or easier price manipulation is not a user benefit.

Before buying units, show:

- the local-currency charge and number of units;
- a simple effective exchange rate;
- whether units expire, restore, transfer, or have regional/device limits;
- refund and correction behavior;
- whether the purchase repeats or is one-time.

Before spending units, show:

- the exact item, access, action, or outcome being purchased;
- the unit cost and local-currency equivalent where reasonably calculable;
- current and resulting balance;
- cumulative session or period spend where repeated use can obscure cost;
- expected remaining cost for a finite task, story, or sequence when knowable;
- a fresh confirmation when the price, exchange basis, or user-defined threshold changes.

Provide transaction history, receipts, correction/support, and user-controlled budgets, caps, and alerts where repeated spend is possible. Use simple ratios and denominations. Do not engineer awkward bundles, changing unit prices, leftover balances, or missing totals to defeat mental calculation or exploit sunk cost.

Treat advertising, waiting, and attention as real costs. Do not deliberately degrade a free experience with irritation so users pay for relief.

Never combine paid units with opaque chance, variable-ratio pressure, real-money gambling, or misleading scarcity. If chance affects material value, disclose odds close to purchase and meet current platform and legal rules; in high-risk contexts, do not use chance at all.

Recheck current storefront rules for billing, restoration, expiration, randomized items, regional alternatives, minors, and refunds before implementation and release.

## 9. Support the subscription lifecycle

A subscription must continue producing meaningful recurring value. Monitor whether it does.

Design:

- purchase pending, success, failure, cancellation, and retry;
- entitlement across launch, offline use, reinstall, and other owned devices where required;
- restore purchases;
- upgrade, downgrade, proration, grace, billing retry, pause, and expiration;
- backend receipt/transaction validation;
- family or account-sharing rules where relevant;
- clear plan and renewal status;
- manage and cancel links;
- data access after downgrade or expiration;
- refund and support paths.

Never revoke primary functionality an existing user already bought without a fair transition.

Make cancellation at least as clear as purchase. Do not use more steps, weaker visual hierarchy, repeated save offers, emotional pressure, or a hidden web route to create friction. A neutral retention offer may appear once when relevant; respect dismissal.

Use win-back only after a real lapse or cancellation, with accurate eligibility and terms. Do not train users that closing every paywall reveals a secret lower price.

Keep subscription state server-authoritative and resilient to delayed notifications, refunds, revocations, billing recovery, and account mismatch. Do not infer entitlement from a locally cached toggle alone.

When paid access must work offline, use a bounded, signed server-issued entitlement lease tied to the account and entitlement. Define expiry/grace, clock-skew behavior, last-verified display where material, and the response to refund, revocation, account switch, or prolonged offline use. Require online verification when consequence or abuse risk outweighs offline value.

## 10. Experiment on long-term value

Instrument the complete funnel:

```text
eligible
-> offer impression
-> plan selected
-> store sheet shown
-> transaction result
-> trial active
-> first paid period
-> later renewal
-> downgrade/cancel/refund
```

Evaluate:

- net revenue per eligible user or install;
- first and later renewal;
- retained value use;
- cohort LTV and service cost;
- trial-to-paid conversion;
- refunds, chargebacks, complaints, ratings, and support;
- involuntary churn and recovery;
- cancellation success and time;
- disclosure comprehension;
- product retention with and without payment.

Run tests through the relevant renewal window. Trial starts or button taps alone cannot establish a winner.

Test conceptually different honest offers before microcopy:

- freemium versus metered versus trial;
- placement after value versus at premium intent;
- outcome demonstration versus feature comparison;
- trial timeline versus no trial;
- plan packaging and duration;
- short single surface versus progressive disclosure;
- interactive product demonstration versus static explanation.

Do not ship a conversion lift when payer quality, renewal, outcome, accessibility, complaints, refund, or comprehension worsens.

Store, billing, pricing-link, and subscription rules change by platform, storefront, and region. Verify the current official policy immediately before implementation and release; never rely on a remembered example.
