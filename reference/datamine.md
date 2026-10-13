# datamine.md — 解包数据档案

**这是本 skill 唯一的 `[官方-解包]` 级来源。** 其余文档的 `[官方]` 指商店页/官方截图，`[wiki]` 指英文 wiki，
`[二手]` 指社区玩家实测。

解包日期：**2026-09-29**。解包对象：Steam Demo build（buildid `25382790`）。

---

## 1. 解包对象与技术参数

| 项 | 值 |
|----|----|
| Demo AppID | `4349200`（正式版 `4348910`） |
| buildid | `25382790`（timeupdated 1789703158） |
| depot | `4349201`，939 MB / 下载 269 MB，**无加密清单** |
| 引擎 | **Unity 2021.3.45f2** + **IL2CPP** + **Addressables** |
| 获取 | `steamcmd` 可**匿名读取** app info，但**下载需要账号 license**（免费 demo 也要"添加到库"） |
| 工具链 | Il2CppDumper v6.7.46（`win` 自包含版）+ UnityPy 1.25.3 + TypeTreeGeneratorAPI |
| 存档 | `%USERPROFILE%\AppData\LocalLow\Questing Goose Studio\Probably Stolen`，格式 `*.es3`（Easy Save 3） |
| 项目代号 | **Emporium**（资源路径 `Assets/Resources/Emporium/...`） |

**踩坑记录**：`Il2CppDumper-net6-win` 是框架依赖版，本机无 .NET 会失败；改用 `Il2CppDumper-win`（13 MB 自包含）。
它**忽略 outputDir 参数**，产物落在 exe 同目录。

---

## 2. ⚠️ 最重要的方法论警告

**解包内容 = 该 build 内的全量资源，包含 demo 未开放的部分。**

文本表里存在 `wip`（开发中）、`unknown_start_type`（存档已损坏）这类标记，说明表是**完整版设计数据**，
不是 demo 实际可玩范围。凡引用解包数据，必须区分：

- **可玩范围内**：可作 `[官方-解包]` 直接断言
- **表内存在但未开放**：标注"（解包可见，demo 未开放）"

例：NewGame 表列出 **13 个开局**，但 demo 商店页只写 3 场景 + 硬核。13 是设计全量，不能说"demo 有 13 个开局"。

---

## 3. 本地化表清单（14 张 / 5596 条中文 / 5680 个 key / 0 失配）

Unity Localization + Addressables。zh 表存值（`m_Id` → 文本），`Shared Data` 表存 key（`m_Id` → `m_Key`），按 id 对齐。

| 表 | 中文条目 | 内容 |
|----|---------|------|
| Dialogue | 2267 | 全部对话 |
| Mechanic | 1157 | 机制说明 + UI 标签 + **物品分类体系** + **事件** |
| Item | 818 | 物品名 / 描述 / 风味文本 |
| UI | 569 | 界面文案 |
| ClientName | 193 | 顾客名 |
| RepPerkTable | 138 | **派系声望特性（穿透/负面）** |
| PhoneDialogue | 87 | 电话对话（王尔德网络） |
| MainMenu | 78 | 主菜单 |
| NetworkUpgrade | 77 | **王尔德网络全部升级项** |
| NewGame | 72 | **开局场景与初始装备** |
| PerkTable | 71 | **全部特性** |
| Hint | 34 | 提示 |
| Tutorial | 24 | 教程 |
| Interactable | 11 | 可交互物 |

**实际打包 10 种语言**（en/de/fr/it/ja/ko/ptBR/ru/es/zh）——商店页只标 5 种，法/意/韩/葡/西为未公开语言。

---

## 4. 模块划分（一手，来自 `catalog.json` + `dump.cs`）

游戏程序集 `Assembly-CSharp.dll`，**8517 个类型**。命名空间为全局。模块按类族清晰切分：

| 模块 | 代表类 |
|------|--------|
| 机器 | `MachineMoistureFarm` `MachinePurifier` `MachineFurnace` `MachineBottlePrinter` `MachineWineRack` `MachineHydroponic` `MachineFeedDispenser` `MachineDesequencer` `MachineBlender` `MachineChemFinisher` `MachineHeatingPlate` `MachineFridge` `MachineProjector` `MachineRecharger` `MachineDealMaker` `MachineBoxDispenser` `MachineCassettePlayer` `MachineTurboBoosterAdv` `MachineAlarm` |
| 物品 | `ItemData` `ItemCondition` `ItemFeature` `ItemContextHandler` + 各 `*ItemDirectory`（Armor/Food/Guns/Container/Furniture/Explosive/Amenities/Construction/Npc/Player/RuinedMachine） |
| 顾客 | `StoreClient` `StoreClientData` `StoreClientCounter` `StoreClientFactionSetup` `StoreClientList{Water,Appraisal,Security,Wanted}` `ClienteleUIManager` |
| 声望 | `StoreReputation` `StoreReputationPerk` `ReputationElement` |
| 鉴定 | `AppraisalHelper` `AppraisalServiceHelper` `AppraisalGuildInteractionEvent` |
| 搜查/罪案 | `RaidManager` `RaidScene` `InspectionUIManager` `Evidence` `ContrabandHelper` `StolenHelper` |
| 改造体 | `AugHelper` `AugScanner` `RuntimeAugments` |
| 事件总线 | `WildUpgradePurchasedEvent` `InspectorArrivedEvent` `InspectionBribeEvent` `AppraisalGuildInteractionEvent` `WantedNotReportedEvent` `CustomerReportedEvent` `ConfrontEvent` `GameOverEvent` `NewGameStartedEvent` `StartingPerkSelectedEvent` |
| 经营 | `PlayerStore` `AmenitiesManager` `CommissaryData` `EmporiumAnalytics` `Loadout` |

---

## 5. 相对社区数据的关键修正

| 主题 | 社区/skill 原说法 | 解包一手 |
|------|------------------|---------|
| 派系数量 | 5 个 | **6 个**：下层区(LL) / 治安部(SEC) / 黑市(BM) / 上层区(UL) / 革命军(REV) / 卡特尔(CARTEL) |
| 香水 | "香水 +15%" | **两种**：「同步」神经活性香水 **+15%**；「本源」费洛蒙香水 **+25%**（后者是违禁品）；同时只能有一种香水生效 |
| 哨兵病 | "OCR 不明，未核实" | **「哨兵崩溃综合征」**：致命且**无法治愈**的自身免疫病，**每周必须注射 1 次免疫宁**，开局自带 1×免疫宁 |
| 警觉 | "不会丢东西" | **夜间永远不会遭遇抢劫** |
| 舌灿莲花 | "声望增长 +33%" | **交易产生的声望**增加（不是全部声望） |
| 奇人异士 | "可多选特性但附带负面" | **初始特性槽位上限 +N 个** |
| 极简主义者 | 未记录 | 主物品栏 **24×10 → 20×10** |
| 声望特性 | "除 2 个数值外无公开数据" | **完整 138 条**（6 派系 × 正/负，含穿透档） |
| 屠宰操作 | "工具放工具箱按数字键"（纯二手，无官方依据） | **刃具体系**：物品需带 **`BLADE_ITEM_TAG`** 才能屠宰；入口 `HusbandryHelper.OnButcher()`，由标签系统回调；存档计数 `animalsButcheredTotal`，界面文案**「已屠宰动物数：{0}」** |
| 剥皮刀 | "买一把刀" | **是屠出来的奖励**：`isSkinningKnifeRewardGiven` + `CheckSkinningKnifeReward()`，屠够数白送（阈值未提取） |
| 捕鼠夹 | 未记录 | `husbandry_mouse_trap`，官方描述要求放**合成奶酪**做诱饵；抓到的是 `husbandry_rat`，**与自养鼠同一物品 ID**，带 `ALLOWED_IN_CAGE_TAG` 可直接入笼 |
| 朊病毒 | 「脘病毒」（错字） | 官方为**朊病毒病** `husbandry_status_prion`；代码有 `CheckCannibalism`（同类相食检测）方法 |

---

## 6. 数据位置

### 6.1 已转写进 skill（**运行期只读这里**）

| skill 内文件 | 来源 | 说明 |
|--------------|------|------|
| [items.md](./items.md) | `Item` 表 | 高频道具速查，分 12 区 —— **道具问题的第一入口** |
| [items-full.md](./items-full.md) | `Item` 表 | 394 条全量原文，39 KB，**重文件** |
| [events.md](./events.md) | `Mechanic` 表 | 事件系统 132 条 |
| [factions.md](./factions.md) | `RepPerkTable` | 138 条声望特性 |
| [npc-events.md](./npc-events.md) | `NetworkUpgrade` | 王尔德网络 77 项 |
| [professions.md](./professions.md) | `NewGame` / `PerkTable` | 13 开局 + 71 特性 |
| [water.md](./water.md) | `Item` + `Mechanic` | 水线全套 |
| [brewing-rats.md](./brewing-rats.md) | `Item` + `dump.cs` | 酿酒养鼠 + 屠宰体系 |
| [scavenging.md](./scavenging.md) | `sharedassets1.assets` 的 `LootTable` / `TableGroup` | 拾荒掉落概率 15 张表（2026-10-13） |

> **以上已足够回答全部已收录问题。运行期不要再回下面的原始文件去搜。**

### 6.1.1 拾荒掉落表的解包方法（2026-10-13）

掉落表**不在本地化表里**，是序列化的 `ScriptableObject`（RNGNeeds `ProbabilityList`）：

1. `dump.cs` 定位：`LootTable`（字段 `ProbabilityList<string> table`）与 `TableGroup`（字段 `ProbabilityList<LootTable> tableGroup`）。
2. `TypeTreeGenerator("2021.3.45f2")` 喂全部 94 个 DummyDll → `env.typetree_generator` → `obj.read_typetree()`（不带 typetree 时这批对象会 `ValueError`，见 `probe_loot.py` 的 ERR 计数）。
3. 全部落在 `sharedassets1.assets`（13 LootTable + 2 TableGroup）；`resources.assets` / `sharedassets0.assets` 已扫过，**无此类对象**。
4. 转储脚本 `.tmp/dump_loot.py` → `loot_dump.json`；概率口径 `m_BaseProbability`（已归一化 Σ=1.00）。
5. 注意：`allModuleTable`（含神经核心 1% / 0.5%）**不在拾荒 TableGroup 链上**，引用时必须说明用途未确认。

### 6.2 原始解包产物（工作区，**构建期专用**）

```
.tmp/extract/
  loc_zh.json          14 张表原始（m_Id + 中文）
  loc_shared.json      14 张 Shared Data（m_Id + key）
  loc_zh_joined.json   key → 中文（按表分组）
  loc_zh_all.tsv       扁平表：table \t key \t 中文
  modules/*.tsv        按模块切片（items/dialogue/perks/rep-perks/wild-network/newgame/events/water/machines/types/...）
  items_full.md        道具全表中间产物（gen_items.py 生成，已转写进 skill）

.tmp/tools/Il2CppDumperWin/
  dump.cs              19.5 MB，8517 类全字段
  DummyDll/            95 个程序集（typetree 用）
  stringliteral.json   硬编码字符串字面量（23,097 条）

.tmp/il2cpp_out 空（输出被写到 exe 同目录）
```

**为什么要把它们挡在运行期之外**：`dump.cs` 19.5 MB、`stringliteral.json` 23k 条，
一次 grep 的代价远超读 skill 内任何文档 —— 这是 0.5.x 回答要花 3 分钟的根因。
数据全部落盘后，`[官方-解包]` 的查询成本降到「读一份 200 行以内的 markdown」。

**格式化占位符**（`{0}` `{0:P0}`）的**具体数值不在此层**，在 IL2CPP 代码的配置类里，需进一步从
`dump.cs` + `GameAssembly.dll` 提取。当前 skill 中凡标 `{0}` 的条目均保持占位符原样。
