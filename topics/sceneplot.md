# Sceneplot

Topic `sceneplot`. Aliases: ScenePlot. Scan date: 2026-10-02.

[All topics](../TOPICS.md) · [Coverage](../_meta/COVERAGE.md)

## Maintained reference

- [Moonlit Forest companion baseline and resident composition](../systems/moonlit-companion-baseline.md) — Installed executable identity, freshly checked asset records, two resident fixtures, entity composition defaults and reusable evidence for the ordered companion investigations. (current; evidence: metadata, extracted-data, native-default, offline-experiment, runtime-reported, inference; builds: gameassembly-237196995381, content-snapshot-4b732b61e590).
- [Resident follow movement, path controllers and recovery](../systems/moonlit-follow-navigation.md) — ALi and LanYu follow through A* Seeker and steering motion; controller preemption preserves stacks, while cancellation does not establish stale-error recovery safety. (current; evidence: metadata, extracted-data, native-default, offline-experiment, inference; builds: gameassembly-237196995381, content-snapshot-4b732b61e590).
- [Moonlit companion follower ownership and state transitions](../systems/moonlit-follower-ownership.md) — Existing follower target identity, scoped membership, native activation and dismissal, distance timers, proposal arbitration and cleanup boundaries. (current; evidence: metadata, extracted-data, native-default, inference; builds: gameassembly-237196995381, content-snapshot-4b732b61e590).
- [Moonlit follower reactions and forest event contracts](../systems/moonlit-follower-reactions.md) — Native action mirroring, idle and emoji dispatch, target resolution, cleanup, and bounded forest context sources for later bubbles and actions. (current; evidence: metadata, extracted-data, native-default, offline-experiment, inference; builds: gameassembly-237196995381, content-snapshot-4b732b61e590).
- [ScenePlot staging](../systems/sceneplot.md) — Historical ScenePlot test entry point, linked to current native schedule, named mark binding, camera and cleanup contracts. (current; evidence: runtime-reported; builds: unknown).
- [NPC schedules, actor ownership and ScenePlot contracts](../systems/sceneplot-and-schedules.md) — Native schedule selection and POI suspension, named position binding, scene cameras, interaction cancellation and completion/abort cleanup, with current prefab evidence and offline verification. (current; evidence: metadata, extracted-data, native-default, offline-experiment, runtime-reported, inference; builds: gameassembly-237196995381).

## Formats and modding contracts

- [Adding a cutscene — what the shipped data makes possible](../modding/cutscene-authoring.md) — Adding a cutscene — what the shipped data makes possible: preserved findings, source scope, and unresolved verification. (current; evidence: metadata, extracted-data; builds: unknown).
  - [Section: adding-a-cutscene--what-the-shipped-data-makes-possible](../modding/cutscene-authoring.md#adding-a-cutscene--what-the-shipped-data-makes-possible) — Read this section with the record build, evidence and audit limits.
  - [Section: m1-the-short-answer](../modding/cutscene-authoring.md#m1-the-short-answer) — Read this section with the record build, evidence and audit limits.
  - [Section: m2-the-shape-of-a-working-cutscene-mission](../modding/cutscene-authoring.md#m2-the-shape-of-a-working-cutscene-mission) — Read this section with the record build, evidence and audit limits.
  - [Section: m3-triggering-and-conditions](../modding/cutscene-authoring.md#m3-triggering-and-conditions) — Read this section with the record build, evidence and audit limits.
  - [Section: how-a-mission-starts](../modding/cutscene-authoring.md#how-a-mission-starts) — Read this section with the record build, evidence and audit limits.
  - [Section: condition-vocabulary](../modding/cutscene-authoring.md#condition-vocabulary) — Read this section with the record build, evidence and audit limits.
  - [Section: m4-authoring-the-cutscene-itself--the-blocker](../modding/cutscene-authoring.md#m4-authoring-the-cutscene-itself--the-blocker) — Read this section with the record build, evidence and audit limits.
  - [Section: m4a-20-built-cutscenes-ship-that-nothing-plays](../modding/cutscene-authoring.md#m4a-20-built-cutscenes-ship-that-nothing-plays) — Read this section with the record build, evidence and audit limits.
  - [Section: m5-dialogue-and-animation-during-the-scene](../modding/cutscene-authoring.md#m5-dialogue-and-animation-during-the-scene) — Read this section with the record build, evidence and audit limits.
  - [Section: m6-ending-the-scene](../modding/cutscene-authoring.md#m6-ending-the-scene) — Read this section with the record build, evidence and audit limits.
  - [Section: m7-registering-it-as-watched](../modding/cutscene-authoring.md#m7-registering-it-as-watched) — Read this section with the record build, evidence and audit limits.
  - [Section: m8-the-realistic-route--stage-it-without-timeline](../modding/cutscene-authoring.md#m8-the-realistic-route--stage-it-without-timeline) — Read this section with the record build, evidence and audit limits.
  - [Section: m8a-a-separate-bepinex-route-for-custom-animation-clips](../modding/cutscene-authoring.md#m8a-a-separate-bepinex-route-for-custom-animation-clips) — Read this section with the record build, evidence and audit limits.
  - [Section: m9-open-and-what-would-settle-it](../modding/cutscene-authoring.md#m9-open-and-what-would-settle-it) — Read this section with the record build, evidence and audit limits.

## Research and negative results

- [Ordered directives for Moonlit Forest companion static analysis](../research/moonlit-companion-investigations/README.md) — Bounded investigations with shared evidence contracts, explicit handoffs and safe parallel branches for Sol-class instances. (current; evidence: none; builds: not-applicable).
- [Moonlit Forest NPC companion — static foundation gaps](../research/moonlit-companion-static-gaps.md) — Documentation coverage, existing follower and invitation evidence, and a bounded static-analysis backlog for taking an existing NPC into Moonlit Forest. (current; evidence: metadata, extracted-data, runtime-reported, inference; builds: gameassembly-237196995381, content-snapshot-4b732b61e590).
- [Instance 01 — follower ownership and state transitions](../research/moonlit-companion-investigations/01-follower-ownership.md) — Trace existing follower activation, AI arbitration, waiting, dropout and release. (current; evidence: none; builds: not-applicable).
- [Instance 04 — follow movement and navigation controllers](../research/moonlit-companion-investigations/04-navigation-controllers.md) — Trace the NPC movement backend and controller-level failure handling independently of world transfer. (current; evidence: none; builds: not-applicable).
- [Instance 07 — environmental and follower reactions](../research/moonlit-companion-investigations/07-reactions.md) — Trace existing reaction activation and expose forest event/context contracts for dialogue and actions. (current; evidence: none; builds: not-applicable).
- [Instance 05 — existing-map museum site and NPC access](../research/museum-investigations/05-site-access.md) — Bind one research site to world, region, streaming and actual resident navigation data, including construction obstacles. (current; evidence: none; builds: not-applicable).
- [Instance 09 — NPC museum routines](../research/museum-investigations/09-routines.md) — Integrate one ordinary museum visit with calendar precedence, travel, exhibit interactions and interruption recovery. (current; evidence: none; builds: not-applicable).
- [Instance 10 — museum integration audit](../research/museum-investigations/10-integration-audit.md) — Audit all museum handoffs for compatible identities, ownership, lifecycle and requirement coverage without implementing a mod. (current; evidence: none; builds: not-applicable).
- [Sequential directives for museum static analysis](../research/museum-investigations/README.md) — Eleven bounded Sol-instance assignments with evidence reuse, explicit contract ownership and sequential handoffs for a museum using existing game systems. (current; evidence: none; builds: not-applicable).
- [Static-analysis foundations for future mods](../research/static-foundations.md) — Static-analysis foundations for future mods: preserved findings, source scope, and unresolved verification. (current; evidence: none; builds: unknown).

## Audit corrections

- [Delta report: new modding knowledge from the 2026-09-07 field notes](../audits/2026-09-08-modding-findings-delta-report.md) — Delta report: new modding knowledge from the 2026-09-07 field notes: preserved findings, source scope, and unresolved verification. (current; evidence: metadata, extracted-data, runtime-reported; builds: unknown).
  - [Section: delta-report-new-modding-knowledge-from-the-2026-09-07-field-notes](../audits/2026-09-08-modding-findings-delta-report.md#delta-report-new-modding-knowledge-from-the-2026-09-07-field-notes) — Read this section with the record build, evidence and audit limits.
  - [Section: 1-executive-summary](../audits/2026-09-08-modding-findings-delta-report.md#1-executive-summary) — Read this section with the record build, evidence and audit limits.
  - [Section: 2-evidence-and-status-rules-used-in-this-report](../audits/2026-09-08-modding-findings-delta-report.md#2-evidence-and-status-rules-used-in-this-report) — Read this section with the record build, evidence and audit limits.
  - [Section: 3-high-value-changes-to-the-baseline](../audits/2026-09-08-modding-findings-delta-report.md#3-high-value-changes-to-the-baseline) — Read this section with the record build, evidence and audit limits.
  - [Section: 31-runtime-json-registration-hypothesis-becomes-a-reported-working-path](../audits/2026-09-08-modding-findings-delta-report.md#31-runtime-json-registration-hypothesis-becomes-a-reported-working-path) — Read this section with the record build, evidence and audit limits.
  - [Section: 32-missions-load-from-plain-json](../audits/2026-09-08-modding-findings-delta-report.md#32-missions-load-from-plain-json) — Read this section with the record build, evidence and audit limits.
  - [Section: 33-starting-a-mission-on-the-player](../audits/2026-09-08-modding-findings-delta-report.md#33-starting-a-mission-on-the-player) — Read this section with the record build, evidence and audit limits.
  - [Section: 4-new-sceneplot--event-dialogue-staging-knowledge](../audits/2026-09-08-modding-findings-delta-report.md#4-new-sceneplot--event-dialogue-staging-knowledge) — Read this section with the record build, evidence and audit limits.
  - [Section: 41-dialogue-participation-and-physical-placement-are-separate](../audits/2026-09-08-modding-findings-delta-report.md#41-dialogue-participation-and-physical-placement-are-separate) — Read this section with the record build, evidence and audit limits.
  - [Section: 42-speaker-slot-binding-beyond-source-and-target](../audits/2026-09-08-modding-findings-delta-report.md#42-speaker-slot-binding-beyond-source-and-target) — Read this section with the record build, evidence and audit limits.
  - [Section: 43-actor-schedule-and-interaction-control](../audits/2026-09-08-modding-findings-delta-report.md#43-actor-schedule-and-interaction-control) — Read this section with the record build, evidence and audit limits.
  - [Section: 44-what-the-borrowed-plot-prefab-actually-places](../audits/2026-09-08-modding-findings-delta-report.md#44-what-the-borrowed-plot-prefab-actually-places) — Read this section with the record build, evidence and audit limits.
  - [Section: 45-placement-methods](../audits/2026-09-08-modding-findings-delta-report.md#45-placement-methods) — Read this section with the record build, evidence and audit limits.
  - [Section: 46-position-groups-and-cameras](../audits/2026-09-08-modding-findings-delta-report.md#46-position-groups-and-cameras) — Read this section with the record build, evidence and audit limits.
  - [Section: 47-facing-control](../audits/2026-09-08-modding-findings-delta-report.md#47-facing-control) — Read this section with the record build, evidence and audit limits.
  - [Section: 5-dialogue-and-condition-system-refinements](../audits/2026-09-08-modding-findings-delta-report.md#5-dialogue-and-condition-system-refinements) — Read this section with the record build, evidence and audit limits.
  - [Section: 51-missionphasedialogstate-is-not-an-event-launcher](../audits/2026-09-08-modding-findings-delta-report.md#51-missionphasedialogstate-is-not-an-event-launcher) — Read this section with the record build, evidence and audit limits.
  - [Section: 52-serialized-versus-live-controller-objects](../audits/2026-09-08-modding-findings-delta-report.md#52-serialized-versus-live-controller-objects) — Read this section with the record build, evidence and audit limits.
  - [Section: 53-event-objects-are-notifications-not-commands](../audits/2026-09-08-modding-findings-delta-report.md#53-event-objects-are-notifications-not-commands) — Read this section with the record build, evidence and audit limits.
  - [Section: 54-data-stores-must-be-paired-correctly](../audits/2026-09-08-modding-findings-delta-report.md#54-data-stores-must-be-paired-correctly) — Read this section with the record build, evidence and audit limits.
  - [Section: 55-time-controller-placement](../audits/2026-09-08-modding-findings-delta-report.md#55-time-controller-placement) — Read this section with the record build, evidence and audit limits.
  - [Section: 6-poi-system-from-structural-map-to-live-diagnostic-workflow](../audits/2026-09-08-modding-findings-delta-report.md#6-poi-system-from-structural-map-to-live-diagnostic-workflow) — Read this section with the record build, evidence and audit limits.
  - [Section: attachment-reported-verified-or-directly-observed](../audits/2026-09-08-modding-findings-delta-report.md#attachment-reported-verified-or-directly-observed) — Read this section with the record build, evidence and audit limits.
  - [Section: inferredpartial-operational-rules](../audits/2026-09-08-modding-findings-delta-report.md#inferredpartial-operational-rules) — Read this section with the record build, evidence and audit limits.
  - [Section: 7-world-lookup-and-transform-handling](../audits/2026-09-08-modding-findings-delta-report.md#7-world-lookup-and-transform-handling) — Read this section with the record build, evidence and audit limits.
  - [Section: 8-entirely-new-systems-and-practical-constraints](../audits/2026-09-08-modding-findings-delta-report.md#8-entirely-new-systems-and-practical-constraints) — Read this section with the record build, evidence and audit limits.
  - [Section: 81-rhythm-minigame](../audits/2026-09-08-modding-findings-delta-report.md#81-rhythm-minigame) — Read this section with the record build, evidence and audit limits.
  - [Section: 82-audio](../audits/2026-09-08-modding-findings-delta-report.md#82-audio) — Read this section with the record build, evidence and audit limits.
  - [Section: 83-performance-safety-of-injected-code](../audits/2026-09-08-modding-findings-delta-report.md#83-performance-safety-of-injected-code) — Read this section with the record build, evidence and audit limits.
  - [Section: 84-exact-shipped-typos](../audits/2026-09-08-modding-findings-delta-report.md#84-exact-shipped-typos) — Read this section with the record build, evidence and audit limits.
  - [Section: 9-rejected-approaches-durable-negative-knowledge](../audits/2026-09-08-modding-findings-delta-report.md#9-rejected-approaches-durable-negative-knowledge) — Read this section with the record build, evidence and audit limits.
  - [Section: 10-cut-content-and-mail-gating](../audits/2026-09-08-modding-findings-delta-report.md#10-cut-content-and-mail-gating) — Read this section with the record build, evidence and audit limits.
  - [Section: 11-impact-on-each-preexisting-document](../audits/2026-09-08-modding-findings-delta-report.md#11-impact-on-each-preexisting-document) — Read this section with the record build, evidence and audit limits.
  - [Section: dialoguesystemmd](../audits/2026-09-08-modding-findings-delta-report.md#dialoguesystemmd) — Read this section with the record build, evidence and audit limits.
  - [Section: questsystemmd](../audits/2026-09-08-modding-findings-delta-report.md#questsystemmd) — Read this section with the record build, evidence and audit limits.
  - [Section: animationmd](../audits/2026-09-08-modding-findings-delta-report.md#animationmd) — Read this section with the record build, evidence and audit limits.
  - [Section: performancesystemmd](../audits/2026-09-08-modding-findings-delta-report.md#performancesystemmd) — Read this section with the record build, evidence and audit limits.
  - [Section: 12-claims-that-remain-open-or-should-not-be-promoted](../audits/2026-09-08-modding-findings-delta-report.md#12-claims-that-remain-open-or-should-not-be-promoted) — Read this section with the record build, evidence and audit limits.
  - [Section: 13-bottom-line](../audits/2026-09-08-modding-findings-delta-report.md#13-bottom-line) — Read this section with the record build, evidence and audit limits.

## Historical and superseded sources

- [Foundations for future Starsand Island mods](../research/mod-foundation-gaps.md) — Foundations for future Starsand Island mods: preserved findings, source scope, and unresolved verification. (historical; evidence: native-default, extracted-data; builds: unknown).

## Asset and evidence collections

- [historical-prefab](../LOCATIONS.md#historical-prefab) — Older prefab evidence. (present; Existing repository/README or recorded investigation; contents and installed freshness not independently audited.).
