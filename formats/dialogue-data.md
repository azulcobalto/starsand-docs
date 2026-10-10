---
id: formats.dialogue-data
title: Dialogue data
summary: 'Dialogue data: preserved findings, source scope, and unresolved verification.'
topics:
- animation
- asset-resolution
- conditions
- cut-content
- diagnostics
- dialogue
- equipment-slots
- facial-animation
- localization
- performance
- poi
- quests
- rigs
- template-registration
covers:
- AvoidTyphoon
- AvoidTyphoon_Child
- CombatDialog.BuffEffect_InBubblePrison
- Condition
- DTGraph
- Desc
- Dialog
- DialogData
- DialogData.Condition
- DialogLib
- DialogLib.FishingFail_AFei
- DialogLib.IntroduceAction.EatTogether_Ding
- DialogLib.SayHello.Gifted_DialogLib.json
- DialogList
- DialogPool_AddLib
- Dialog_Mechanics.Investigate_Puzzle_Door
- DrinkCoffee_Typhoon
- Eat_Typhoon
- Graph
- KDialogLibSet.ResignSentenceSpeaker
- Localization.FixDialogKey_20260819
- Localization.bytes
- Localization.rawdump
- LocalizationRef
- Message.DialogShow
- MissionDialog
- MissionDialog.FML.Plant_M1.2
- MissionDialog.Relation.BaiLiLing_Lv5_Main_Invite_Dialog09
- MsgDialog.Branch.AnglingRod_FishingPoint
- NPCSensingPlayerLongTime_Normal
- Name
- Object.UseForDialog_Mission_AVGMan
- OutPort
- PlotInteract.Wait_ChuXia_Dialogue
- Prefix
state: current
evidence:
- metadata
- extracted-data
builds:
- unknown
reviewed: null
sources:
- file: docs/_archive/originals/dialoguesystem.md
  sections:
  - 7
  - 8
---

# Dialogue data

Split from the original dialogue investigation. Section numbers are retained for evidence provenance; use the [move ledger](../_meta/MOVED.md) for old references.

## 7. Lib data schema — where lines live (one of two stores; see §8)

```
KDialogLibSet : JsonTemplateSet<KDialogLibSet, DialogLib> → JsonAssetTemplateSet
   loads Unity TextAssets from ConfigDir; fields textAssets, m_RealPath, IsUseBinary

DialogLib
  ID              : string
  TagDescription  : Dictionary<string,string>     tag → who that tag is
  DialogList      : List<DialogData>
  └─ DialogData                                   ← smallest gateable unit
     Note       : string                          authoring comment
     Condition  : KConditionData
     Sentences  : List<SentenceData>
     └─ SentenceData                              ← the line
        Tag            : string   speaker slot, keys into TagDescription
        Prefix         : string
        Text           : string
        NarrativeAudio : string
```

`KDialogTemplateSet : JsonTemplateSet<_, DialogTemplate>` is the parallel set for graphs:
`DialogTemplate { Name, Title, Graph, AvailableCheck, IsSoliloquy, TagDescription }`.

`KDialogLibSet.ResignSentenceSpeaker` reassigns speakers ⇒ `Tag` is a **role slot**, not a fixed NPC.

**On-disk key sets (verified over all 6,041 JSON files — 1,124 libs, 4,806 templates, 111 other):**

```
lib          ID, Desc, DialogList, TagDescription (1122)   (+ MaxCDSeconds, Condition on 2 files)
DialogData   Sentences (5371), Condition (5361), Note (4769)
SentenceData Tag (6317), Text (6317), Prefix (6064), NarrativeAudio (4822)
template     Name, Title, Description, Graph, AvailableCheck, IsSoliloquy, TagDescription (4768)
             + Icon (6) and a 17-field mission tail on the one Mission-schema outlier
```

Serialized libs carry a `Desc` field that the stub does not show. `TagDescription` serializes as a
**list of `{Tag, Desc}` objects**, not the stub's `Dictionary<string,string>` — e.g.
`[{"Tag": "TARGET", "Desc": "阿兹拉"}]`.

**`Prefix` is the game's primary expression channel, not a minor field.** It carries inline
directives such as `<ani:@F1_FistYes/>` — **6,370 non-empty `Prefix` values across 218 distinct
directives** (6,772 string-valued `Prefix` fields in total, of which 402 are empty; every non-empty
one matches a single `<ani:.../>` directive), against **4,442 uses of the `DialogAnimation_*`
operators combined**: 4,243 Play, 199 SetBool and 0 SetTrigger. The `@F1_` prefix is a canonical authoring label
that is remapped per body rig at play time, so a directive naming `F1` still drives the correct
animation on any character. See `animation.md` §A5 and §A2.

## 8. `Assets/Tree/` — extracted config

6,043 files, flat, extracted from bundles and given a `.json` suffix (they had none). **6,041 are
JSON and all 6,041 parse** as plain JSON — no MessagePack decode needed; the two exceptions are
`Localization.bytes` and `Localization.rawdump`. `Assets/Tree.txt` maps each family back to its
source container.

**Family classification (verified by structure, not by name):**

| Prefix | Count | Kind | Source container |
|---|---:|---|---|
| `MissionDialog.*` | 3,630 | 3,628 **template**, 2 indent-detail | `/Config/Dialog/` |
| `DialogLib.*` | 1,106 | 1,105 **lib**, 1 template | `/Config/DialogLib/` |
| `Dialog.*` | 836 | **template** | `/Config/Dialog/` |
| `RelationDialog.*` | 316 | **template** | `/Config/Dialog/` |
| `IndentDetails.*` / `Indent.*` | 48 | `{ID, NameText, DescriptionText, HeadIconPath}` | `/Config/IndentDetails/` |
| `Localization.*` | 24 | key→text table | `/Config/Localization/` |
| `Mission.*` | 18 | **template** | `/Config/Mission/` |
| `MissionDialogLib.*` | 17 | **lib** | `/Config/DialogLib/` |
| `Branch.*` | 15 | interact phase graphs | `/Config/Interact/Interact/` |
| `Interact.*` | 12 | interact phase graphs | `/Config/Interact/Interact/` |
| `POIDialog.*` | 4 | **template** | `/Config/Dialog/` |
| `RelationDialogLib.*` | 2 | **lib** | `/Config/DialogLib/` |
| `DT.*` | 2 | decision trees (`DTGraph`) | `/Config/DecisionTree/` |
| `DialogFeedback.*` | 2 | key→text table | `/Config/DialogFeedback/` |
| singletons | 9 | `CombatDialog.BuffEffect_InBubblePrison`, `Dialog_Mechanics.Investigate_Puzzle_Door`, `Message.DialogShow`, `MsgDialog.Branch.AnglingRod_FishingPoint`, `Object.UseForDialog_Mission_AVGMan`, `PlotInteract.Wait_ChuXia_Dialogue`, `React.Photo_Dialog`, `UIDialog`, `UIPerformanceDialog` | various |

**Totals: 1,124 libs, 4,806 templates.** Discriminator: a lib has `DialogList` and no `Graph`; a
template has `Graph`. The prefix is a reliable proxy with **one exception**:
`DialogLib.SayHello.Gifted_DialogLib.json` is a template. Tooling must special-case it.

### Two separate text stores — and libs are the smaller one

| Store | Lines | Gating |
|---|---:|---|
| Lib sentences (`DialogList[].Sentences[]`) | 6,317 objects / **6,315 non-empty** | per-entry `DialogData.Condition` + pool/provider selection |
| Inline template sentences (`Graph.Nodes[].Data.Components.Sentence.Data[]`) | 26,440 objects / **26,428 non-empty** | **graph edges / node `OutPort` conditions only** |
| Total | 32,757 objects / **32,743 non-empty** | |

"Lines" below always means a **non-empty `Text` value**; 14 sentence objects ship with empty text and
have no localization key.

Inline sentences carry **no `Condition` field of their own** — the `Sentence` component is just
`{ "Data": [ {Tag, Text, Prefix, NarrativeAudio} ] }`. They are gated by where the node sits in the
graph. By family: `MissionDialog` 20,440, `Dialog` 4,355, `RelationDialog` 1,590, rest 55. This is
81% of all dialogue text, and §5's condition analysis does not apply to it.

### Reference integrity

| Check | Result |
|---|---|
| Libs referenced by any template | 134 / 1,124 via the two template *components* (199 uses); 212 / 1,124 if any `DialogLib.*` string anywhere in a template counts (306 uses). The rest bind via entity pools, §6 |
| Templates referenced by another template (`SubDialog.SubDialogList[].TemplateID`) | 66 / 4,806 |
| Dangling template refs | 0 |
| Dangling lib refs via `DialogPool_AddLib` | **5** — `DialogLib.SendGift_Lv2.{DingJianJun, HaMeng, NanGongMiYin}`, `DialogLib.FishingFail_AFei`, `DialogLib.IntroduceAction.EatTogether_Ding` |
| Further unresolved `DialogLib.*` IDs in scalar `DialogLib` fields (§6 path 5) | **9** — `AvoidTyphoon`, `AvoidTyphoon_Child`, `DrinkCoffee_Typhoon`, `Eat_Typhoon`, `NPCSensingPlayerLongTime_Normal`, `SayHiToMainrole2_ActorA`, `SeaFishing_Ceremony`, `StandPhoneSurf_Typhoon`, `TouristWander` |

Two further values in fields named `DialogLib` are `Mission.*` IDs. Those are more likely polymorphic
or misnamed fields than missing libraries, and are **not** counted as dangling.

The dangling refs are either a genuine content bug or an incomplete extraction; unresolved. Note the
Typhoon cluster among the scalar-field misses — it lines up with the Typhoon-is-a-scripted-event
finding elsewhere, so those four may never have shipped as libs at all.

### Text is literal, and the literal *is* the localization key

Zero `$$key$$`-form `Text` fields exist anywhere in the dialogue data — all literal zh-Hans.
Localization is a **side table keyed by JSON path**:

```
Assets/LocalizationRef/{zh-cn,en}.json    115,636 entries each, 1:1 parallel
  Translations[] { Key, Version, Value }

lib      $$<stem>.DialogList[<i>].Sentences[<j>].Text$$
         e.g. $$DialogLib.Chat.Ali.DialogList[17].Sentences[0].Text$$
template $$<stem>.Graph.N[<nodeID>].Data.Components.Sentence.Data[<j>].Text$$
         e.g. $$MissionDialog.BegForFood_Cat_FishPoint.Graph.N[3].Data.Components.Sentence.Data[0].Text$$
```

**32,739 of 32,743 sentence texts (99.99%) appear somewhere in the zh-cn `Value` set**, across every
family — lib and template alike. The en `Value` at the same key is its translation. The 4 misses are
dev leftovers prefixed `∫` (`∫主线对话测试` = "mainline dialogue test") — unlocalized, and evidence
that the pipeline generates keys without validating coverage.

**What that test does and does not show.** It is set membership on the *value*, so a duplicated line
("谢谢！") can match some other entry's value rather than its own. Read the 99.99% as "essentially
all shipped dialogue text is present in the localization table," not as "every key path resolves."

Direct key-path resolution, building each sentence's key from the convention above, gives:

| Result | Count |
|---|---:|
| Non-empty sentence paths with a key in **both** zh-cn and en | 32,739 |
| Source literal **exactly equals** the zh-cn value at its own key | 32,731 |
| Key exists but zh-cn value differs from the source literal | 8 |
| No key at all (the `∫` dev strings) | 4 |
| Empty text, no key | 14 |

The eight mismatches are all placeholder lines in
`MissionDialog.Relation.BaiLiLing_Lv5_Main_Invite_Dialog09` — values like `采访1` ("interview 1") and
`三人对话1` ("three-person dialogue 1"). So the key-path convention is confirmed across the whole
corpus, not just on samples.

**Build the key from the logical name, not the filename stem.** Where extraction collided and renamed
a file, the two differ: `MissionDialog.FML.Plant_M1.2 #28895.json` has logical name — and
localization prefix — `MissionDialog.FML.Plant_M1.2`. Use the template's `Name` field or the
library's `ID` field.

**Consequence — edit safety differs between the two stores:**

- **Graph node data is ID-keyed.** `N[<nodeID>]` uses the node's `ID` field. The October 2 native
  trace and current language-table audit confirm this across thousands of fields where IDs differ
  from array positions. Reordering nodes preserves their `Data` keys, but option text in `OutPort`
  retains an additional `Nodes[<arrayPosition>]` segment beneath that node-ID scope, so its keys
  can change. See the [localization contracts and validator](../systems/condition-operators-localization.md)
  for exact paths, current table provenance and remapping checks.
- **Libs are position-keyed, and therefore fragile.** `DialogList[<i>]` is an array index —
  `DialogData` has no ID field. Reordering, inserting into, or splitting a `DialogList` renumbers
  every key after the edit point and silently desyncs all non-zh translations. Lib edits must be
  append-only, or must rewrite `LocalizationRef` keys in lockstep.
- `Sentences[<j>]` / `Data[<j>]` is positional in both stores, so inserting a sentence mid-node is
  unsafe everywhere.

`Localization.FixDialogKey_20260819` is a hand-authored key-fix table dated 2026-08-19 — consistent
with the shipping team having hit this problem, though its actual cause has not been traced.

`Localization.*.json` in `Tree/` (24 files, from `/Config/Localization/`) is a **separate,
hand-authored namespace** — `$$BlackCurtain.*$$`, `$$FixDialogKey_*$$`, `$$LifeExperience$$` —
narration/curtain text and UI nouns referenced from dialogue, not sentence bodies.

