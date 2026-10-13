# scavenging.md — 垃圾场拾荒掉落表（官方概率）`[官方-解包]`

> **来源**：解包 `sharedassets1.assets` 中的 `LootTable` / `TableGroup` 资产
> （RNGNeeds `ProbabilityList` 结构，共 **13 张 LootTable + 2 张 TableGroup**），demo buildid `25382790`。
> 构建期转储：`.tmp/loot_dump.json`（**运行期不访问**，数据已抄录在下）。
>
> **概率口径**：字段 `m_BaseProbability` 已按权重归一化（每张表 Σ = 1.00），
> 可直接读作「该次判定抽中它的概率」。`m_Weight` 是归一化前的原始权重，二者成固定比例。
> `m_Enabled=0` 的条目权重为 0，**当前不会掉出**（本作有 2 条）。

## 1. 判定链（两层）

```
垃圾场 POI
 └─ POI_dumpingGround 表   → 决定这一处生成哪种"堆"
      └─ 堆对应 TableGroup  → 决定抽哪张子表
           └─ 子表 LootTable → 决定具体掉出什么物品
```

一次拾荒 = 两次抽样（先定表、再定物），所以**单个物品的净概率 = 两段相乘**。

## 2. 生成哪种堆（表 2001 `POI_dumpingGround`）

| 堆 | 概率 |
|----|------|
| 废料堆 `scrap_pile` | **45%** |
| 垃圾堆 `junk_pile` | **40%** |
| 新鲜废料堆 `fresh_scrap_pile` | **15%** |

## 3. 两张主表（TableGroup）

### 3.1 `dumpingGroundTG`（表 2003）——「翻过的/普通废料堆」

| 子表 | 概率 | 抽到什么 |
|------|------|----------|
| `junkTable` 垃圾 | **65%** | 见 §4.1 |
| `materialTable` 材料 | **15%** | 见 §4.5 |
| `dumpingGroundMedical` 医疗 | **5%** | 见 §4.2 |
| `householdTable` 日用品 | 4.75% | 见 §4.3 |
| `packedFoodTable` 包装食品 | 4.75% | 见 §4.6 |
| `toolTable` 工具 | 2% | 见 §4.8 |
| `makeshiftWeaponTable` 土制武器 | 2% | 见 §4.4 |
| `t1moduleTable` T1 模组 | 1% | 见 §4.7 |
| `t2moduleTable` T2 模组 | **0.5%** | 见 §4.7 |

### 3.2 `dumpingGroundFreshTG`（表 2002）——「新鲜废料堆」

| 子表 | 概率 | 抽到什么 |
|------|------|----------|
| `materialTable` 材料 | **40%** | 见 §4.5 |
| `householdTable` 日用品 | 15% | 见 §4.3 |
| `makeshiftWeaponTable` 土制武器 | 15% | 见 §4.4 |
| `packedFoodTable` 包装食品 | 15% | 见 §4.6 |
| `toolTable` 工具 | 10% | 见 §4.8 |
| `t1moduleTable` T1 模组 | **5%** | 见 §4.7 |

> **新鲜废料堆不含 `junkTable`** —— 翻不出纯垃圾，材料/工具/模组占比显著更高。这是两种堆的核心差别。

## 4. 子表明细

### 4.1 `junkTable` — 垃圾（表 2008，6 项）

| 物品 | 概率 |
|------|------|
| 垃圾 `junk` | **85%** |
| 碎玻璃 `glass_shard` | 3% |
| 报废模组 `system_module_ruined` | 3% |
| 铅管 `pipe_weapon` | 3% |
| 空啤酒瓶 `empty_beer_bottle` | 3% |
| 刮刮乐彩票 `scratcher` | 3% |

### 4.2 `dumpingGroundMedical` — 医疗（表 2006，3 项）

| 物品 | 概率 |
|------|------|
| 绷带 `bandage_item` | 33.3% |
| 止血绷带 `hemostatic_bandage_item` | 33.3% |
| 外用绷带 `topical_bandage_item` | 33.3% |

### 4.3 `householdTable` — 日用品（表 2007，8 项，各 12.5%）

咖啡因药片 `caffeine_pill` · 牙膏 `toothpaste` · 滤水器 `water_filter` · 四合一洗涤剂 `shampoo` ·
一卷纸巾 `paper_towel` · 一卷厕纸 `toilet_paper` · **整盒水质试纸** `full_water_test_strip_box` ·
**整盒净水药片** `full_water_purification_tablet_box`

### 4.4 `makeshiftWeaponTable` — 土制武器（表 2009，4 项，各 25%）

玻璃刀 `glass_shard_shiv` · 美工刀 `box_cutter` · 厨刀 `kitchen_knife` · 铅管 `pipe_weapon`

### 4.5 `materialTable` — 材料（表 2010，8 项，各 12.5%）

废金属 `scrap_metal` · 金属螺丝 `nuts_metal` · 助熔剂 `flux_agent` · 3D 打印耗材 `printer_plastic` ·
线缆 `wire` · 枪械零件 `gun_part` · 电子元件（普通）`common_electronic` · 韧棉织物 `kotton_fabric`

### 4.6 `packedFoodTable` — 包装食品（表 2012，13 项）

各 **8.18%**（w=106）：繁星果糊 · 能量饮料 · 汽水 · 猫咪巧克力棒 · 轻食能量棒 · 红魔鬼啤酒 ·
碳酸代乳 · 代糖果汁 · 合成肉 · 一板零嚼 · 速食拉面
各 **5%**（w=65）：努特加 · 贝氏优质香草冰淇淋

### 4.7 模组表

**`t1moduleTable`（表 2013）** — 随机性能 / 随机效率 / 随机质量模组，各 **33.3%**
**`t2moduleTable`（表 2014）** — 性能 / 环保 / 精炼模组，各 **33.3%**

### 4.8 `toolTable` — 工具（表 2015，5 项，各 20%）

螺丝刀 `screwdriver` · 剪线钳 `wire_cutter` · 模组提取器（基础）`module_extractor` ·
等离子切割机 `welder` · 一次性涡轮增压器 `turbo_booster`

## 5. 净概率速查（两段相乘得出）

| 目标 | 废料堆（普通） | 新鲜废料堆 |
|------|----------|----------|
| 垃圾 | **≈55.3%** | **0%** |
| 任一材料（每种） | ≈1.9% | **5%** |
| 任一工具（每种） | 0.4% | **2%** |
| 土制武器（每种） | 0.5% | **3.75%** |
| T1 模组（每种） | 0.33% | **1.67%** |
| T2 模组（每种） | **0.17%** | 0% |
| 任一医疗（每种） | 1.67% | 0% |
| 任一日用品（每种） | 0.59% | 1.875% |
| 任一食品（贵的那两种） | ≈0.37% | ≈1.15% |

读法：**要材料/工具/模组 → 去新鲜废料堆；要纯垃圾 → 普通废料堆**。

## 6. 用途未确认的表（同样解出，但不在这条拾荒链里）

| 表 | 内容 | 备注 |
|----|------|------|
| `allModuleTable`（表 2005） | 10 项：损坏/报废模组各 11.75%、性能/效率/质量各 15%、超频/精炼/环保各 10%、**神经核心（受限）1%、（无限制）0.5%** | 用途**未确认**（非拾荒 TG 的成员，可能是箱子/任务表） |
| `accessCardTable`（表 2004） | 服务 30% / 医疗·工程·治安各 20% / 指挥 10%；补给、研发 `m_Enabled=0`（当前不掉） | 用途**未确认** |
| `medicalTable`（表 2011） | 8 项：嗅盐/绷带/止血绷带/外用绷带/医用酒精各 15%、奥克西莫注射器/南丁格尔软膏各 10%、外科手术工具 5% | 用途**未确认** |

> **神经核心（无限制）当前只在 `allModuleTable` 里以 0.5% 出现**，且该表不在拾荒链上 ——
> 社区「拾荒能出神经核心」的说法**未被本数据支持**，标**待核实**。

## 7. 工具与特性的加成（未解包）

| 手段 | 官方描述 | 数据状态 |
|------|----------|----------|
| 手电筒 | 「垃圾场拾荒受伤几率降低」 | 未解包 |
| 螺丝刀 | 拾荒 +10% 螺丝 | 加成挂在 `m_InfluenceProvider`，未解包 |
| 剪线钳 | 拾荒 +10% 线缆 | 同上 |
| 等离子切割机 | 拾荒 +10% 废金属 | 同上 |
| 拾荒扫描仪 | 提高贵重物几率（同时只吃一台） | 同上 |
| 受伤率 | 每次 10.00% 轻微 / 2.25% 严重 | `[wiki]`（见 systems.md） |

> `ProbabilityList` 里每条都带 `m_InfluenceProvider` / `m_InfluenceSpread` 字段——
> 工具加成就是通过它缩放概率。**具体缩放系数在 IL2CPP 代码层，尚未提取。**

## 8. 未收录 / 待核实

- **`junk_pile`（垃圾堆）具体走哪张表** —— 未确认。按命名推断可能是 `junkTable`，但**无证据**，不写死。
- **TableGroup ↔ 堆名的对应（`dumpingGroundTG` ↔ 废料堆、`dumpingGroundFreshTG` ↔ 新鲜废料堆）是**按命名与概率结构**推断**的，未见代码明文。
- 每次拾荒的**抽样次数上限**（`GetMaxScavAttempts()`）与其数值——未提取。
- 「新鲜」与「普通」在游戏内的**实际区分条件**（时间/是否被翻过）——未解包。
