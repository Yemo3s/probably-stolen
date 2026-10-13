# item-images.md — 道具图库索引（278 张，全部解包自游戏本体）

> ## ⚠️ 本发布包不含图片文件（2026-10-13 移出）
>
> 全部图片资产（278 张道具图标 + 12 张分区拼图 + 4 张官方截图，共 **2.36 MB**）已从 skill 移出到本地档案：
> `D:\WorkSpace\WorkBuddy\2026-09-29-14-06-33\.archive\deep-space-pawnshop\assets\`
>
> **移出原因**：① 平台目录层级上限为「根/二级/文件」，`assets/items/*.png` 属第 3 层，整包会被拒；
> ② 图标与截图为游戏资产，公开分发有版权风险；③ 问答贴图功能已于 2026-09-30 关闭，移出对功能无影响。
>
> **恢复方式**：把档案目录里的 `assets/` 整体移回 skill 根目录即可（下表文件名即对应关系）。
> 若只想保留图而不违反层级限制，可把 `assets/items/*.png` **平铺到 `assets/` 一层**并加前缀。
>
> **本文件仍然有效** —— 它记录的是「物品 ↔ 图名」的对照关系与重建方法，与图片文件是否随包无关。

> **来源**：`[官方-解包]` demo buildid `25382790`（resources.assets / sharedassets1.assets 的 Sprite 直出）。
> 用户要某个道具的图时：单件 → `assets/items/<文件名>.png`；整类概览 → `assets/items/sheets/cat_<编号>.png`。
> **展示规则**（2026-09-30 / 2026-10-13 修订）：问答模式**不贴图**，且本发布包无图可贴。

> 生成管线与坐标修复方法见 [datamine.md](./datamine.md)。


标 `※` 的条目是**替代图**（原始 sprite 的序列化纹理缺内容，用了同名变体/近似图，或对应关系待核对）。


## 1. 水线

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 水分收集器 | `moisture_farm.png` |  |
| 净水器 | `purifier.png` |  |
| 海德拉微型净水器 | `portable_water_purifier.png` | 只到基础水 |
| 蒸发器 | — | 真无图（见文末清单，v0.8.2 下架碎片图） |
| 紫外线灯 | `uv.png` | 只杀微生物 |
| 净水药片 | — | 真无图（见文末清单，v0.8.2 下架碎片图；药瓶见图 `water_tablet_container.png`） |
| 滤水器 | `water_filter.png` | 纯度有上限 |
| 高级滤水器 | `water_filter_adv.png` | 每日自恢复50耐久 |
| 水罐 | `water_pitcher.png` | 可装滤芯；已换完整罐身图 |
| 水培芦苇滤芯 | `hydroreed_filter.png` | v0.8.2 换图源：icon-map A 级映射 `farm_module_l6`（水培模块），原同名 sprite 是碎片 |
| 韧棉织物 | `kotton_fabric.png` | 不能净水 |
| 水质试纸 | `water_test_strip.png` |  |
| 水质试剂盒 | `water_test_container.png` |  |
| 水质扫描仪 | `aquascan.png` | 显示杂质构成 |
| 密封水配给包(标准) | `water_ration.png` | 750ml 基础水 |
| 密封水配给包(小) | `water_ration_small.png` | 375ml |
| 排水口 | `drain.png` | 已换完整格栅图 |
| 水瓶(标准瓶) | `water_bottle_full.png` |  |
| 水瓶(大) | `large_water_bottle_full.png` | **合成图**：瓶身 `large.png` + 满水 `large_blue_100.png` |
| 水瓶(小) | `small_water_bottle_full.png` |  |
| 空啤酒瓶 | `empty_beer_bottle.png` | 酿造厂有回购业务 |
| premium 瓶 | `water_bottle_full_premium.png` | ※ 疑似「瓶装泉水」，对应关系待核对 |

拼图：`assets/items/sheets/cat_1.png`（20 项）

> 已移除（sprite 序列化纹理全空，确无可用图，原图为黑块/碎片）：水壶 `water_jug*`、
> 自动售水机 `fountain*`、自动售货机 `vending*` —— 见文末无图清单。


## 2. 机器与电力

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 熔炉 | `furnace.png` | 矿石纯度>废金属 |
| 3D打印机 | `printer_off.png` |  |
| 水瓶打印机 | `bottle_printer.png` |  |
| 催陈器(酒架) | `wine_rack.png` | 质量每125=+1天 |
| 冰箱 | `fridge.png` | 葡萄酒/未封水不受影响 |
| 能量电池 | `battery100.png` |  |
| 自充电电池 | `sbattery100.png` | 高级稀有 |
| 能量阵列 | `powerblock.png` | 相邻+2电/晚 可叠加 |
| 涡轮增压器(普通) | `turbo_booster.png` | 一次性 |
| 涡轮增压器(高级) | `turbo_booster_adv.png` | 不消耗 |
| 等离子切割机 | `welder_s.png` | 拾荒+10%废金属 |
| 剪线钳 | `wirecutter.png` | 拾荒+10%线缆 |
| 螺丝刀 | `screwdriver_s.png` | 拾荒+10%螺丝 |
| 幻影投影仪 | `mirage_generator.png` | 提升临街吸引力 |
| 警报系统 | `alarm_system.png` | 降低夜间盗窃 |
| 密码解序器 | `desequencer.png` | 写钥匙卡 |
| 搅拌机 | `blender.png` | 化学线 |
| 加热板 | `heating_plate.png` | 化学线 |
| 水培系统 | `hydroponic.png` |  |
| 机器区 | `machine_bay0.png` |  |
| 清洁机器人 | `vacuum_robot.png` | 自动收集粪便 |
| 牲畜饲料分配器 | `animal_feeder.png` |  |

拼图：`assets/items/sheets/cat_2.png`


## 3. 模组

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 模组(绿)※ | `module_green.png` | 颜色↔类型对应未确认 |
| 模组(黄) | `module_yellow.png` |  |
| 模组(红) | `module_red.png` |  |
| 空白模组 | `module_white.png` | 可机器重写 |
| 损坏模组 | `module_corrupt.png` | 可修或拆解 |
| 报废模组 | `module_ruined.png` |  |
| 模组提取器 | `module_extractor.png` | 有限次 |
| 模组提取器(高级) | `module_extractor_adv.png` | 无损耗 |
| 节点(小) | `node_s.png` | 转递相邻加成 |
| 节点(中) | `node_m.png` |  |
| 神经核心※ | `core.png` | 受限/无限制两版同图 |
| 水培模组(示例) | `farm_module1.png` | 共7种 |
| 熔炉模组(高炉/垃圾)※ | `module_black_4.png` | 对应未确认 |
| 打印机芯片 | `printer_chip1.png` | 共5种+手枪 |
| 助熔剂 | `flux_agent.png` | 禁用质量影响 |
| 助熔剂(高级) | `flux_agent_advanced.png` |  |

拼图：`assets/items/sheets/cat_3.png`


## 4. 刀·武器·工具

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 剥皮刀 | `skinning_knife.png` | 屠宰对口·屠够白送 |
| 切肉刀 | `kitchen_cleaver.png` | 可屠宰 |
| 厨刀 | `kitchen_knife.png` | 可屠宰 |
| 战斗匕首 | `combat_knife.png` | 可屠宰 |
| 战斗砍刀 | `combat_machete.png` | 可屠宰 |
| 美工刀 | `box_cutter.png` | 可屠宰 |
| 铅管 | `pipe.png` |  |
| 撬棍 | `crowbar.png` | v0.8.1 补：旧清单误判无图 |
| 短柄斧 | `hatchet.png` | 可移除水培作物 |
| 电击棍 | `stun_baton.png` |  |
| 消防斧 | `fireaxe.png` |  |
| 手电筒 | `flashlight3.png` | 拾荒降受伤 |
| 拾荒扫描仪 | `metal_scanner.png` | 只吃一台 |
| 改造体扫描仪 | `aug_scanner.png` | 100%准确·极耗电 |
| 基因扫描仪 | `genetic_scanner.png` | 看动物基因 |
| 植物分析仪 | `plant_analyser.png` |  |
| 哨兵3型(下机匣) | `glock_receiver.png` | 10mm |
| 左轮(长管) | `revolver_long.png` | .45 AFP |
| 自制手枪 | `handmade_pistol.png` |  |
| 重型自制手枪 | `heavy_handmade_pistol.png` | 10mm 穿甲 |
| 3D打印手枪 | `printed_gun.png` |  |
| 霰弹枪 | `shotgun.png` |  |
| 重型冲锋枪 | `heavy_smg.png` | 10mm |
| 电击枪 | `stun_gun.png` |  |
| 泰瑟枪 | `tazer.png` |  |
| 轻型手枪弹 | `light_pistol_ammo.png` | 有NL/AP变体 |
| 重型手枪弹 | `heavy_pistol_ammo.png` |  |
| 弹匣(STANAG-30) | `stanag_30.png` |  |

拼图：`assets/items/sheets/cat_4.png`


## 5. 鉴定·许可证

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 放大镜 | `magnifier.png` | 鉴定起手 |
| 成分光谱仪 | `chem_scanner.png` |  |
| 标志校验卡 | `republic_logo_checker.png` |  |
| 海明威色卡 | `cigarette_color_guide.png` |  |
| 鉴定指南※ | `guide0.png` | guide0-6 对应品类 |
| 标签打印机 | `labeler_blue.png` | 赝品改标签 |
| 档案箱 | `dossier.png` |  |
| 鉴定委员会初级证书 | `cert1.png` | 挂展示柜才刷客 |
| 1级武器许可证 | `permit_gun_1.png` | 声望<0吊销 |
| 2级武器许可证 | `permit_gun_2.png` | <30吊销 |
| 3级武器许可证 | `permit_gun_3.png` | <60吊销 |
| 治安部通缉名单 | `paper_wanted.png` |  |
| 事件回执单 | `sec_slip.png` |  |

拼图：`assets/items/sheets/cat_5.png`


## 6. 养鼠·酿酒

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 动物笼 | `animal_cage.png` | 废金属修·金属锭升级 |
| 捕鼠夹 | `mouse_trap.png` | 放合成奶酪 |
| 捕鼠夹(带诱饵) | `mouse_trap_cheese.png` |  |
| 老鼠(中/公) | `rat_m_m.png` | 夹子产物同ID |
| 老鼠(大/母) | `rat_l_f.png` |  |
| 血清(红) | `red_serum.png` | 催生长·降免疫 |
| 血清(绿) | `green_serum.png` | 提免疫 |
| 血清(蓝)※ | `blue_serum.png` | 第4色 待核对 |
| 血清(紫)※ | `purple_serum.png` | 第4色 待核对 |
| 酒瓶(带气塞) | `wine_bottle.png` |  |
| 发酵中 | `wine_fermenting.png` |  |
| 酵母 | `yeast.png` |  |
| 超级酵母 | `superyeast.png` | 1天出琼浆 |
| 合成酵母 | `illegal_yeast.png` | 走私酒·致癌 |
| 酵母生物反应器 | `yeast_gen.png` | 不消耗 |
| 荧光莓 | `bloomberry_p.png` |  |
| 荧光莓种子 | `bloomberry_seed.png` |  |
| 空气塞 | `fermentation_airlock.png` |  |

拼图：`assets/items/sheets/cat_6.png`


## 7. 食物·饮品

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 生肉(标准) | `raw_meat.png` | 400g+出大肉 |
| 生肉(小) | `small_raw_meat.png` | 50g/份 |
| 肉粒 | `morsel.png` |  |
| 肉碎 | `meat_scrap.png` |  |
| 动物脂肪 | `fat_meat.png` |  |
| 泥炭合成肉 | `processed_meat.png` |  |
| 速食拉面 | `cup_noodle.png` |  |
| 营养果 | `nutrifruit.png` | 无籽改造 |
| 填料草 | `fillerweed.png` | 填充增重 |
| 食用帽菇 | `meal_cap.png` |  |
| 梦帽菇 | `dream_cap.png` | 中和后可食 |
| 梦魇帽菇 | `nightmare_cap.png` | 剧毒 |
| 梦尘 | `dream_dust.png` |  |
| 梦魇尘 | `nightmare_dust.png` | 毒+致幻 |
| 合成奶酪 | `cheese.png` | 捕鼠夹诱饵 |
| 红魔鬼啤酒 | `red_beer.png` | 3.5% |
| 努特加 | `nudka.png` | 原为脱漆剂 |
| 贝氏冰淇淋 | `beis_icecream.png` | 冷冻升值 |
| 肋明治 | `ribwich.png` | 有鉴定指南 |
| 果汁袋 | `juice_pouch.png` |  |
| 汽水 | `items_food_soda_red.png` |  |
| 2L汽水 | `soda_2l.png` |  |
| 能量饮料 | `energy_drink.png` |  |
| 咖啡豆 | `coffee_bean.png` |  |
| 猫咪巧克力棒 | `cat_bar.png` |  |
| 轻食能量棒 | `li_eat_snackbar.png` |  |
| 一板零嚼 | `zerochew.png` | 食欲抑制剂 |
| 面粉 | `items_food_bag_of_flour.png` |  |

拼图：`assets/items/sheets/cat_7.png`


## 8. 医疗·药品

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 免疫宁注射器 | `injector_purple_large.png` | 每周必打·哨兵病 |
| 奥克西莫注射器 | `injector_pink.png` | 合法但成瘾 |
| 奥克莫吸注射器 | `injector_pink_alt.png` | 非成瘾替代 |
| 纳洛通注射器 | `injector_pure_white.png` | 过量急救 |
| 赛纳普斯注射器 | `injector_black.png` | 治成瘾 |
| 注射器(红)※ | `injector_red.png` | 对应药品待核对 |
| 注射器(蓝)※ | `injector_blue.png` | 对应药品待核对 |
| 注射器(绿)※ | `injector_green.png` | 对应药品待核对 |
| 咖啡因药片 | `cafeine_pill.png` |  |
| 避孕套 | `pack_condom.png` |  |
| 绷带(基础) | `bandage_small.png` |  |
| 绷带(外用药膏) | `topical_bandage_small.png` | 促愈合 |
| 绷带(止血) | `hemostatic_bandage_small.png` |  |
| 南丁格尔软膏 | `salve.png` | 抗菌再生 |
| 嗅盐 | `smelling_salt.png` |  |
| 血袋 | `blood_bag.png` |  |
| 蓝血 | `blue_blood_bag.png` | 上层区稀罕物 |
| 外科手术工具 | `surgery_toolkit.png` |  |
| 医疗物资箱 | `med_box.png` | 需识别卡 |
| 治安部物资箱 | `sec_box.png` |  |
| 工程物资箱 | `eng_box.png` |  |
| 服务物资箱 | `service_box.png` |  |
| 治安部物证柜 | `evidence_box.png` |  |
| 医疗包(大) | `medical_pouch.png` |  |
| 注射器袋 | `injector_pouch.png` |  |

拼图：`assets/items/sheets/cat_8.png`


## 9. 违禁品·钥匙卡

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 暗灯 | `black_lamp.png` | 向小偷发销赃信号 |
| 拾荒者信物 | `scav_medal.png` | 提升拾荒客光顾 |
| 钥匙卡(指挥) | `command_keycard.png` | 开大多数锁 |
| 钥匙卡(治安) | `sec_keycard.png` |  |
| 钥匙卡(医疗) | `med_card.png` |  |
| 钥匙卡(工程) | `eng_card.png` |  |
| 钥匙卡(研发) | `sci_card.png` |  |
| 钥匙卡(补给) | `sup_card.png` |  |
| 钥匙卡(服务) | `ser_card.png` |  |
| 空白钥匙卡 | `blank_card.png` | 需解序器写入 |
| 解序芯片(指挥) | `cmd_module.png` |  |
| 解序芯片(治安) | `sec_module.png` |  |
| 解序芯片(医疗) | `med_module.png` |  |
| 解序芯片(工程) | `eng_module.png` |  |
| 解序芯片(研发) | `sci_module.png` |  |
| 解序芯片(补给) | `sup_module.png` |  |
| 解序芯片(服务) | `ser_module.png` |  |
| 神经活性香水(同步) | `perfume1.png` | +15% |
| 费洛蒙香水(本源) | `perfume2.png` | +25% 违禁 |
| MBS神经毒气 | `canister_nerve.png` |  |
| 塑性炸药 | `c4.png` |  |
| 闪光弹 | `flashbang.png` |  |
| 烟雾弹 | `smoke_grenade_green.png` |  |
| 破片手雷 | `frag.png` |  |
| 放射性废料 | `nuclear_waste.png` |  |
| 彩票 | `lottery.png` | 周六开奖 |
| 刮刮乐 | `scratch.png` | 上层区禁止 |
| 一叠刮刮乐 | `scratch_stack.png` |  |
| 食品券 | `food_stamp.png` | 有防伪手册 |
| 治安部档案 | `intel_sec.png` |  |
| 采购凭单 | `exchange_directive.png` |  |
| 凭单 | `slip.png` |  |

拼图：`assets/items/sheets/cat_9.png`


## 10. 店务·藏匿·背包

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 霓虹灯牌(水) | `water_sign.png` | 引卖水客 |
| 霓虹灯牌(食品) | `food_sign.png` |  |
| 霓虹灯牌(日用品) | `household_sign.png` |  |
| 霓虹灯牌(材料) | `material_sign.png` |  |
| 霓虹灯牌(医疗) | `medical_sign.png` |  |
| 霓虹灯牌(奢侈品) | `berry_sign.png` |  |
| 霓虹灯牌(通用) | `items_sign_1.png` |  |
| 探险招募牌 | `hiring_sign.png` |  |
| 工具箱(新) | `toolbox_new.png` | 数字键1-9装备 |
| 工具箱(旧) | `toolbox_old.png` |  |
| 储藏区 | `storage_bay.png` |  |
| 储藏区(大) | `storage_bay_large.png` |  |
| 储藏区(化学师) | `storage_bay_chem.png` |  |
| 储藏区(枪械师) | `storage_bay_gun.png` |  |
| 走私暗格 | `smuggler_bay.png` | 盘查藏物 |
| 走私暗格(大) | `smuggler_bay_large.png` |  |
| 走私暗格(迷你) | `smuggler_bay_mini.png` |  |
| 垃圾桶 | `trashcan.png` | 夜间永久清除 |
| 背包(小) | `simple_backpack.png` |  |
| 背包(基础) | `simple_backpack_medium.png` |  |
| 背包(大) | `simple_backpack_large.png` |  |
| 军用背包(大) | `simple_backpack_large_military.png` |  |
| 军用背包(标准) | `simple_backpack_medium_military.png` |  |
| 挎包 | `satchel.png` |  |
| 腰包 | `fanny_pack.png` |  |
| 房契 | `deed.png` |  |
| 报纸 | `newspaper.png` |  |
| 便签 | `postit.png` |  |
| 手写便签 | `handnote.png` |  |
| 导师手册 | `tutorial_book.png` |  |
| 专业手册 | `manual1.png` |  |
| 保险柜 | `safe.png` |  |

拼图：`assets/items/sheets/cat_10.png`


## 11. 材料

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 金属矿石 | `ore1.png` | 纯度高于废金属 |
| 稀有金属矿石 | `ore2.png` |  |
| 废金属 | `scrap_metal.png` |  |
| 金属锭 | `metal_ingot.png` |  |
| 线缆 | `wire.png` |  |
| 螺母/螺丝 | `nuts_metal_pile.png` |  |
| 玻璃碎片 | `glass_shard.png` |  |
| 韧棉种子 | `kotton_plant_seed.png` |  |
| 韧棉植株 | `kotton_plant.png` |  |
| 韧棉纤维 | `kotton_fiber_p.png` |  |
| 电子元件 | `electronic1.png` | 共3档 |
| 化学用品 | `chemical1.png` | 共3档 |
| 填料草种子 | `fillerweed_seed.png` |  |
| 营养果种子 | `nutrifruit_seed.png` |  |
| 梦帽菇孢子 | `dream_cap_seed.png` |  |
| 水培芦苇种子 | `hydroreed_seed.png` |  |
| 水培营养片 | `nutrient_tablet.png` | 严禁食用 |
| 枪械零件 | `gun_part.png` |  |

拼图：`assets/items/sheets/cat_11.png`


## 12. 冷门·特殊

| 道具 | 图标文件 | 备注 |
|------|----------|------|
| 仿生机械手(钢) | `hand_steel.png` | 有鉴定指南 |
| 仿生机械手(碳) | `hand_carbon.png` |  |
| 仿生机械手(金) | `hand_gold.png` |  |
| 等离子燃料匣 | `plasma_fuel_cell.png` | 价值看质量 |
| 永恒焕活精华液 | `skincare_cream.png` | 上层区高价 |
| 洗涤剂 | `soap.png` |  |
| 厕纸 | `toilet_paper.png` |  |
| 牙膏 | `toothpaste.png` |  |
| 卫生棉条 | `box_tampon.png` |  |
| 海明威香烟(黑) | `cig_black.png` | 赝品重灾区 |
| 海明威香烟(红) | `cig_red.png` |  |
| 名片(酿酒厂) | `card_brewer.png` | 等于电话本 |
| 名片(化学家) | `card_chem.png` |  |
| 名片(采矿社) | `card_mining.png` |  |
| 名片(药商) | `card_pharma.png` |  |
| 名片(王尔德) | `card_wild.png` |  |
| 磁带播放器 | `cassette_player.png` |  |
| 音乐磁带 | `cassette1.png` | 共10首 |
| 垃圾 | `trash_pile.png` | 可转废金属 |
| 器官(心) | `organ_heart.png` | 器官贩子线 |
| 器官(肝) | `organ_liver.png` |  |
| 器官(肺) | `organ_lung_left.png` |  |
| 器官(肾) | `organ_kidney_left.png` |  |
| 器官运输箱 | `organ_transport_box.png` |  |
| 有机打印系统 | `bioprinter_system.png` |  |

拼图：`assets/items/sheets/cat_12.png`


---

## 图像管线备忘（维护用）

- 原始导出：`.tmp/sprites_res/`（1155）+ `.tmp/sprites_sa1/`（789），UnityPy Sprite 直出。
- **已知坑**：约 15% 的 sprite 序列化纹理里没有对应内容（运行期打包布局 > 序列化内容），
  需按 6 种坐标解释裁剪并取内容量最高者；`fix_blanks.py` / `substitute_blanks.py` 在 `.tmp/`。
- **映射关系以 [icon-map.txt](./icon-map.txt) 为准**（v0.8.1，由游戏代码字面量邻域反推，非人工猜）：
  `identifier → sprite → atlas`。conf **A** = 标识符即图名（147 条，可靠）；
  **B** = 代码邻域票 ≥2 且图名有权威图集（235 条，较可靠，抽检精度约 85%）；
  **C** = 弱证据（26 条，仅线索）。
  **图名与物品标识符只有约 36% 同名** —— 这就是此前"靠名字猜、对不上"的根因，别再按名字猜。
- **权威图集分类**（sprite → atlas，35 个 `Items/*` 512×512 图集，GameAssembly.dll 内 1500+ 处引用投票）：
  `items_tool(58) / items_mod(51) / items_misc(48) / items_medical(46) / items_module(32) /
  items_amenities(34) / items_hydroponic_plant(27) / items_ship(24) / itematlas(64) / items_container(19) /
  items_furniture(19) / items_food(19) / items_sec(16) / items_weapons_melee(14) / items_tool2(13) /
  items_material(13) / items_husbandry(12) / water_container3(11) / items_sign(11) / items_winemaking(11) …`
  校验规则：**某物品所用 sprite 的图集必须与该物品类别一致**，不一致即为错配 —— 这是纠"对不上"的硬约束。
- **真无图清单**（sprite 条目与图集区域都在，但**发行包里就是黑块**，是 demo 裁剪/未填充，不是"纹理缺失"）：
  `armor_lining / chemforge / hemostatic_agent / molotov_cocktail / nuts / spectral_analyser / stick_grenade /
  gl_item(玻璃刀) / recharger*(充能器) / steel_sheet_rough / water_jug_full / fireaxe / printer_off /
  fountain*(自动售水机) / vending*(自动售货机) / evaporator*(蒸发器, v0.8.2) / water_tablet(净水药片, v0.8.2)`。
  问到时直接说明，**禁止拿近似图冒充**。
  （**v0.8.1 修正**：撬棍 `crowbar` 其实有完好的图且已入库 —— 旧清单误判；老鼠 `rat_m_m` / `rat_l_f` 为有效图。）
- **叠加层坑**（2026-09-30 补，v0.7.0 漏网）：容器类图标分两层 —— 完整瓶/罐身（`large.png`、`pitcher.png`）
  与液体水位叠加（`large_blue_10~100`、`pitcher_red_*` 等，颜色 = 水色档、数字 = 水位%）。
  直出的 `<容器>_full` 常是只剩液体的碎片或全空 → **必须「瓶身 + 水位」PIL alpha_composite 合成**。
  统计指标（opaque/sd）抓不出这种碎片图，**入库前必须目检**。
- 游戏更新后重跑：`export_sprites.py` → `curate_items.py`（对照本文件增删行）→ `fix_blanks.py`。
- **反推映射的工具链**（都在 `.tmp/`，非交付物）：`re_scan3.py`（扫 GameAssembly.dll 的 il2cpp 段，
  RIP-相对字面量引用，13.5 万条）→ `sprite_atlas.py` / `loc_sprite.py`（代码顺序邻域投票）
  → `build_iconmap.py`（合成 icon-map.txt）。`re_probe.py` / `re_ptr.py` / `re_dis.py` 是排错用探针。
