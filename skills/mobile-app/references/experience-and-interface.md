# Experience and Interface

Use this reference for user journeys, information architecture, navigation, screens, forms, interaction, visual craft, motion, design systems, and accessibility.

## Contents

1. Map the journey
2. Choose mobile navigation
3. Specify every screen state
4. Design search and discovery
5. Design home, dashboard, and result surfaces
6. Create clear hierarchy and content
7. Design forms and input
8. Adapt to people, devices, and contexts
9. Use motion and emotion with purpose
10. Build a proportional design system
11. Review and hand off

## 1. Map the journey

Map behavior before drawing high-fidelity screens:

```text
Entry and user intent:
Preconditions:
First value:
Repeat value:
Decision points:
Waits and uncertainty:
Errors and recovery:
Completion and next choice:
Pause, resume, and exit:
```

Annotate where the user feels uncertain, overloaded, exposed, delayed, accomplished, or in control. Fix avoidable pain before adding delight.

Use the shortest ethical route to value. A step earns its place only when it:

- creates user value;
- collects information that visibly improves the result;
- protects safety, privacy, or security;
- enables an informed choice;
- satisfies a real platform or legal requirement.

Prototype the risky interactions and state transitions, not merely a click-through happy path. Test with realistic data, latency, keyboard, permissions, long text, errors, and return after interruption.

## 2. Choose mobile navigation

Start with platform conventions and diverge only for a measurable user need.

Define:

- top-level peer destinations;
- hierarchical child routes;
- contextual or modal tasks;
- global actions and search;
- deep-link targets;
- authentication redirects;
- back, close, cancel, and reselection behavior;
- state restoration after tab switches or process recreation.

Use a bottom tab/navigation bar when the app has a small set—usually three to five—of frequent peer destinations. For each item:

- use a concise text label and familiar icon;
- distinguish selection without color alone;
- meet the current platform hit-area minimum;
- preserve navigation and scroll state within each destination;
- expose badges only for current, actionable information;
- give the badge an accessible meaning;
- respect safe areas, text scaling, landscape, tablets, foldables, and cover displays.

Do not place an action in a peer-destination model and pretend it is a tab. Use the platform-appropriate action component. Do not animate a tab change like a hierarchical push.

Use a navigation stack for progressive drill-down. Match the platform's back model, including Android system/predictive back and iOS navigation gestures where applicable. A deep link must land in an understandable state and back out predictably.

Use a sheet, dialog, or popover for a contained contextual task, not as a cramped replacement for every route. Account for:

- content length and scrolling;
- keyboard and focus;
- screen-reader entry and dismissal;
- accidental swipe dismissal;
- unsaved work;
- destructive or high-consequence actions.

Make every gesture-only action available through a visible, semantic control. Teaching a hidden gesture once does not make it discoverable or accessible.

## 3. Specify every screen state

Give every screen a contract:

```text
Primary user job:
Entry points:
Required data:
Owned state:
Primary action:
Secondary actions:
Exit and back behavior:
Analytics:
Accessibility:
```

Design the relevant states explicitly:

The table below lists presentation obligations, not one mutually exclusive state enum. Content, connectivity, freshness, and mutation status can coexist. Distinguish saved locally, queued, synced, and authoritatively completed; never label a pending offline mutation as final success.

| State | Required behavior |
| --- | --- |
| Initial loading | Explain real activity; avoid a blank screen |
| Refreshing | Keep usable content when safe; show freshness |
| Populated | Make the main value and next action clear |
| First-use empty | Explain value and offer a concrete start |
| No results | Preserve the query/filters and suggest recovery |
| Partial | Identify what succeeded, failed, or remains |
| Stale | Show last updated time and refresh behavior |
| Offline | Preserve safe local value; explain queued or unavailable work |
| Permission denied | Explain impact neutrally and provide a usable path |
| Validation error | Place a specific correction beside the field |
| Recoverable error | Preserve work and offer an idempotent retry |
| Terminal error | Explain what cannot continue and where help exists |
| Success | Confirm the result and persisted effect |
| Destructive action | Prefer undo; otherwise confirm the specific consequence |
| Expired session | Preserve safe work and return after authentication |
| Interrupted return | Restore context without duplicating the action |

Use skeletons only when the approximate structure is stable. Do not show fictional content, imply progress that is not occurring, or shift controls as content streams in.

Distinguish “nothing exists yet” from “nothing matches.” Empty states should help; they should not blame, pressure, or become advertising space.

## 4. Design search and discovery

Decide whether the need is global search, search within a destination, filtering the current collection, browse/discovery, or systemwide indexing. Give search a primary position when finding is a primary job; do not add a permanent top-level destination for an occasional filter.

Define the search contract:

```text
Searchable corpus and current scope:
Query types and supported language:
Exact, prefix, fuzzy, or semantic behavior:
Freshness and offline behavior:
Suggestions, recents, and history retention:
Ranking, grouping, filters, and sort:
Result action and return path:
No-result and partial-result recovery:
Sensitive data and logging:
Success and quality measures:
```

Keep the query, scope, filters, sort, and scroll position when the user inspects a result and returns. Make scope visible. Let people clear the query and each active filter without reconstructing the search.

Before and during entry:

- state what can be searched with a specific prompt or label;
- offer recents only when useful and privacy-appropriate, with clear/delete controls;
- distinguish suggestions, corrections, categories, and actual results;
- let people refine a suggestion rather than forcing immediate submission;
- preserve typed text through rotation, interruption, and recoverable error;
- debounce or submit according to cost, latency, and user intent;
- cancel or ignore stale requests so an older response cannot replace a newer query;
- let people review the recognized voice query before a consequential search.

For results:

- prioritize relevance to the stated job, not paid placement or engagement alone;
- show enough context to distinguish similar items;
- label sponsored, personalized, inferred, or unavailable results;
- make match emphasis understandable without color alone;
- expose useful filters and sort with their active state and result effect;
- support large result sets without duplicates, skipped items, or scroll jumps;
- preserve the query on no results and offer specific ways to broaden, correct, or clear it;
- distinguish no match, incomplete index, offline cache, permission limit, and server failure.

Announce result counts and important updates at a usable cadence without reading every change. Keep keyboard and screen-reader focus stable as suggestions and results update.

Treat query and history data as potentially sensitive. Minimize analytics, avoid showing sensitive recents on shared surfaces, provide deletion, and never silently reuse private searches for advertising or public personalization.

Measure successful find-and-act, time to useful result, reformulation, zero/partial-result rate, wrong-result exits, filter recovery, and downstream outcome. Raw query volume or time in results is not proof of success.

## 5. Design home, dashboard, and result surfaces

Do not default the home screen to a dashboard because competitors do. Choose the return surface that best serves the next real job: resume, create, review an exception, inspect a result, or understand change.

For every summary, dashboard module, score, or report, specify:

```text
Question answered:
Raw value, definition, unit, and baseline:
Time window and freshness:
Source or provenance:
Observed fact:
Interpretation and uncertainty:
User-relevant consequence:
Available next action:
Drill-down or correction path:
Neutral fallback when interpretation is unsafe:
```

Help users answer, in order:

1. What happened or what is true now?
2. Why might it have happened?
3. What can I do next?

Separate observed data, calculated value, inference, explanation, and recommendation visually and semantically. Never present correlation or an AI-generated narrative as a known cause.

For a composite or proprietary score, explain its inputs, range, direction, comparison baseline, update cadence, uncertainty, and correction path. Keep the underlying values available. Do not use a mysterious score to manufacture authority or urgency.

Choose a chart only when it makes a comparison, distribution, relationship, or change easier to understand than a value, list, or table. Preserve units, time range, baseline, scale, and exact values. Provide an accessible summary and a route to the underlying data; do not rely on shape or color alone.

Design first-use, insufficient-data, partial, stale, offline, permission-limited, anomalous, and error states. Label missing or estimated data instead of filling the gap with fictional precision.

Use personality to clarify the emotional meaning of data only when it fits the domain. In medical, financial, safety, or other serious contexts, factual clarity, uncertainty, and actionability dominate character or celebration.

Measure comprehension, correct interpretation, appropriate next action, correction, and downstream outcome—not dashboard dwell time, screenshots, shares, or visual novelty.

## 6. Create clear hierarchy and content

Make the principal job and next action visually dominant. Reduce simultaneous choices, but do not hide information necessary for safety, trust, or comparison.

Use:

- semantic typography rather than arbitrary fixed sizes;
- meaningful grouping and proximity;
- restrained emphasis;
- whitespace as structure;
- consistent alignment and rhythm;
- familiar symbols plus labels where ambiguity exists;
- progressive disclosure for secondary detail;
- product imagery or examples that truthfully show the result.

Avoid deeply nested cards, boxes, and padding that shrink the usable canvas. A card should express a meaningful group or interactive object, not serve as the default container for every element.

Write concise, specific copy:

- name the action and its result;
- state price, time, risk, and limitation plainly;
- use active voice and familiar language;
- explain recovery, not merely that an error occurred;
- avoid jargon, hype, guilt, and false certainty;
- keep labels stable across screens and states.

For a consequential decision, specify adjacent to confirmation:

```text
Affected objects and verified identity:
Current state and freshness:
Exact proposed action:
Expected resulting state:
Fees, rates, pending items, and assumptions:
Conditions or uncertainty that could change the result:
Reversibility and recovery:
```

Use familiar names or imagery to support recognition, but keep authoritative identifiers available when mistakes matter. An avatar or logo is not identity proof.

Use smart defaults only when they are common, low-risk, reversible, and obvious. Never default optional consent, marketing, public sharing, destructive action, or an expensive plan.

## 7. Design forms and input

Ask only for information needed now. Reuse known data and defer optional enrichment.

Choose the control from the answer model and error cost:

- direct selection for a small, stable, mutually understandable set;
- search or autocomplete for a long or changing set;
- free text when the user's own wording is the data;
- structured date, time, numeric, and measurement controls when precision matters;
- a slider only for genuinely approximate values, with an editable or accessible exact alternative when needed.

Do not replace a reliable control with a gesture-only carousel, curved slider, emoji scale, or custom novelty input unless testing shows better task performance and it retains semantic, keyboard, screen-reader, and precise-input support.

For each field:

- use a persistent visible label;
- explain why sensitive or unusual information is needed;
- choose the correct keyboard, input mode, content type, and autofill hint;
- accept human-friendly input and normalize safely;
- preserve entry across validation, navigation, backgrounding, and retry;
- validate at a useful moment without interrupting every keystroke;
- state the error and correction in text;
- associate help and error semantics with the field;
- support paste, password managers, one-time-code autofill, and accessibility tools where relevant.

Prefer a single coherent form when it is easy to scan. Split it into steps when each chunk has a meaningful purpose, decision, or dependency—not to inflate completion metrics.

One field per screen is not inherently simpler. When comparing structures, keep the requested data and validation constant and measure qualified completion, elapsed time, correction, backtracking, abandonment, resume success, downstream data validity, and assistive-technology and keyboard cost.

For a multi-step flow, provide truthful progress, back/edit, save/resume, and a clear final consequence. Do not count work the user has not completed.

Keep the primary action visible when the keyboard appears, but do not cover inputs or rely on one fixed viewport. Test external keyboards and alternative input.

## 8. Adapt to people, devices, and contexts

Build accessibility into component and state contracts.

Support:

- roles, names, values, states, hints, and actions for assistive technology;
- logical reading, traversal, and focus order;
- focus restoration after navigation, modal dismissal, and errors;
- text scaling and reflow without clipping or lost actions;
- sufficient contrast and non-color cues;
- current platform target sizes with spacing that prevents mistaps;
- simple gestures plus visible alternatives;
- reduced motion and reduced transparency where applicable;
- captions, text alternatives, and visual equivalents for sound;
- non-audio equivalents for haptic-only meaning;
- keyboard, switch, and voice access;
- RTL layout, pluralization, and locale-aware names, dates, numbers, units, and currency.

Do not put essential content only in placeholders, tooltips, hover, animation, color, sound, or vibration.

Use live-region or platform announcements sparingly. Announce meaningful status changes without reading every streamed token or repeatedly stealing focus.

Test with real screen readers and platform accessibility tools, large text, increased contrast, reduced motion, color filters, and alternative input. Automated checks are a floor, not proof of task completion.

Design for:

- one-handed and distracted use;
- compact, medium, and expanded windows;
- safe areas, cutouts, keyboards, and system bars;
- portrait, landscape, split screen, and rotation where supported;
- low-end hardware, poor connectivity, and battery constraints;
- privacy on lock screens, screenshots, app switcher, and shared devices.

## 9. Use motion and emotion with purpose

Give every motion a job:

- confirm input;
- explain spatial or state continuity;
- reveal hierarchy;
- communicate real progress or system status;
- direct attention to a changed result;
- acknowledge a meaningful completion.

Make motion interruptible and state-driven. Keep controls stable, avoid blocking the result, and ensure the end state remains clear if animation is removed. Honor reduced-motion settings with a considered alternative.

Concentrate craft on high-leverage moments:

- first value;
- a consequential wait;
- permission or trust explanation;
- error and recovery;
- meaningful completion;
- payment confirmation;
- return after interruption.

Use anticipation, reveal, and afterglow only in proportion to an earned result. Provide skip/mute where appropriate. Never introduce fake delay, hide owned data, or mimic a loot-box reveal to make a routine action compulsive.

Name the intended emotion—confidence, calm, competence, encouragement, belonging, or celebration—and check that it fits the domain. A playful mascot in a financial loss, medical warning, privacy failure, or destructive action can trivialize the situation.

Use peak-end thinking to reinforce authentic value and clear closure. Do not use one charming peak to camouflage a confusing or harmful middle.

## 10. Build a proportional design system

Start with semantic primitives:

- color roles and contrast pairs;
- typography roles;
- spacing and layout grid;
- shape, border, and elevation;
- icon and illustration rules;
- motion and haptic roles;
- content tone;
- platform adaptations.

Define a behavioral grammar as well as visual tokens:

- primary-action placement and priority;
- back, close, cancel, done, and undo semantics;
- gesture and visible-control pairing;
- direct-manipulation and spatial transition rules;
- loading, interruption, cancellation, and restoration;
- selection, validation, destructive action, and completion feedback;
- motion, haptic, and audio roles with equivalent cues;
- stable sequences for common tasks.

Extract a component when a pattern recurs or consistency is safety-critical. Specify:

```text
Purpose:
Anatomy:
Variants:
Sizes:
States:
Content rules:
Interaction:
Accessibility semantics:
Platform differences:
Motion:
Analytics, if any:
```

Include default, pressed, focused, selected, disabled, loading, error, and large-text behavior where relevant.

Keep the system proportional to the product. Do not create a large library ahead of evidence, and do not duplicate the same concept under visually different components.

Treat design and code as two implementations of the same semantics. Keep token names, component states, content, platform exceptions, and screenshots/prototypes synchronized.

For a material navigation or interaction change, write a migration plan. Preserve familiar paths where practical, provide discoverable cues and a visible fallback, test assistive-technology behavior, stage the rollout, monitor task success and error, prepare support, and define rollback. Do not call a hidden gesture discoverable because users may eventually learn it.

## 11. Review and hand off

Review a flow in this order:

1. User outcome and missing requirements.
2. Information architecture and sequence.
3. State, failure, and recovery coverage.
4. Trust, privacy, price, and consequence clarity.
5. Accessibility and platform behavior.
6. Visual hierarchy and content.
7. Motion, delight, and final polish.

Do not begin with pixel comments when the flow itself is wrong.

Handoff enough to implement behavior, not just frames:

- annotated flow and entry paths;
- state table and sample data extremes;
- component/token references;
- interaction and motion behavior;
- keyboard, back, deep-link, and restoration rules;
- accessibility labels, focus, and announcements;
- localization and text expansion;
- analytics and acceptance scenarios;
- assets and licensing;
- open decisions and edge cases.

Verify the built result against the design on physical devices. Resolve discrepancies in the shared system rather than accumulating one-off overrides.
