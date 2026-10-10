---
id: formats.conditions
title: Conditions
summary: 'Conditions: preserved findings, source scope, and unresolved verification.'
topics: &id001
- conditions
- diagnostics
- dialogue
- poi
- quest-mail
- quests
- template-registration
covers:
- Accessor_Tags
- AvailableCheck
- BuffCheck
- BuildableRegion_CheckCompleted
- Calendar_NowIsFestival
- CheckAppState
- CheckBattleState
- CheckDataValue
- CheckDistanceBetweenEntity
- CheckFlag
- CheckHadSpeakWithNPCToday
- CheckHasFollowerCondition
- CheckHasOwner
- CheckHasVehicle
- CheckInRoom
- CheckItemPreferenceLevel
- CheckItemRequestSubmit
- CheckItemRequestSubmitInDialog
- CheckLearnedFormula
- CheckLearnedProcessFormula
- CheckLockRoomMaster
- CheckNPCAffectionStar
- CheckNPCArriveWeekReceiveGiftLimit
- CheckNPCCanReceiveGift
- CheckNPCHadUnlock
- CheckNPCIndentAllNPCAffection
- CheckPhotoSelect
- CheckPlayerCollectDLC
- CheckPlayerHadGetTitle
- CheckPlayerHasDLC
- CheckPlayerHasDLCOnly
- CheckPlayerTalentLevel
- CheckPrepareStationUnlocked
- CheckRoomHasMember
- CheckRoomMaster
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
  - 5
sections:
- anchor: conditions
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: 5-conditions
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: the-template-condition-vocabulary-enumerated
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
---

# Conditions

The [condition/operator and localization contracts](../systems/condition-operators-localization.md)
provide the current machine-readable registration catalogue, native state-store and timing findings,
and offline validation rules. The vocabulary below retains its original evidence scope.

Split from the original dialogue investigation. Section numbers are retained for evidence provenance; use the [move ledger](../_meta/MOVED.md) for old references.

## 5. Conditions

Gating is **data-driven**, not hardcoded.

```
KConditionData
  Data          : Dictionary<Type, JObject>    condition class → its params
  Objects       : List<KConditionData>         nested subtrees
  IsOr          : bool
  ReverseResult : bool
```

Comparers are typed: `KComparer_{Bool,Int,Float,String,StringSet}` with `ECompareOp_*`.
`KConditionData` and `KConditionObject` both carry a `JsonCvt : JsonConverter<>` — confirmed: the
on-disk form is compact, not field-for-field.

**On-disk shape (verified, §8):** `IsOr` / `Objects` / `Data` do not appear. Instead a boolean
combinator is the sole key of the object, holding a list of terms; each term is an object carrying
`ReverseResult` plus exactly one condition key, whose value is that condition's parameters.

```json
"Condition": {
  "AND": [
    { "ReverseResult": false,
      "Time_CheckDate": { "CheckWeekday": true, "WeekdayCompare": { "Op": "Equal", "RValue": 1 },
                          "CheckDay": false, "CheckMonth": false, "CheckYear": false } },
    { "ReverseResult": false,
      "Weather_Today": { "DestType": "ClearSky" } }
  ]
}
```

Comparer objects serialize as `{ "Op": ..., "RValue": n }`, or `{ "Op": "Between", "MinValue": a,
"MaxValue": b }`. The JSON condition keys are short names, not the `K*Condition` class names — do
not grep for `KWeatherCondition` in the data.

**Attachment points (verified):**

| Field | Granularity |
|---|---|
| `DialogData.Condition` | one lib entry — finest available |
| `DialogTemplate.AvailableCheck` | whole graph |
| `OptionData.Condition` / `.ForceShowCondition` | player choice |
| `KDialogPoolCheck_Valid {PoolName, Tag}` | external gate: "has this NPC anything to say" |

`SentenceData` has **no** condition field. Smallest gateable unit is `DialogData`.

**Dialogue-native conditions** (`KDialogCondition` nested classes): `CheckFlag` (Key + bool),
`CheckDataValue` (Key + int), `DailyTalkCount` (SourceTag + int; fed by
`KDialogOpt_RecordDailyTalkPerson`).

**Game-wide catalogue.** The interop source contains **328 direct `: KCondition` declarations**
(314 in GameWorld, 14 in UI), including nested and compiler-generated types. That is a count of
declared classes, **not** a registration catalogue: nothing in the local files says which of them are
JSON-registered or legal inside an `AvailableCheck`, and answering that needs a runtime registration
test. Notable:
- Affection — `KCheckNPCAffectionStar`, `KCheckPlayerNPCAffectionStar`, `KListenAffectionAddCondition`
- Weather — `KWeatherCondition {Template, CheckType, MatchType, TargetType}`,
  `KCheckStationLockedByWeatherCondition`
- Time/season — `KTimeCondition`, `KCheckStationLockedByTimeCondition`, `KCheckShopItemSeedInSeason`
- Also: battle state, driving, angling, room occupancy, mail, item-holding, tool rarity, distance

**What is actually used in shipped lib data (verified, 5,371 `DialogData` entries across all 1,124
libs):** **15** distinct condition keys, a small subset of the 328 declared. Counts below are from the
1,106-file `DialogLib.*` family; the 19 `MissionDialogLib` / `RelationDialogLib` entries add nothing
new. **These conditions gate lib entries only — 81% of dialogue text is inline in templates and has
no per-line condition at all (§8).**

| Key | Uses | Notes |
|---|---:|---|
| `Time_CheckDate` | 1704 | `CheckDay/Month/Weekday/Year` + a comparer each |
| `Tag` | 1541 | |
| `CheckNPCAffectionStar` | 796 | |
| `Time_WaitGameTime` | 416 | |
| `Weather_Today` | 359 | `{ "DestType": "ClearSky" }` — **one field**, not the 4-field `KWeatherCondition` shape |
| `Item_CheckTag` | 341 | |
| `NPCHalfStarCheck` | 304 | |
| `Time_CheckTime` | 292 | `CheckHour/Minute` + comparer |
| `Item_CheckTemplate` | 239 | |
| `Calendar_NowIsFestival` | 198 | |
| `Role_Gender` | 36 | |
| `Accessor_Tags` | 20 | |
| `EntityData_CheckString` | 3 | |
| `EntityData_CheckTimestamp` | 1 | |
| `Tool_CheckActive_Tag` | 1 | |

Time and affection dominate. Nothing in the lib data uses the `KDialogCondition` nested set
(`CheckFlag` / `CheckDataValue` / `DailyTalkCount`) — those are presumably template-side only.

**Scope:** that table is **lib conditions only** — all 15 keys, across all 5,371 `DialogData`
entries. Templates use a much larger vocabulary, enumerated below.

**`Time_CheckDate.Month` is a season index, not a calendar month** (inferred from ~6 samples, not
proven): spring lines carry `MonthEqual1`, every snow line carries `MonthEqual4`. So `1=spring,
2=summer, 3=autumn, 4=winter`. This matters — season gating and weather gating are separate
mechanisms, and a line can be correctly scoped by one while lacking the other.

```json
"Time_CheckDate": { "CheckMonth": true,  "MonthCompare":   {"Op":"Equal","RValue":4},
                    "CheckWeekday": true,"WeekdayCompare": {"Op":"Equal","RValue":6},
                    "CheckDay": false, "CheckYear": false }
```

`Weekday` appears to drive a rotation schedule (which line plays on which in-game day), not calendar
meaning.

### The template condition vocabulary (enumerated)

**There are seven condition attachment sites in the Tree corpus, not the three usually cited.**
Measured by walking every condition tree in all 6,041 files:

| Site | Uses | Distinct keys |
|---|---:|---:|
| `DialogList[].Condition` — lib entry | 6,251 | 15 |
| `Graph.Nodes[].OutPort.<port>.Condition` — the edge gate | **4,782** | **75** |
| `Graph.Nodes[].OutPort.<port>.ForceShowCondition` | 32 | 7 |
| `AvailableCheck` — template root | 23 | 9 |
| `Extensions.AvailableCheck` | 16 | 5 |
| `DTGraph.Nodes[].OutPort.<port>.Condition` — decision-tree graphs | 9 | 2 |
| `Graph.Nodes[].Data.Goals[].Condition` — mission goals | 2 | 2 |

The last three are easy to miss: `Extensions.AvailableCheck` is a **second, separate** availability
gate from the root-level one, `DTGraph` is a different graph type living in the same corpus, and two
mission `Goals` carry conditions inside dialogue files. The template side uses **77** keys in total;
the union with libs is **80**, of which 12 are shared, 3 lib-only and 65 template-only.

**Scope:** this is the `Config/Dialog*` corpus only. Other config families use conditions the
dialogue data never does — `Config/Indent/NPCIndent/` alone adds `Wiki_TypeGetNum` and
`CheckNPCIndentAllNPCAffection` (§10). Treat 80 as the dialogue vocabulary, not the game's.

**All 75 `OutPort` keys.** `lib` is the same key's count in lib entries, so a zero there marks a
template-only condition; `files` is how many files it appears in.

| Key | OutPort | lib | files |
|---|---:|---:|---:|
| `Indent_IsRequestSubmit` | 1952 | 0 | 1859 |
| `CheckNPCAffectionStar` | 395 | 796 | 232 |
| `NPCHalfStarCheck` | 303 | 304 | 38 |
| `Data_CheckString` | 218 | 0 | 82 |
| `Tag` | 203 | 1541 | 229 |
| `MissionData_CheckString` | 164 | 0 | 64 |
| `Inventory_CheckTagAddItems` | 141 | 0 | 71 |
| `Data_CheckFloat` | 123 | 0 | 47 |
| `EntityData_CheckTimestamp` | 110 | 1 | 74 |
| `EntityData_CheckFloat` | 95 | 0 | 62 |
| `CheckNPCHadUnlock` | 87 | 0 | 16 |
| `CheckItemRequestSubmit` | 81 | 0 | 43 |
| `EntityData_CheckString` | 75 | 3 | 54 |
| `Inventory_CheckAmount` | 75 | 0 | 30 |
| `Time_CheckDate` | 65 | 1704 | 84 |
| `CheckTakePhotoInclude` | 46 | 0 | 18 |
| `Role_Gender` | 45 | 36 | 21 |
| `CheckNPCCanReceiveGift` | 40 | 0 | 12 |
| `CurrencyCheck` | 37 | 0 | 14 |
| `CheckHasOwner` | 35 | 0 | 11 |
| `CheckHadSpeakWithNPCToday` | 34 | 0 | 12 |
| `MissionData_CheckFloat` | 32 | 0 | 6 |
| `Item_CheckAmount` | 26 | 0 | 15 |
| `PetHasState` | 21 | 0 | 7 |
| `Follower_IsFollower` | 20 | 0 | 10 |
| `Item_CheckTag` | 20 | 341 | 144 |
| `MissionCheckCompleted` | 20 | 0 | 9 |
| `Time_CheckTime` | 20 | 292 | 68 |
| `CheckNPCArriveWeekReceiveGiftLimit` | 19 | 0 | 10 |
| `Calendar_NowIsFestival` | 19 | 198 | 37 |
| `CheckItemPreferenceLevel` | 18 | 0 | 10 |
| `Accessor_Tags` | 16 | 20 | 5 |
| `CheckInRoom` | 15 | 0 | 13 |
| `CheckRoomMaster` | 14 | 0 | 12 |
| `Inventory_CheckAddItems` | 13 | 0 | 4 |
| `Mission_HasImmediatelyDialog` | 12 | 0 | 11 |
| `XiaoLiuRenCheck` | 12 | 0 | 2 |
| `CheckPhotoSelect` | 11 | 0 | 9 |
| `Pet_AdoptingCount` | 11 | 0 | 10 |
| `Inventory_CheckTagAmount` | 10 | 0 | 5 |
| `Weather_Today` | 10 | 359 | 93 |
| `Follower_Count` | 8 | 0 | 5 |
| `CheckPlayerHasDLC` | 8 | 0 | 1 |
| `CheckPlayerHasDLCOnly` | 8 | 0 | 1 |
| `CheckAppState` | 8 | 0 | 5 |
| `CheckPlayerTalentLevel` | 8 | 0 | 8 |
| `CheckPlayerHadGetTitle` | 6 | 0 | 12 |
| `CheckLearnedFormula` | 6 | 0 | 4 |
| `Food_RecipeHadLearned` | 6 | 0 | 3 |
| `CheckLearnedProcessFormula` | 6 | 0 | 3 |
| `BuffCheck` | 5 | 0 | 2 |
| `DivinedCheck` | 4 | 0 | 1 |
| `CheckDistanceBetweenEntity` | 4 | 0 | 2 |
| `MissionCheckInvolved` | 4 | 0 | 1 |
| `CheckStaffCanOpenStoreView` | 4 | 0 | 1 |
| `LocationCheck` | 4 | 0 | 1 |
| `DialogPool_Valid` | 3 | 0 | 2 |
| `NetCheckIsHost` | 2 | 0 | 2 |
| `NPCPrologueCondition` | 2 | 0 | 1 |
| `Inventory_CheckTagCategoryAmount` | 2 | 0 | 2 |
| `CheckHasVehicle` | 2 | 0 | 1 |
| `ShootingGameSuccessChecker` | 2 | 0 | 2 |
| `Crop_CropTypeCount` | 2 | 0 | 2 |
| `Farm_CurrentPlantCropCount` | 2 | 0 | 2 |
| `CheckItemRequestSubmitInDialog` | 2 | 0 | 1 |
| `CheckPrepareStationUnlocked` | 2 | 0 | 1 |
| `Pet_ShopCanAdoptCount` | 1 | 0 | 1 |
| `EntityCountByTag` | 1 | 0 | 1 |
| `RandomNumberCheck` | 1 | 0 | 1 |
| `CheckHasFollowerCondition` | 1 | 0 | 1 |
| `CheckLockRoomMaster` | 1 | 0 | 1 |
| `CheckRoomHasMember` | 1 | 0 | 1 |
| `BuildableRegion_CheckCompleted` | 1 | 0 | 1 |
| `LivestockGeneCountChecker` | 1 | 0 | 1 |
| `CheckSuccessAnglingHarvest` | 1 | 0 | 1 |

The other two template sites use small subsets:

```
ForceShowCondition (7)  Follower_IsFollower 10, CheckPlayerCollectDLC 8, CheckNPCAffectionStar 7,
                        DivinedCheck 2, Time_CheckTime 2, Weather_Today 2, Tag 1
AvailableCheck (9)      CheckPlayerHadGetTitle 7, Inventory_CheckAmount 5, CheckBattleState 2,
                        EntityData_CheckTimestamp 2, MissionData_CheckString 2, Tag 2,
                        EntityData_CheckString 1, Data_CheckString 1, Data_CheckFloat 1
```

`CheckPlayerCollectDLC` and `CheckBattleState` appear **only** at those two sites and nowhere in the
75 — which is why the template-side union is 77, not 75.

**Parameter shapes for the keys you are most likely to write.** Every `Comparer` is the
`{Op, RValue}` / `{Op:"Between", MinValue, MaxValue}` / `{Entries:[{Op, RValue}]}` object above:

```jsonc
"Indent_IsRequestSubmit"     { "Key": "PrepareBigFireworks.Item", "DefaultVal": false }
"Data_CheckString"           { "Key": "TakeBigWatermelonSuccess", "Comparer": {"Op":"Empty"} }
"Data_CheckFloat"            { "Key": "rdmnum", "Comparer": {"Op":"Equal","RValue":0} }
"EntityData_CheckTimestamp"  { "Key":"PetState", "Tag":"TARGET", "Type":5, "TrueOnEmpty":true,
                               "Comparer": {"Op":"GreatOrEqualThan","RValue":1} }
"Inventory_CheckAmount"      { "Template":"Item.Crop.Grass", "Tag":"SOURCE", "OnlyCheckBag":false,
                               "Comparer": {"Op":"GreatThan","RValue":0} }
"Inventory_CheckTagAddItems" { "AddEntityTag":"SOURCE", "AddItemTag":"OBJECT" }
"CurrencyCheck"              { "CurrencyTemplate":"Currency.Default", "SourceTag":"SOURCE",
                               "Comparer": {"Op":"GreatOrEqualThan","RValue":70} }
"MissionCheckCompleted"      { "MissionID":"Mission.POI.ChuXia.Register", "WillCheckCount":false }
"CheckItemRequestSubmit"     { "RequestItemInfoContextTag":"PrepareDishes", "Submit":true }
"CheckNPCHadUnlock"          { "Tag":"TARGET", "GlobalTag":"" }
"Role_Gender"                { "Tag":"@MainRole", "DestGender":"Female", "DefaultVal":false }
"Tag"                        { "Tag":"SOURCE",
                               "Comparer": {"Entries":[{"Op":"Exclude","RValue":"FirstRandomTalk"}]} }
"BuffCheck"                  { "EntityTag":"@MainRole", "BuffIDs":["Buff.Friendly_Pet"],
                               "AllContain":false }
"RandomNumberCheck"          { "Comparer": {"Op":"LessOrEqualThan","RValue":0.1} }
"LocationCheck"              { "TargetLocation":"Location.Island_StarSand.Dock02" }
"CheckPlayerHasDLC"          { "DLCFile":"DLC", "DLCNameKey":"GanenDlc01" }
```

**`RandomNumberCheck` is the only nondeterministic gate in the vocabulary, and it is used once.**
Dialogue branching is otherwise entirely determined by world state — worth knowing before assuming
a line you cannot reproduce in-game is random.

**`Indent_IsRequestSubmit` alone is 41% of all template gating.** Commission/delivery requests (§10)
are the single largest branching mechanism in the game's dialogue, ahead of affection.

**Three findings that matter for §9:**

1. **`Weather_Today` is the only weather key in the entire vocabulary** — 10 uses in templates, 359 in
   libs. Nothing else in the 80 relates to weather. This **retires the caveat** in §9 that a grep for
   the literal string `Weather` might have missed gating under an unknown key. It could not have.
2. **Weather gating does exist in graphs**, not just libs, so the two stores share the mechanism.
3. **Controller-level `Condition` fields are never used** (0 across all templates). Gating happens at
   `OutPort` and at the lib entry, nowhere else.

Keys used in libs but never anywhere template-side: exactly three — `Item_CheckTemplate`,
`Time_WaitGameTime`, `Tool_CheckActive_Tag`. Keys used template-side but never in libs: **65** —
everything inventory-, mission-, room-, pet-, photo-, recipe-, DLC- and multiplayer-related. Only
**12** keys are shared by both stores, so the two gating surfaces are largely disjoint vocabularies,
not one vocabulary used in two places.

**`AvailableCheck` is sparse, not dead: 19 of 4,806 templates have a populated value** — 2 in the
836-file `Dialog.*` family and **17 in `MissionDialog.*`**. The "834/836 empty" figure holds for
`Dialog.*` alone and does not generalise to the corpus.


