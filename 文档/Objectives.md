# 🗡️ 目标<!-- {docsify-ignore-all} -->
玩家必须推进并达成目标才能完成任务。有一些目标来源于其它插件，你必须安装这些插件作为前置才能使用这部分目标。  
首先，我们会先介绍我们插件所自带的默认目标：  
# 默认目标
## ⛏️ 破坏方块|BreakBlocks

> **达成需求**：玩家破坏指定数量的方块。  
> **命令参数**：  
> + **```<材料名称>```** - 用于指定需要玩家破坏的方块。可以用“hand”来指定你当前手持的物品。可以用“any”将其设定为任何物品都可以计入数量。你还可以指定在NotQuests物品系统中制作的物品。  
> + **```<数量>```** - 用于指定需要玩家破坏的方块的数量。  
> + **```(flags)```** - 可选Flag
> + + **```--doNotDeductIfBlockIsPlaced```** - 默认情况下，如果你放置了破坏方块目标中指定的方块，进度将会被相应地扣除。否则，玩家可以通过放置后再破坏的方式刷进度。若设置了此Flag，将会禁用该安全机制。  
> **示例**：```/qa edit 任务名称 objectives add BreakBlocks grass_block 4```（设定某个任务的目标为破坏4个草方块）  
<br/>  

## ❣️ 繁殖|BreedMobs

> **达成需求**：玩家繁衍出指定生物。  
> **命令参与**：  
> + **```<实体名称>```** - 用于指定需要玩家繁殖的生物类型。可以用“any”将其设定为任何生物都可以计入数量。  
> + **```<数量>```** - 用于指定需要玩家繁殖出的生物数量。  
> **示例**：```/qa edit 任务名称 objectives add BreedMobs cow 4```（设定某个任务的目标为繁衍4只牛）  
<br/>

## ❓ 条件|Condition
  
> **达成需求**：玩家需要满足特定条件（需要先使用```/qa conditions```创建出条件）。插件每秒都会检测玩家是否满足特定条件，或是检测玩家是否执行了该条件所指定的事件（例如：在条件中指定了某个金钱事件）。毫无疑问这是在以另一种方式增加目标。例如，你甚至可以使用PlaceholderAPI来创建目标。  
> **命令参数**：  
> + **```<条件名称>```** - 用于指定玩家需要达成的条件名称。这里输入的是需要让插件来检测的条件名称，条件需要用```/qa conditions```命令事先创建。  
> + **```(flags)```** - 可选Flag
> + + **```--checkOnlyWhenCorrespondingVariableValueChanged```** - 若设置了此Flag，插件就只会在玩家执行条件所指定的事件时才会进行检测。插件将会停止定时检测功能。正因如此，这样做的话会更加高效一些。  
> **示例**：```/qa edit 任务名称 objectives add Condition myCondition```（设定某个任务的目标为达成名叫“myCondition”的条件）  
<br/>

## 🥗 消耗物品|ConsumeItems

> **达成需求**：玩家需要消耗指定物品。通常来说，吃喝某物才算作是消耗物品 - 就比如说吃苹果，就是消耗了苹果。  
> **命令参数**：  
> + **```<材料名称>```** - 用于指定玩家需要消耗的物品名称。可以用“hand”来指定你当前手持的物品。你还可以指定在NotQuests物品系统中制作的物品。  
> + **```<数量>```** - 用于指定玩家需要消耗的物品数量。  
> **示例**：```/qa edit 任务名称 objectives add ConsumeItems apple 5```（设定某个任务的目标为消耗5个苹果）  
<br/>

## ⚒️ 合成物品|CraftItems

> **达成需求**：玩家需要合成指定物品。    
> **命令参数**：  
> **```<材料名称>```** - 用于指定玩家需要合成的物品名称。可以用“hand”来指定你当前手持的物品。你还可以指定在NotQuests物品系统中制作的物品。  
> + **```<数量>```** - 用于指定玩家需要合成的物品数量。  
> **示例**：```/qa edit 任务名称 objectives add CraftItems enchanting_table 1```（设定某个任务的目标为合成1个工作台）
<br/>

## 🚚 交付物品|DeliverItems

> **达成需求**：玩家需要交付指定物品给NPC（Citizen NPC和盔甲架都可以）。交付的意思是从玩家物品栏那里移除一定数量的指定物品。  
> **命令参数**：  
> + **```<材料名称>```** - 用于指定玩家需要交付的物品名称。可以用“hand”来指定你当前手持的物品。你还可以指定在NotQuests物品系统中制作的物品。  
> + **```<数量>```** - 用于指定玩家需要交付的物品数量。  
> + **```<NPC ID 或者 Armorstand>```** - 要么输入Citizen的NPC ID，要么输入Armorstand获取一个盔甲架，直接放置盔甲架即可将该目标的交付对象指定为此盔甲架。  
> **示例**：```/qa edit 任务名称 objectives add DeliverItems coal 20 armorstand```（设定某个任务的目标为交付20个煤炭给指定盔甲架）
<br/>

## 🪄 附魔|Enchant
  
> **达成需求**：玩家需要进行附魔。  
> **命令参数**：  
> + **```<魔咒名称>```** - 用于指定玩家需要附魔出的魔咒。  
> + **```<材料名称>```** - 用于指定玩家需要附魔的物品名称。可以用“any”将其设定为任何物品都可以计入数量。  
> + **```<数量>```** - 用于指定玩家需要附魔的物品数量。  
> + **```(flags)```** - 可选Flag  
> + + **```--min <最小等级>```** - 用于指定附魔的最小等级。
> + + **```--max <最大等级>```** - 用于指定附魔的最大等级。
> **示例**：```/qa edit 任务名称 objectives add Enchant minecraft:efficiency diamond_pickaxe 3.0 --min 2.0```（设定某个任务的目标为给钻石镐附魔出不低于2级的效率魔咒3次）  
<br/>

## 🐟 垂钓|FishItems

> **达成需求**：玩家需要钓上指定物品。  
> **命令参数**：  
> + **```<材料名称>```** - 用于指定玩家需要钓上的物品。可以用“hand”来指定你当前手持的物品。可以用“any”将其设定为任何物品都可以计入数量。你还可以指定在NotQuests物品系统中制作的物品。  
> + **```<数量>```** - 用于指定玩家需要钓上的物品数量。  
> **示例**：```/qa edit 任务名称 objectives add FishItems cod 3```（设定某个任务的目标为钓上3条鳕鱼）
<br/>

## 👉 交互|Interact

> **达成需求**：玩家需要按下鼠标左键或右键，或者二者一起按，以此与指定位置进行交互。  
> **命令参数**：  
> + **```<数量>```** - 用于指定玩家需要交互的次数。  
> + **```<世界名称>```** - 玩家需要进行交互的指定位置所在的世界名称。  
> + **```<x>```** - 玩家需要进行交互的指定位置的x轴坐标。  
> + **```<y>```** - 玩家需要进行交互的指定位置的y轴坐标。  
> + **```<z>```** - 玩家需要进行交互的指定位置的z轴坐标。  
> + **```(flags)```** - 可选Flag  
> + + **```--leftClick```** - 若设置了此Flag，玩家需要与指定位置进行交互的交互操作将会被设定为鼠标左击。  
> + + **```--rightClick```** - 若设置了此Flag，玩家需要与指定位置进行交互的交互操作将会被设定为鼠标右击。
> + + **```--cancelInteractions```** - 若设置了此Flag，玩家与指定位置交互时产生的交互事件将不会被执行。例如，如果位置指定的是一个箱子，玩家需要右击箱子，在未设置此Flag的情况下，箱子会被打开，目标也会达成，但如果设置了此Flag，那么“打开箱子”这一交互事件将不会被执行，箱子不会被打开，目标也会达成。  
> + + **```--taskDescription <目标描述>```** - 若设置了此Flag，输入描述后，玩家就可以在目标位置看到你所输入的描述了，以便玩家了解该目标具体要做什么。  
> + + **```--maxDistance <半径（单位：格）>```** - 若你想指定的交互位置不是一个点，而是一个范围区域，那么可以设置此Flag，输入半径后，需要进行交互的位置就会限定在指定位置的某个半径范围内。  
> **示例**：```/qa edit 任务名称 objectives add Interact 2 world 1453 71 -2451 --rightClick --maxDistance 2 --cancelInteraction --taskDescription "Find Trents fishing rod"```（设定某个任务的目标为需要在名叫world的世界里，鼠标右击以x1453,y71,z-2451为中心周围2格半径范围内的方块2次，右击时像开箱子这样的交互事件会被取消，目标描述是“Find Trents fishing rod”）  
<br/>

## 🤸 跳跃|Jump

> **达成需求**：玩家需要进行指定次数的跳跃。  
> **命令参数**：  
> + **```<数量>```** - 用于指定玩家需要跳跃的次数。  
> **示例**：```/qa edit 任务名称 objectives add Jump 10```（设定某个任务的目标为跳跃10次）
<br/>

## 🩸 击杀生物|KillMobs

> **达成需求**：玩家需要击杀指定生物。  
> **命令参数**：  
> + **```<实体名称>```** - 用于指定需要玩家击杀的生物类型。可以用“any”将其设定为任何生物都可以计入数量。可以用“player”指定生物类型为玩家。如果你安装了MythicMobs或是EcoBosses插件，你也可以使用这些插件（英文原文写的是是mod，应该是口误？）创造出的生物，你甚至还可以直接用```mmfaction:你的阵营名称```指定MythicMobs的某个阵营。  
> + **```<数量>```** - 用于指定玩家需要击杀生物的次数。  
> + **```(flags)```** - 可选Flag  
> + + **```--nametag_containsany <字符串>```** - 若设置了此Flag，插件将会检测生物名称是否**包含**该字符串。  
> + + **```--nametag_equals <字符串>```** - 若设置了此Flag，插件将会检测生物名称是否**吻合**该字符串。
> + + ProjectKorra联动：  
> + + + **```--withProjectKorraAbility <技能>```** - 若设置了此Flag，玩家需要使用ProjectKorra的技能击杀才能计入进度。  
> **示例**：```/qa edit 任务名称 objectives add KillMobs zombie 10```（设定某个任务的目标为击杀10只僵尸）  
<br/>

## 🔢 数字变量|NumberVariable

> **达成需求**：玩家需要满足变量中的要求。这样做可以相对地在目标中使用变量。  
> **命令参数**：  
> + <待补充>
> **示例**：```/qa edit 任务名称 objectives add NumberVariable PlaytimeMinutes moreOrEqualThan PlaytimeMinutes+2```（设定某个任务的目标为需要再游玩2分钟）  
<br/>

## 🔢 目标|Objective

> **达成需求**：玩家需要完成下属子目标，所有目标完成后，该目标才会被标记为完成。这是一个子目标的容器，也就是父目标。  
> **命令参数**：  
> + **```<目标显示名称>```** - 用于指定该目标的显示名称。  
> **示例**：```/qa edit 任务名称 objectives add Objective "Crafting Objectives"```（设定某个任务为父目标，显示名称为“Crafting Objectives”）  
<br/>

## 🏴‍☠️ 打开埋藏的宝藏|OpenBuriedTreasure

> **达成需求**：玩家需要打开指定数量的埋藏的宝藏（埋藏的宝藏是Minecraft原版特性）。  
> **命令参数**：  
> + **```<数量>```** - 用于指定玩家需要打开埋藏的宝藏的个数。  
> **示例**：```/qa edit 任务名称 objectives add OpenBuriedTreasure 3```（设定某个任务的目标为打开3个埋藏的宝藏）
<br/>  

## 📕 其它任务|OtherQuest

> **达成需求**：玩家需要完成其它任务。  
> **命令参数**：  
> + **```<其它任务名称>```** - 用于指定玩家需要完成的其它任务的名称。  
> + **```<数量>```** - 用于指定玩家需要完成的其它任务的次数。  
> + **```(flags)```** - 可选Flag 
> + + **```--countPreviouslyCompletedQuests```** - 若设置了此Flag，玩家在解锁该目标前完成的所有指定任务的次数都将计入在内。否则，只有在解锁后完成的指定任务才会被计算在内。  
> **示例**：```/qa edit 任务名称 objectives add OtherQuest 其它任务名称 2 --countPreviouslyCompletedQuests```（设定某个任务的目标为完成名叫“其它任务名称”的任务2次，该目标解锁前的完成次数也会被计入。）  
<br/>

## 🚮 拾取物品|PickupItems

> **达成需求**：玩家需要从地上拾取指定物品到物品栏里。  
> **命令参数**：  
> + **```<材料名称>```** - 用于指定需要玩家拾取的物品。可以用“hand”来指定你当前手持的物品。可以用“any”将其设定为任何物品都可以计入数量。你还可以指定在NotQuests物品系统中制作的物品。  
> + **```<数量>```** - 用于指定玩家需要拾取的物品数量。  
> + **```(flags)```** - 可选Flag 
> + + **```--doNotDeductIfItemIsDropped```** - 默认情况下，如果你丢弃了拾取物品目标中指定的物品，进度将会被相应地扣除。否则，玩家可以通过丢弃后再拾取的方式刷进度。若设置了此Flag，将会禁用该安全机制。  
> + + **```--doNotDeductIfItemIsPlaced```** - 默认情况下，如果你放置了拾取物品目标中指定的物品，进度将会被相应地扣除。否则，玩家可以通过放置后再破坏并拾取的方式刷进度。若设置了此Flag，将会禁用该安全机制。 
> + + **```--doNotDeductIfItemIsRemovedFromInventory```** - 默认情况下，如果你从物品栏里移除拾取物品目标中指定的物品（比如：放入箱子），进度将会被相应地扣除。否则，玩家可以通过将物品放入箱子后再破坏并拾取的方式刷进度。若设置了此Flag，将会禁用该安全机制。 
> **示例**：```/qa edit 任务名称 objectives add PickupItems dirt 12```（设定某个任务的目标为拾取12个泥土）
<br/>

## 🪧 放置方块|PlaceBlocks

> **达成需求**：玩家需要放置指定方块。  
> **命令参数**：  
> + **```<材料名称>```** - 用于指定需要玩家放置的方块。可以用“hand”来指定你当前手持的物品。可以用“any”将其设定为任何物品都可以计入数量。你还可以指定在NotQuests物品系统中制作的物品。  
> + **```<数量>```** - 用于指定玩家需要放置的方块数量。  
> + **```(flags)```** - 可选Flag 
> + + **```--doNotDeductIfBlockIsBroken```** - 默认情况下，如果你破坏了放置方块目标中指定的方块，进度将会被相应地扣除。否则，玩家可以通过破坏后再放置的方式刷进度。若设置了此Flag，将会禁用该安全机制。  
> **示例**：```/qa edit 任务名称 objectives add PlaceBlocks acacia_planks 20```（设定某个任务的目标为放置20个金合欢木板）  
<br/>

## 🛬 抵达位置|ReachLocation

> **达成需求**：玩家需要抵达指定位置。  
> **命令参数**：  
> + **```<选择器类型>```** - 目前，只有*worldeditselection*一种选择器类型。你需要用WorldEdit中的选择器选择一个区域设定为玩家需要抵达的位置。正因如此，要创建此目标，你需要安装一个WorldEdit。请在运行此命令前，先创建一个WorldEdit选择器（使用```//wand```或者```//pos1```和```//pos2```命令）。  
> + **```<位置名称>```** - 用于指定玩家需要抵达的位置的名称。这个名称将会显示在目标描述中。  
> **示例**：```/qa edit 任务名称 objectives add ReachLocation worldeditselection Luthers Church```（设定某个任务的目标为地抵达一个名叫Lythers Church的位置，需要使用worldeditselection选择器事先选择出该区域）  
<br/>

## 🧑‍💻 运行命令|RunCommand

> **达成需求**：玩家需要运行指定命令。  
> **命令参数**：  
> + **```<数量>```** - 用于指定玩家需要运行命令的次数。
> + **```<命令>```** - 用于指定玩家需要运行的命令，如果需要运行的命令中包含着空格，请将该命令放在引号（""）中。指定的命令无需在开头加斜杠（/）
> + **```(flags)```** - 可选Flag  
> + + **```--ignoreCase```** - 若设置了此Flag，将会无视指定的命令的大小写。也就是说，运行的命令无论是/warp spawn还是/wArP sPaWn都可以。  
> + + **```--cancelCommand```** - 若设置了此Flag，当目标处于解锁状态时，运行命令的事件不会执行，而是会被取消。所以说，如果玩家运行指定的命令，除了增加该目标的进度以外，什么都不会发生。  
> **示例**：```/qa edit 任务名称 objectives add RunCommand 2 "warp spawn" --ignoreCase```（设定某个任务的目标为运行/warp spawn命令2次，无视大小写）
<br/>

## 🧑‍💻剪羊毛|ShearSheep

> **达成需求**：玩家需要剪指定数量的羊毛。  
> **命令参数**：  
> + **```<数量>```** - 用于指定玩家需要剪的的羊毛数量。  
> + **```(flags)```** - 可选Flag  
> + + **```--cancelShearing```** - 若设置了此Flag，当目标处于解锁状态时，剪羊毛的事件不会执行，而是会被取消。所以说，如果玩家拿剪刀右击羊，除了增加该目标的进度以外，什么都不会发生。  
> **示例**：```: /qa edit 任务名称 objectives add ShearSheep 4 --cancelShearing```（设定某个任务的目标为剪4次羊毛，取消剪羊毛事件）
<br/>

## 🔥 烧炼物品|SmeltItems

> **达成需求**：玩家需要从熔炉中取出特定数量的烧炼好的物品。没错，玩家必须将物品烧炼后，再将其去除，该目标计入的是输出的物品数量，而不是放入熔炉的物品数量。  
> **命令参数**：  
> + **```<材料名称>```**：用于指定需要玩家通过烧炼获得的物品名称。可以用“hand”来指定你当前手持的物品。可以用“any”将其设定为任何物品都可以计入数量。你还可以指定在NotQuests物品系统中制作的物品。 
> + **```<数量>```** - 用于指定玩家需要烧炼出的物品数量。  
> **示例**：```/qa edit 任务名称 objectives add SmeltItems coal 4```（设定某个任务的目标为通过烧炼得到4个煤炭）
<br/>

## 🧟 潜行|Sneak

> **达成需求**：玩家需要进行潜行。  
> **命令参数**：  
> + **```<数量>```** - 用于指定玩家需要进行潜行的次数。  
> **示例**：```/qa edit 任务名称 objectives add Sneak 4```（设定某个任务的目标为潜行4次）  
<br/>

## 🗯️ 与NPC对话|TalkToNPC

> **达成需求**：玩家需要与NPC（Citizen NPC或者盔甲架）进行对话（右击）。  
> **命令参数**：  
> + **```<NPC ID 或者 Armorstand>```** - 要么输入Citizen的NPC ID，要么输入Armorstand获取一个盔甲架，直接放置盔甲架即可将该目标的对话对象指定为此盔甲架。  
> **示例**：```/qa edit 任务名称 objectives add TalkToNPC armorstand```（设定某个任务的目标为与指定盔甲架对话）
<br/>

## ❗ 触发器命令|TriggerCommand

> **达成需求**：需要有足够权限的人（可以是命令方块或是有OP权限的玩家。通常由控制台运行）才能运行的特殊命令。  
> 这可以使得NotQuests能够与许多不同的插件进行联动。  
> ### 使用案例
> 设定一个“*为我们投票*”的目标，一旦玩家进行投票后，目标即达成。至于投票插件，你得在奖励部分添加一个触发器命令。  
> 然后，一旦插件检测投票插件奖励部分的触发器命令被从控制台运行了（即玩家投票后），该玩家的触发器命令目标就会达成。  
>> 如果你想用上像“Interactions”这样的插件制作出特别的任务，这项功能非常有用，如果你想制作一个更细节、能与NPC开展脚本化对话的话可以用用那个插件。不过请注意：那个插件的上手门槛很高。同时，请注意：较新版本的NotQuests插件已经拥有了完整的对话系统。  
> #### 示例：如何给任务名称为“1”的示例任务添加触发器命令  
> ![o1.png](https://s2.loli.net/2023/10/21/Le2UXAQqgbHKcFW.png)  
> 该示例的对应触发器命令应该是```/qa triggerObjective playervoted NoeX``` - 此处NeoX是我的游戏ID。  
> 在我们的投票示例中，如果你将该命令在你的投票插件中设定为投票奖励，玩家一旦进行投票，目标就会达成。  
> ![o2.png](https://s2.loli.net/2023/10/21/bFdlPosrXiGWDje.png)  
> **命令参数**：  
> + **```<触发器名称>```** - 用于指定触发器的名称。这里触发器名称需要应用到触发器命令中（```/qa triggerObjective <触发器名称>```）。  
> + **```<数量>```** - 用于指定完成目标所需的触发器/命令被触发/运行的次数。  
> **示例**：```/qa edit 任务名称 objectives add TriggerCommand trigger1 1```（设定某个任务的目标为执行名为“trigger1”的触发器命令1次）  
> **触发“触发器”/达成目标的命令**：```/qa triggerObjective trigger1 {玩家ID}```玩家ID需要替换为玩家游戏ID。  
<br/>

# [Citizens](https://ci.citizensnpcs.co/job/Citizens2/)联动目标  
## ℹ️ KillEliteMobs
# [Jobs Reborn](https://www.zrips.net/jobs/)联动目标
## ℹ️ JobsRebornReachJobLevel
# [Project Korra](https://github.com/ProjectKorra/ProjectKorra/releases)联动目标
## ℹ️ ProjectKorraUseAbility
# [Slimefun](https://github.com/Slimefun/Slimefun4/releases)联动目标
## ℹ️ SlimefunResearch
# [Towny](https://github.com/TownyAdvanced/Towny/releases)联动目标
## ℹ️ TownyNationReachTownCount
## ℹ️ TownyReachResidentCount
# [BetonQuest](https://docs.betonquest.org/2.0-DEV/Downloads/)联动目标
## ℹ️ BetonQuestObjectiveStateChange
# [UltimateJobs](https://github.com/Warsteiner37/UltimateJobs/releases)联动目标
## ℹ️ UltimateJobsReachJobLevel