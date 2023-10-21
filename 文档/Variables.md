# ⭐ 变量<!-- {docsify-ignore-all} -->
变量还可以用于快速创建高级事件和条件！正因如此，下面的很多变量都可以运用于条件当中，并且大多数情况也可以运用于事件当中。不仅如此，变量还可以在一些所谓的表达式中运用。因此，你甚至可以对这样变量进行计算！  
# 默认变量
## ❓ ActiveQuests

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表  
> **条件示例**：  
> + ```/qa conditions add isWoodCutterQuestActive ActiveQuests contains woodCutter```（设定条件isWoodCutterQuestActive为名叫“woodCutter”的任务处于激活状态）
> + ```/qa conditions add isOnlyWoodCutterQuestActive ActiveQuests equals woodCutter```（设定条件isOnlyWoodCutterQuestActive为名叫“woodCutter”的任务处于激活状态，且除此之外没有其它任务）
> + ```/qa conditions add hasAllWoodQuestsActive ActiveQuests contains woodCutter,saveTheWoods```（设定条件hasAllWoodQuestsActive为名叫“woodCutter”和“saveTheWoods”的任务同时处于激活状态）
> **事件示例**：
> + ```/qa actions add giveQuestWoodCutter ActiveQuests add woodCutter```（设定事件giveQuestWoodCutter为强制给予玩家名叫“woodCutter”的任务）
> + ```/qa actions add setQuestWoodCutter ActiveQuests set woodCutter```（设定事件setQuestWoodCutter为强制给予玩家名叫“woodCutter”的任务，同时放弃玩家其它所有任务）
> + ```/qa actions add giveForestQuests ActiveQuests add woodCutter,saveTheWoods```（设定事件giveForestQuests为强制给予玩家名叫“woodCutter”和“saveTheWoods”的任务）
<br/>

## ❓ Advancement

> **条件：✅ 事件：✅**  
> **类型**：布尔值
<br/>

## ❓ Block

> **条件：✅ 事件：✅**  
> **类型**：字符串
<br/>

## ❓ Chance

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ Climbing

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ CompletedObjectiveIDsOfQuest

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ CompletedQuests

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ Condition

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ ContainerInventory

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ CurrentBiome

> **条件：✅ 事件：❌**  
> **类型**：字符串
<br/>

## ❓ ContainerInventory

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ CurrentPositionX

> **条件：✅ 事件：✅**  
> **类型**：双精度浮点数
<br/>

## ❓ CurrentPositionY

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ CurrentPositionZ

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ CurrentWorld

> **条件：✅ 事件：✅**  
> **类型**：字符串
<br/>

## ❓ DayOfWeek

> **条件：✅ 事件：❌**  
> **类型**：字符串
<br/>

## ❓ EnderChest

> **条件：✅ 事件：✅**  
> **类型**：ItemStack、列表
<br/>

## ❓ Experience

> **条件：✅ 事件：✅**  
> **类型**：整数
<br/>

## ❓ ExperienceLevel

> **条件：✅ 事件：✅**  
> **类型**：整数
<br/>

## ❓ False

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ Flying

> **条件：✅ 事件：✅**  
> **类型**：单精度浮点数
<br/>

## ❓ FlySpeed

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ GameMode

> **条件：✅ 事件：✅**  
> **类型**：字符串
<br/>

## ❓ Glowing

> **条件：✅ 事件：✅**  
> **类型**：布尔值
<br/>

## ❓ Health

> **条件：✅ 事件：✅**  
> **类型**：双精度浮点数
<br/>

## ❓ InLava

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ InWater

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ Inventory

> **条件：✅ 事件：✅**  
> **类型**：ItemStack、列表
<br/>

## ❓ ItemInInventoryEnchantments

> **条件：✅ 事件：❌**  
> **类型**：字符串、列表
<br/>

## ❓ MaxHealth

> **条件：✅ 事件：✅**  
> **类型**：双精度浮点数
<br/>

## ❓ Money

> **条件：✅ 事件：✅**  
> **类型**：双精度浮点数
<br/>

## ❓ Name

> **条件：✅ 事件：✅**  
> **类型**：字符串
<br/>

## ❓ Op

> **条件：✅ 事件：✅**  
> **类型**：布尔值
<br/>

## ❓ Permission

> **条件：✅ 事件：✅**（需要LuckPerms前置）  
> **类型**：布尔值
<br/>

## ❓ Ping

> **条件：✅ 事件：❌**  
> **类型**：整数
<br/>

## ❓ PlaytimeTicks

> **条件：✅ 事件：✅**  
> **类型**：整数
<br/>

## ❓ PlaytimeMinutes

> **条件：✅ 事件：✅**  
> **类型**：双精度浮点数
<br/>

## ❓ PlaytimeHours

> **条件：✅ 事件：✅**  
> **类型**：双精度浮点数
<br/>

## ❓ QuestAbleToAccept

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ QuestOnCooldown

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ QuestPoints

> **条件：✅ 事件：✅**  
> **类型**：长整型数
<br/>

## ❓ QuestReachedMaxAccepts

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ QuestReachedMaxCompletions

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ QuestReachedMaxFails

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ RandomNumberBetweenRange

> **条件：✅ 事件：❌**  
> **类型**：整数
<br/>

## ❓ ReflectionStaticBoolean

> **条件：✅ 事件：✅**  
> **类型**：布尔值
<br/>

## ❓ ReflectionStaticDouble

> **条件：✅ 事件：✅**  
> **类型**：双精度浮点数
<br/>

## ❓ ReflectionStaticFloat

> **条件：✅ 事件：✅**  
> **类型**：单精度浮点数
<br/>

## ❓ ReflectionStaticInteger

> **条件：✅ 事件：✅**  
> **类型**：整数
<br/>

## ❓ ReflectionStaticString

> **条件：✅ 事件：✅**  
> **类型**：字符串
<br/>

## ❓ Sleeping

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ Sneaking

> **条件：✅ 事件：✅**  
> **类型**：布尔值
<br/>

## ❓ Sprinting

> **条件：✅ 事件：✅**  
> **类型**：布尔值
<br/>

## ❓ Swimming

> **条件：✅ 事件：✅**  
> **类型**：布尔值
<br/>

## ❓ True

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ WalkSpeed

> **条件：✅ 事件：✅**  
> **类型**：单精度浮点数
<br/>

# [BetonQuest](https://dev.betonquest.org/)联动变量
## ❓ BetonQuestCondition

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

# [PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI/releases)联动变量
## ❓ PlaceholderAPINumber

> **条件：✅ 事件：❌**  
> **类型**：双精度浮点数
<br/>

## ❓ PlaceholderAPIString

> **条件：✅ 事件：❌**  
> **类型**：字符串
<br/>

# [Project Korra](https://github.com/ProjectKorra/ProjectKorra/releases)联动变量
## ❓ ProjectKorraElements

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

## ❓ ProjectKorraIsBender

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>

## ❓ ProjectKorraSubElements

> **条件：✅ 事件：✅**  
> **类型**：字符串、列表
<br/>

# [Towny](https://github.com/TownyAdvanced/Towny/releases)联动变量
## ❓ TownyNationName

> **条件：✅ 事件：✅**  
> **类型**：字符串
<br/>

## ❓ TownyNationTownCount

> **条件：✅ 事件：❌**  
> **类型**：整数
<br/>

## ❓ TownyTownPlotCount

> **条件：✅ 事件：❌**  
> **类型**：整数
<br/>

## ❓ TownyTownResidentCountVariable

> **条件：✅ 事件：❌**  
> **类型**：整数
<br/>

# [UltimateClans](https://polymart.org/resource/ultimate-clans-v5.1162)联动变量
## ❓ UltimateClansClanLevel

> **条件：✅ 事件：✅**  
> **类型**：整数
<br/>

# [Floodgate](https://github.com/GeyserMC/Floodgate)联动变量
## ❓ FloodgateIsFloodgatePlayer

> **条件：✅ 事件：❌**  
> **类型**：布尔值
<br/>
