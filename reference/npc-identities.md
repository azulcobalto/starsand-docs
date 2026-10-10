---
id: reference.npc-identities
title: Npc identities
summary: 'Npc identities: preserved findings, source scope, and unresolved verification.'
topics: &id001
- animation
- asset-resolution
- diagnostics
- dialogue
- equipment-slots
- facial-animation
- npc-identity
- poi
- quests
- rigs
covers:
- AFei
- ALi
- AVGMen
- Adventure
- Adventure01
- Adventure01_Interim
- Adventure02
- Adventure05
- AreaPlace.CoralTown_MusicShop
- BaiLiLing
- BoatMan
- Calender
- Calender.CoralTown_ChuXia
- ChenShuHui
- ChenXing
- ChuXia
- CommunityCenter
- CompleteDescription
- Components.Calender
- Components.DisplayableTitle.Title
- Crop
- Description
- Dialog.SayHello.ChuXia
- DingJianJun
- DingXiaoKui
- DingXiaoLong
- DingXiaoMiao
- FangShiMiao
- FangWenTing
- FengXi
- Fight
- Fish
- Fishing
- GaiSiTe
- Graphs
state: current
evidence:
- metadata
- extracted-data
builds:
- unknown
- content-snapshot-4b732b61e590
reviewed: null
sources:
- file: docs/_archive/originals/dialoguesystem.md
  sections:
  - 14
sections:
- anchor: npc-identities
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: 14-codenames-vs-shipped-names--read-this-before-matching-npcs-by-filename
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: which-field-to-trust
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: renamed-characters
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: full-npc-roster-codename--identity
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: professions-talents-and-their-four-mission-families
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: the-level-up-chain-missionfml
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: identifying-mentors-from-data-alone
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: the-repeatable-commissions
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: names-were-recycled-not-just-changed
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: a-single-npcs-content-spans-both-names
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: supplied-identity-reference
  topics: *id001
  limit: Read this section with the record build, evidence and audit limits.
- anchor: kickstarter-npcs-current-installed-source-comparison-2026-10-04
  topics: *id001
  limit: Hash-verified installed JSON collections and English localization; compiled formatter equivalence and live behavior are unverified. Kickstarter origin is owner-supplied.
---

# Npc identities

Split from the original dialogue investigation. Section numbers are retained for evidence provenance; use the [move ledger](../_meta/MOVED.md) for old references.

## 14. Codenames vs shipped names — read this before matching NPCs by filename

**Config filenames are development codenames. Several were reassigned to different characters during
development and never renamed.** Identity must be resolved from file *contents*, never from a
filename.

### Which field to trust

| Field | Where | Reliability |
|---|---|---|
| `TagDescription[].Desc` | libs and templates | **Best available.** The speaker label, player-facing, and usually the strongest authored evidence of identity — but the files cannot guarantee it is *always* current. |
| `Components.DisplayableTitle.Title` | `Role.*` entity | Good, but it is the **map/interaction label** — sometimes an occupation (种子店老板 "seed shop owner", 餐厅店主 "restaurant owner", 医生 "doctor") rather than a personal name. |
| `Components.Calender` / pool `Graphs` | `Role.*` entity | Useful corroboration — often already updated to the new name while the filename is not. |
| `Description` | templates | **Do not trust.** Stale authoring notes; several `XiaHeAn` files are described as 小葵 dates, but their `TagDescription` is 顾禾. |
| filename | — | **Do not trust.** |

### Renamed characters

| Filename codename | Shipped identity | English |
|---|---|---|
| `Role.CoralTown_XiaHeAn` | 顾禾 | **GuHe / Graminova** — seed shop owner, farming-job mentor |
| `Role.CoralTown_ZiLu` | 初夏 | ChuXia / Solara |
| `Role.CoralTown_AVGMen` | 岚 | LanYu / Zephyria |
| `Role.CoralTown_FangWenTing` | 沈霓 | ShenNi / Neona |
| `Role.CoralTown_ShiLiHaiLang` | 百里零 | BaiLiLing / Zerine |
| `Role.CoralTown_NingFang` | 予画 | LinYuHua / Lunelle |
| `Role.CoralTown_DingXiaoMiao` | 丁小葵 | DingXiaoKui / Pastelle |
| `Role.CoralTown_LinMengMeng` | 洛桃桃 | LuoTaoTao |
| `Role.CoralTown_RenQiuYing` | 沈梅 | |
| `Role.CoralTown_XiaChengShi` | 顾松年 | |
| `Role.CoralTown_TianRuLv` | 初建国 | |
| `Role.CoralTown_XiaQiLing` | 夏琳 | |
| `Role.CoralTown_YeXingLan` | 叶星阑 | YeXingLan — title is 餐厅店主, name unchanged |

The remaining ~20 named NPCs (`FengXi`→枫汐, `JianXu`→简煦, `ChenXing`→晨星, `LuoHeGuang`→洛和光,
`YuTangTang`→雨棠棠, `ALi`→阿梨, `JinJiEr`→金吉尔, `YouFang`→游方, `NiYa`→妮雅, …) keep their
codename, transliterated.

### Full NPC roster: codename → identity

`Role.CoralTown_<codename>` on the left. Chinese identity comes from `TagDescription` and the config
bindings, and is verifiable from the files. **The English names and the relationship descriptions are
project-owner supplied and cannot be checked against the local game data** — claims such as
former-romance-candidate status, crossover origin, or canonical English identity need an external
source or the owner's confirmation, not a grep.

| Codename | 中文 (pinyin) | English | Role | Romanceable? |
|---|---|---|---|---|
| `AVGMen` | 岚 lán | **Zephyria** | **Adventuring** mentor — adventurer guild 冒险家公会 | Yes |
| `ShiLiHaiLang` | 百里零 bǎi lǐ líng | **Zerine** | **Crafting** mentor — general shop 零点杂货店 | Yes |
| `XiaHeAn` | 顾禾 gùhé | **Graminova** | **Farming** mentor — seed shop 幸福种子店 | Yes |
| `DingXiaoMiao` | 丁小葵 dīng xiǎokuí | **Pastelle** | **Ranching** mentor — ranch 绿茵牧场 | Yes |
| `FengXi` | 枫汐 fēngxī | **Delphin** | **Fishing** mentor — diving shop 深海观测站 | Yes |
| `NingFang` | 予画 yǔ huà | Lunelle | clothes shop 浮生织物 | Yes |
| `FangWenTing` | 沈霓 shěn ní | Neona | vehicle shop 超级马力 | Yes |
| `LuoHeGuang` | 洛和光 luò héguāng | Loren | arcade 玄同游戏厅 | Yes |
| `ChenXing` | 晨星 chénxīng | Stella | pet shop 哇呜哇呜动物之家 | Yes |
| `ALi` | 阿梨 ālí | Alex | furniture shop 梨木工坊 | No |
| `YeXingLan` | 叶星阑 yè xīnglán | Aurelis | restaurant 小叶府 | Yes |
| `ZiLu` | 初夏 chū xià | Solara | community centre 社区中心; **tutorial lead** — 23 of 59 `Mission.ML.*` main-line files, nearly double the next NPC | Yes |
| `YuTangTang` | 雨棠棠 yǔ tángtáng | Serena | salon 花迟妆造 | Yes |
| `JianXu` | 简煦 jiǎnxù | Sylvain | music shop 竹间乐器行 | Yes |
| `YouFang` | 游方 yóu fāng | Youfang | divination system | **former** romance candidate, cut content |
| `XiaQiLing` | 夏琳 xiàlín | Charlene | café/bar 日咖夜醉 (Hostal) | No |
| `DingXiaoLong` | 丁小龙 dīng xiǎolóng | Bruce | Pastelle's younger brother | No |
| `DingJianJun` | 丁建军 dīng jiànjūn | Sagewood | 丁 family | No |
| `TianRuLv` | 初建国 chū jiànguó | Regis | Solara's grandfather | No |
| `LinMengMeng` | 洛桃桃 luò táotáo | Momo | Loren's younger sister | No |
| `RenQiuYing` | 沈梅 shěn méi | Matilda | | No |
| `BoatMan` | 陆正航 lù zhèngháng | Marston | beach guard | No |
| `XiaChengShi` | 顾松年 gù sōng nián | Garrick | | No |
| `ChenShuHui` | 陈淑慧 chén shūhuì | Hattie | | No |
| `FangShiMiao` | 房时渺 fáng shí miǎo | Fang | **crossover** — My Time at Sandrock | No |
| `NiYa` | 妮雅 nī yǎ | Nia | **crossover** — My Time at Sandrock | No |
| `JinJiEr` | 金吉尔 jīn jí ěr | Ginger | **crossover** — My Time at Portia | No |
| `GaiSiTe` | 盖斯特 gài sī tè | Gust | **crossover** — My Time at Portia | No |

**Crossover characters have no shop, no profession, and no romance quest** — useful negative filter
when auditing content completeness. Nia is often *at* the seed shop and talks with Graminova, but
neither sells nor is related to him; proximity in schedules is not a relationship.

**Surname clusters** are a reliable relationship signal in the data: 丁 (Pastelle, Bruce, Sagewood),
洛 (Loren, Momo), 初 (Solara, Regis), 沈 (Neona, Matilda), 顾 (Graminova, Garrick).
Read the surname, not the workplace: Matilda shares 沈 with **Neona**, not with Graminova, despite
appearing around the seed shop.

**A machine-readable marker for the original roster's tier exists.** An entity that `Includes` a
`Role.Base_*_Expression` base identifies that expression profile — the original investigation counted 19 entities, described as the 14
romance candidates plus YouFang plus the 4 crossovers. It is more reliable than any naming
convention. Note also that rig prefixes (`F1`, `M3`, …) are **body builds, not genders** — Bruce
uses `F2`, Hattie uses `M3`. See `animation.md` §A3–A4.
The four Kickstarter NPCs below have authored friendship stories without this base; do not use it
as an exhaustive filter for named characters or story-bearing NPCs. The original roster's relationship
classification is owner-supplied, not a current `CanMarry` query.

### Professions, talents and their four mission families

`Config/Talent/TalentNode/` (46 nodes) + `Config/Talent/HonoraryTitle/` (31).

| Profession | Mentor | Talent tree | Mission token |
|---|---|---|---|
| Adventuring | Zephyria (`AVGMen`) | `Fight` | `Adventure` |
| Crafting | Zerine (`ShiLiHaiLang`) | `Production` | `Manufacture` |
| Farming | Graminova (`XiaHeAn`) | `Crop` | `Plant` |
| Ranching | Pastelle (`DingXiaoMiao`) | `Livestock` | `Livestock` |
| Fishing | Delphin (`FengXi`) | `Fishing` | `Fish` |

**Three naming vocabularies for the same five things** — talent nodes say `Fight` / `Production` /
`Crop` / `Livestock` / `Fishing`; missions say `Adventure` / `Manufacture` / `Plant` / `Livestock` /
`Fish`; only `Livestock` is shared. Plus the codename/shipped-name split above. Budget for all three
when searching.

**Four distinct mission families, easily confused:**

| Family | Count | Naming | What it is |
|---|---:|---|---|
| `Mission.FML.<Prof><NN>` | 176 | `Adventure01`, `Adventure01_Interim`, `Adventure02`, … | **The level-up chain.** |
| `Mission.Occupation.*` | 230 | `<NPC>_<Prof>_Lv<n>_Cycle_Collect_<nn>` | repeatable collection commissions |
| `Mission.Talent.*` | 1254 | `<NPC>_<Prof>_Lv<n>_Cycle_<nn>` | repeatable talent commissions |
| `Mission.TitleApply.<Tree>_Lv<n>` | 13 | uses **talent-node** vocabulary | honorary-title application |

#### The level-up chain (`Mission.FML.*`)

```
Adventure00 → 01 → 01_1 → 01_2 → 01_Interim → 01_Interim_2
            → 02 → 02_Interim → 03 → 03_Interim → 04 → 04_Interim → 05
```

Numbered steps are the level-ups themselves (`Mission.FML.Adventure01` is titled
成为见习冒险师 "Become an Apprentice Adventurer"; `Adventure05` is 成为冒险专家 "Become an Adventure
Expert", and its `CompleteDescription` records unlocking full shop access). `_Interim` steps are the
历练 "trial" stages between levels. A parallel `<Prof>Guide<NN>` chain runs alongside — 8–10 files per
profession, apparently the tutorial variant.

**The chain belongs to the mentor; other NPCs appear only in follow-up steps.** Measured by NPC token
occurrence across each chain's files:

| Chain | Files | Mentor | Others |
|---|---:|---|---|
| Adventure | 23 | `AVGMen` 21 | ZiLu 2, DingXiaoLong 2, YouFang 2, JianXu 1, DingXiaoMiao 1 |
| Plant | 26 | `XiaHeAn` 22 | ZiLu 4, ChenXing 2, XiaChengShi 2, YeXingLan 1 |
| Fish | 26 | `FengXi` 22 | ZiLu 3, DingXiaoLong 3, FangWenTing 2, ChenShuHui 2, ChenXing 1, BoatMan 1, ALi 1 |
| Manufacture | 27 | `ShiLiHaiLang` 22 | DingXiaoMiao 4, FangWenTing 3, FengXi 2, XiaHeAn 2 |
| Livestock | 21 | `DingXiaoMiao` 19 | NingFang 3, AVGMen 2, ZiLu 1, YuTangTang 1, JianXu 1 |

The first quest of each level-up chain is given by the mentor, other NPCs may take part in follow-ups,
and the chain always ends with the mentor since the last quest triggers the level-up.

#### Identifying mentors from data alone

`Mission.Occupation.*` gives a clean test: **mentors have `Lv1`–`Lv5` files for their own profession;
every other NPC has only `Lv1`, across all five professions.** That yields exactly
`BaiLiLing`→Manufacture, `DingXiaoKui`→Livestock, `FengXi`→Fish, `LanYu`→Adventure, `XiaHeAn`→Plant —
18 files each versus 10 for everyone else.

#### The repeatable commissions

`Mission.Talent.*` is a uniform matrix: **19 NPCs × 5 professions × Lv1–5 × cycles**, mirrored
file-for-file across `Config/Dialog/`, `Config/Mission/`, `Config/Indent/Indent/`,
`Config/IndentDetails/` and `Config/Item/RewardList/` — 1,254 files in each of the five containers.
Two cycles per NPC per profession-level, except farming Lv2–5 which has six. Every participating NPC
offers commissions in every profession; these are the grind, not the story.

Together with §5's finding that `Indent_IsRequestSubmit` is 41% of all template gating, the commission
system is the largest single content system reachable from dialogue.

**The Talent and Occupation families use shipped names, not codenames** — `BaiLiLing`, `ChuXia`,
`DingXiaoKui`, `LanYu`, `LinYuHua`, `ShenNi` all appear. `XiaHeAn` shows the rename is only partial
even in new content: his romance arc ships as `GuHe_*`, his commissions as `XiaHeAn_*`.


**Shop names encode owner names** — an independent confirmation of the rename map:

```
梨木工坊   Pear-wood Workshop   ← 阿梨   ALi      (梨)
小叶府     Little Ye Manor      ← 叶星阑  YeXingLan (叶)
零点杂货店  Zero-Point Grocery   ← 百里零  BaiLiLing (零)
```

Further corroboration: `AreaPlace.CoralTown_MusicShop` gates its door on
`AttachObject.DefaultEnableKey: ["JianXu_Door"]`, and `Schedule.*ZiLu*` files place her at
`CommunityCenter` while `Schedule.*YuTangTang*` place her at `Salon`.

**Two shop interaction systems, not one.** Ten owners carry `SellerWelcome` / `SellerEnd` dialogue
pools bound to `DialogLib.Sales{Welcome,End}.<codename>`; ChuXia, YuTangTang and JianXu carry none —
their shops run through `NPCStore` plus `ScheduleAI` instead. A mod adding shop banter needs to know
which system a given shop uses.

**Two shop-owning NPCs outside the romance roster** also carry Seller pools: `RenQiuYing`
(沈梅 / Matilda) and `XiaChengShi` (顾松年 / Garrick), with no shop-place schedule matched.
`MissionDialogLib.NPCSendGiftPOI_SeedShop_ShenMei` places Matilda at the seed shop, but see the
surname note above — she is Neona's relation, not Graminova's, and shop proximity is not kinship.

Unassigned shops: 报刊亭 (Newsstand), 美食摊 (FoodStall). Minor NPCs cover 鱼店 (FishMarket →
`AFei`, titled 鱼店老板) and 旅行小摊 (TravelShop → likely `HaMeng`, titled 游商).


### Names were recycled, not just changed

`Role.CoralTown_XiaHeAn` is 顾禾, but several of its own date and favour-chat templates carry
`Description` notes reading 小葵 — while `Role.CoralTown_DingXiaoMiao` is 丁小葵, whose short form is
小葵 and whose entity title is exactly 小葵.

So **小葵 refers to different characters depending on which file and which field you read.** Resolve
identity from `TagDescription` and nothing else; corroborate against the entity's `Calender` and pool
`Graphs`.

### A single NPC's content spans both names

Which name a file uses depends on when it was authored, so one character's content is split:

```
Role.CoralTown_ZiLu   (初夏 / ChuXia)
  ├─ Chat          → DialogLib.Chat.ZiLu             ← codename
  └─ TalkingBubble → DialogLib.TalkingBubble.ChuXia  ← shipped name

Role.CoralTown_XiaHeAn (顾禾 / GuHe)
  ├─ Chat / Date / FavorChat  → *.XiaHeAn.*          ← codename
  └─ romance mission arc      → MissionDialog.Relation.GuHe_Lv*  ← shipped name
```

Verified three ways on `ZiLu`: title 初夏, `Calender.CoralTown_ChuXia`, `SayHello` pool binds
`Dialog.SayHello.ChuXia`. Same triple-consistency on `AVGMen`, `NingFang`, `LinMengMeng`, `XiaHeAn`.

**Consequences:**

- Never match an NPC to their dialogue by filename. Resolve through the entity's `PoolData`.
- Any per-NPC statistic built from lib filenames is mis-attributed. The §9 defect list names libs
  correctly, but several rows belong to a different character than the filename suggests.
- Grepping the asset index for a character by name finds only the half of their content authored under
  that name.

**Two conclusions this trap reliably produces, both false:**

1. *"Marriage candidates LanYu, GuHe, DingXiaoKui, ChuXia and ShenNi have no `Role.*` entity file, so
   some second mechanism must attach their dialogue pools."* All five **do** have entity files, under
   codenames, and there is no second mechanism. The search matched filenames against shipped names.
2. *"顾禾 (GuHe / Graminova) is absent — unreleased or cut."* He is `Role.CoralTown_XiaHeAn`, one of
   the two best-equipped NPCs in the game at 36 pool slots, with a full romance arc under
   `MissionDialog.Relation.GuHe_*` and `IndentDetails.Relation.GuHe_*`.

All 14 marriage candidates plus YouFang resolve to entity files. Nothing is missing.

`Config/RoleDetail/` (59 files) mirrors the same codenames and is the closest thing to an NPC roster.


## Supplied identity reference

The separate identity table is preserved as an [original source](../_archive/originals/ZH-EN_reference.md). The maintained roster above owns identity lookup. Chinese identity is grounded in speaker labels and config bindings; English names and relationship descriptions remain owner-supplied. Reused historical codenames are scoped by the specific entity/config, not unconditional aliases.

## Kickstarter NPCs: current installed source comparison (2026-10-04)

**These four use the resident friendship system and have three- and five-heart stories, but lack
the expression/follower/dating configuration of the crossover NPCs.** They are a distinct content
profile; neither the old expression marker nor the romance roster finds all story-bearing NPCs.

Source: `work/content-index/index.sqlite`, snapshot `4b732b61e590aaf392d46b7ebb09f4d61acf2f30367139c449edaf5005c466cb`.
The four source JSON-collection bundles (`local/3073/786855.ab`, `786857.ab`, `786859.ab`, `786860.ab`)
and English localization bundle (`local/2304/589833.ab`) were SHA-256 checked against the installed
game on the audit date. All matched. English localization was also freshly decoded and compared
with `work/operators-localization/en.json`. Evidence, including full Unity asset identities, JSON
pointers, inherited bases, comparisons and localized fields, is saved in
[evidence.json](../../work/npc-kickstarter/20261004-comparison/evidence.json); reproduce with
[audit.py](../../work/npc-kickstarter/20261004-comparison/audit.py).

This is **extracted authored data**, not a runtime test. The index exposes the JSON collections;
compiled MessagePack formatter equivalence, controller bootstrap and UI availability remain
unverified. Kickstarter reward origin and non-romanceability were supplied by the owner;
`CanMarry: false` independently corroborates the latter. No prior-build diff was performed to date
their introduction. Unlike the original roster above, **these English names are independently
verified against the installed localization table**.

### Identity and story aliases

| English | Chinese | `Role.CoralTown_` suffix | Everyday dialogue/calendar token | Story token |
|---|---|---|---|---|
| Azra | 阿兹拉 | `KS_Abigail` | `Abigail` | `Abigail` |
| Aiko | 亚衣子 | `KS_Fuleidelike` | `Fuleidelike` | **`Frederick`** |
| Some | 萨姆 | `KS_Qingmuweilai` | `Qingmuweilai` | `QingMuWeiLai` |
| Sherria | 谢莉娅 | `KS_Xieliya` | `Xieliya` | `XieLiYa` |

Both `CDisplayableTitle.Title` and `CRoleInfo.Name` English keys resolve to the supplied names.
The Chinese titles agree with the bound chat/self-introduction `TagDescription` labels. Azra and
Aiko additionally carry English alias tags; Some and Sherria do not. Resolve the latter through
localization and entity bindings. Sherria's affection template uses the separately cased
`RoleDetail.CoralTown_KS_XieLiYa`. Aiko is particularly easy to miss: her relation missions use
`Frederick`, not `Aiko` or `Fuleidelike`.

### Shared systems and reduced social configuration

| Feature | All four KS NPCs | Comparison with existing NPCs |
|---|---|---|
| Resident foundation | `Role.Base_Resident`; inherited navigation, scripting, map/minimap markers, persistence, schedule simulation, gift limits and gift AI | Same foundation as established residents; not a separate NPC engine |
| Body and face | F1 for Azra/Some/Sherria; F3 for Aiko; each includes its own `Role.Face_*` animation map | Shared body families, individual facial redirects; absence of `_Expression` does **not** mean no facial animation |
| Friendship | `NPCAffection` and matching `RoleDetail`; configured effects for stars 0–6 | Same seven configured tiers as Nia/Stella; Momo's detail has 0–5 |
| Gifts | Five preference levels, populated return/face-send drop lists, two-heart gift mail | Same gifting machinery and authored personal preferences |
| Dialogue | Exactly **12 bound pools** and **24 entries in each bound Chat library** | Nia has 29 pools, Momo 28, Stella 31, Solara 34 in this snapshot |
| Routine | Own calendar, weather/season schedules, home area entity, biography, birthday, portrait/map art, prologue and narrative-audio references | Normal resident integration; audio references alone do not verify audible playback |
| Marriage | `CanMarry: false` for all four | Agrees with owner-supplied non-romanceable status |
| Dating/following | No `Role.Base_Lover`, `Role.Base_Follower`, follower emoji or `Role.Base_LiveTogether` base; no inherited `DatingTarget` or `FollowerAI` | Nia includes Lover/Follower/Expression despite `CanMarry: false`; the KS profile is narrower than the crossover profile |
| Expression profile | No `Role.Base_*_Expression` | The installed collection still has 19 entities with this direct include; none is KS |
| Shops/professions | No seller pools or direct shop components; no named Talent, Occupation or profession-level-up chain participation found | Bios describe occupations, but that does not make them profession mentors or members of the repeatable commission matrix |

All 12 pools resolve to existing collection records: `SayHello`, `SayHelloRepeated`, `Chat`,
`SayGoodbye`, `GiftReturnGift`, `SelfIntroduce`, five `GiftReceived_*` reactions and `TalkingBubble`.
They omit the established characters' `GiftReceiving`, cancellation/limit, gift-description,
`SenseDailyGreet`, `NPCSendGift`, online greeting and date-selection **pool bindings**. Azra has
extra DailyGreet/SendGift/GiftDescription libraries on disk, but her entity does not bind those
additional slots. Existence of a library is not evidence that the entity exposes its slot.
Likewise Some's biography describes online communication, but she has no online greeting pools.
That alone does not establish whether the phone can use another dialogue route.

The inherited resident `NPCIndentClient` still accepts generic `NPCIndent.Mystery`; the absence of
named profession commissions does not mean all commission infrastructure is absent.

### Friendship stories are present for every member

| NPC | Three-heart story | Five-heart story | Additional difference |
|---|---|---|---|
| Azra | **Challenger** | **Pink Meteor** | Also has `Mission.Relation.Abigail_MakeSnowMan`; three schedule templates, with spring reused for summer/autumn |
| Aiko | **Tideworn Dreams** | **Dreams Beneath the Bamboo** | Story files use `Frederick`; five schedule templates |
| Some | **Online Friend** | **Final Easter Egg** | Story files use `QingMuWeiLai`; five schedule templates |
| Sherria | **Battle of Prodigies** | **Sherria's Transformation** | Visible missions use `_Repair` rather than `_Invite`; five schedule templates |

The eight `Mission.Relation.<story>_Lv{3,5}_Main_MainLine` graphs contain actual
`CheckNPCAffectionStar >= 3/5` gates and are neither `NotOpen` nor `Deprecated` in these sources.
Their hidden controller, `Mission.Relation_Mission_Mainline_KS`, configures eight POI activations.
`Mission.Fix.KSRelationPoiRecover` has matching recovery entries for all eight. This is stronger
evidence than filenames, but does not independently prove that the live game bootstraps this
controller. Several Lv3 controller titles misleadingly say "5 Hearts"; trust the condition fields.
`Relation` therefore does not mean "romance quest".

### Character-specific preferences and data caveats

At preference level +2, Azra favors `Doll`/`HandCraft`, Aiko `Book`/`HandCraft`, Some
`VestigePlants`/`Food_Pet_Meat`, and Sherria `Dish_Veg`/`Dish_Meat`. Birthdays are respectively
month/day 4/18, 2/22, 4/20 and 2/27. Their biographies integrate them into the existing cast:
Azra arrives for Zephyria's recruitment and rides with Neona; Aiko is a mysterious visiting scholar;
Some introduces herself as Solara's online friend; Sherria challenges Stella and joins her band.

Several shared fields warrant caution:

- All four details set **`Cohabitation: true`** and list both `Item.FriendshipNecklace` and
  `Item.LoveRing`. Nia has the same combination with `CanMarry: false`. The KS entities have no
  Lover/Follower/LiveTogether base, their calendars have empty `LivingTogether`, and their
  affection `UnlockActions` arrays are empty. These detail fields alone do not establish usable
  romance, cohabitation or breakthrough interactions.
- All four have **`ShopWeekDiscount.petshop-3` at three hearts**, including characters who do not
  own the pet shop. Stella's detail also uses it. Possible template reuse is an inference;
  whether it affects the live discount requires runtime tracing.
- Azra's structured `RoleInfo.JobInfo` says scholar while Aiko's says world-traveling adventurer;
  their biographies/self-introductions identify them the other way around. This looks swapped;
  identity and gameplay profession should not be inferred from that field alone.
- Azra/Aiko/Sherria all point `FullImage` at `StandingPainting/F3_021.png`; Some points at
  `StandingPainting/F1_026.png`, also used by Stella. Their head portraits use individual face
  IDs. These are shared configured image paths, not a verified rendering defect.
- Azra's return-gift drop list retains a 小葵 authoring description, repeating the original
  reference's stale-note problem. Bound IDs, item entries and current labels identify the NPC.

Practical classification: retain **origin**, **friendship stories**, **marriage eligibility**,
**follower/dating components** and **expression profile** as separate attributes. The four KS NPCs
have the first two, explicitly disable marriage, and lack the latter two profiles in this source.

### Asset packaging, world initialization, and use as a mod template

Follow-up inspected the current Unity prefabs and the building scene, rather than relying only on
config paths. [packaging-evidence.json](../../work/npc-kickstarter/20261004-comparison/packaging-evidence.json)
records fresh bundle hashes, prefab/scene serialized files and PathIDs, root component data, family
records and metadata leads. Reproduce with
[inspect_packaging.py](../../work/npc-kickstarter/20261004-comparison/inspect_packaging.py).

**No separate KS serialization format or general-purpose KS loader was found in the inspected
paths.** Their content uses the same configuration collections, Unity prefab classes and family
initialization components as ordinary residents. The observed difference is packaging and content
selection, not a distinct NPC implementation.

| Layer | Freshly inspected KS evidence | Ordinary comparison |
|---|---|---|
| Entity configuration | Entries in `JsonCollect/Entity.bytes` | Same TextAsset contains the other residents; same `EntityTemplate` name/Includes/Ignores/Components structure |
| Relationship and routines | Shared `RoleDetail.bytes`, `Schedule/Calender.bytes`, `Schedule/Schedule.bytes` | Same per-family collection assets used by other residents |
| Character art | All four `ArtSource/Character/NPC/KS_*.prefab` roots in `local/2561/655718.ab` | Stella in `655716.ab`, Nia in `655706.ab`; all six root component class lists are identical |
| Root components | Transform, CapsuleCollider, Rigidbody, AkGameObj, KMovementHub, KRLGameLODUnit, KRoleLOD, KRendererLOD | No KS-specific component in these root lists; this does not claim identical meshes, child hierarchies or rig data |
| Movement | Azra/Some/Sherria reference `Movement_F1.prefab`; Aiko references `Movement_F3.prefab` | Shared movement prefab families, not KS-only movement classes |
| Family records | Four one-member `FamilyGroup.CoralTown_House_KS_*` records in `JsonCollect/NPCGen/FamilyGroupConfig.bytes` | Nia's one-member family has the same field structure, `BirthRate: 1` and `MinGenLevel: Low` |
| Scene initialization | Four `FamilyInit`-shaped components in `StarSandIsland_LogicBuilding_05.unity`, bundle `local/2816/720914.ab` | The pet-shop family initializer uses the identical serialized MonoScript reference and field shape |

The family IDs are `KS_ABGE`, `KS_FLDLK`, `KS_QMWL` and `KS_XLY` under
`FamilyGroup.CoralTown_House_`. Each member points at the corresponding `Role.CoralTown_KS_*`
template with an `Occupier_<dialogue-name>` tag. Scene components set `TemplateName` to the family
ID, `Savable: 1`, `UseSyncInit: 0`, and bind `AllMemberOwnerScope` plus a matching tagged
`SingleMemberOwnerScope`. Metadata identifies this field set as `Role.FamilyInit`, and declares
`KFamilySpawner.InternalCreateEntity(context, template)` at RVA `0x338bbc0`. The spawn method's body
was not freshly traced. This is the authored world-entry chain, not a runtime execution proof:

```text
scene FamilyInit -> family template -> member RoleTemplateID -> entity template
                                                        -> RLObject.PrefabPath
```

**Yes: a KS NPC is a useful structural template for a new non-romanceable resident.** Its smaller
social configuration reduces dependencies compared with a romance candidate. It does not provide
a ready-made mod import route, and its shared placeholder fields should be cleaned rather than
blindly copied. Match the F1/F3 body profile to the intended art.

A proposed resident mod would need the following integration work:

1. Register new entity/detail/calendar/schedule/dialogue/gift records under unique, stable IDs and
   resolve their dependencies. Preserve exact casing. Entity composition must run as well as map
   registration; the traced `KEntityTemplateSet.Build` constructs inherited components.
2. Supply a character prefab, portrait/map art and any required animation resources through a
   resource path the game can resolve. An `ArtSource://` string alone does not mount a mod bundle.
3. Create a persistent actor through a family initializer or another validated actor-creation
   route. Copying a character prefab alone provides no family, occupancy scope or scheduled home.
   The scene's `serializedGuid`/pinned identity must not be duplicated for a new resident.
4. Add localization and activate optional story/POI content separately. Registering templates does
   not construct their world consumers; the built-in KS controller/recovery records enumerate the
   four shipped characters, not arbitrary new mods.
5. Verify appearance, interaction, routines, save/reload and world transfer with the mod enabled.
   Shared resident save components suggest reuse of the standard persistence path, but a stable
   ID and successful reload are still necessary runtime checks.

Relevant existing foundations are [entity composition](../systems/moonlit-companion-baseline.md)
and [registration/reference timing](../systems/template-loading.md). Metadata additionally declares
`KEntityTemplateSet.RegisterRuntimeTemplate(template, replaceExisting)` at `0x2e3fec0` and
`RemoveRuntimeTemplate` at `0x2e400f0`; these are **candidate APIs**, not a newly verified injection
contract. The official bridge has a pet-entity injection method (`InjectPetRecords`, `0x4538760`),
but its declared `ModData` record families have no resident-NPC collection. Pets demonstrate a
dynamic-entity integration lead, not a generic human-NPC manifest capability. A runtime plugin is
the plausible route; a turnkey official-modkit NPC package has not been established here.
