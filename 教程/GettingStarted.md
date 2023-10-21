# 👋入门指南<!-- {docsify-ignore-all} -->

?> 本教程是根据插件5.17.1及以上版本、Paper核心1.20.1版本进行撰写的。   
如果你运行的是旧版本或Spigot服务器，可能会遇到功能缺失、命令与教程不符的情况。本教程不提供相应的指导，请自行研究。   

<br/>

?> 我知道这个文档并不完善，其内容仅为NotQuests实际功能的10%。这不怪我，这份文档可是开源的，所以要怪就怪你自己，或者说你们这个玩家社区，怪懒的！**可耻！**    
要是你对NotQuests有了更多的了解，你就可以在这里[参与文档的撰写](https://github.com/AlessioGr/NotQuests-Docs/tree/main/docs)，成为贡献者。（需要Github账号，文档可以直接在这里进行编辑） - 欢迎你的参与！  

  

让我们赶紧来探索NotQuests这个插件吧！有两种入门方式供君选择：  
+ 要么读完这篇教程  
+ 要么看我们的[视频](https://www.youtube.com/watch?v=OC45_H3Tv8Y)（油管链接，别急，我还没做）。注意，这个视频教程里的NotQuests是v3版本，有些命令可能不一样。  

# 任务结构
在NotQuests里，一项任务是由多个不同的内容构成的。例如：
+ **displayName**（显示名称）：玩家所能看见的任务名称。
+ **description**（描述）：任务描述。
+ **limits**（限制）：该任务玩家能接取、完成或失败的最大次数。
+ 等等……  
除此之外，你还可以将下面这些附加进任务中：
+ **Objectives**（目标）：设定一些“玩家需要去做的事情”作为目标。一旦这些事情全部做完，任务就会完成。
+ **Requirements**（前置）：判定玩家是否可以接取任务。如果玩家未满足任务所需的前置条件，就无法接取该任务。
+ **Rewards**（奖励）：奖励一词应该不难理解吧！奖励是在玩家完成任务后会对玩家“执行”的一系列操作。
+ **Triggers**（触发器）：这项属性叫做触发器，理解起来可能有点困难。说白了，就是在某些事情发生时“执行”一个事件。

# 命令
插件一共有2种类型的命令：  
+ ```/q```或```/notquests```：这个类型的命令是**玩家命令**。所有玩家都可以使用该命令。
+ ```/qa```或```/notquestsadmin```：这个类型的命令是**管理员命令**。我们需要用这个类型的命令来创建和编辑任务。  
在NotQuests中，无论创建什么任务，只需在游戏中执行各种命令即可完成，而不需要去查改配置文件。

## 完善命令
在你输入命令后，需要用空格进行分割，而分割后输入的这部分内容我们称之为*参数*。用下图作为举例，*edit*和*questname*即为参数，这条命令中，共有2个参数：  
![完善命令（只是个图片示例，不用翻译吧）](/pic/getting-started/command-completions.png)  
如果你在最后一个参数后再按一下空格键，我们的智能命令系统会自动为你显示“后续”可用（可补全）的参数。如果你输入的命令无法执行，不妨试试在后面加一个空格，看看后面是否还有需要填写的参数，然后，再看一遍**完善命令**这部分内容！  

!> 如果无法自动填充参数，后面没有显示后续可用参数，只需**按下回车**执行现有的命令就好！之后你就会看到一个**帮助菜单**。这个菜单会为你提供帮助，它会告诉你可用参数及其用途。
<br/>

# 创建我们的第一个任务
想要学会一件事，我觉得最好最简单的方式就是：边学边做！所以，别在这无聊的文档上浪费时间了，我们来创建我们的第一个任务吧：  
```/qa create TheVirus```  
执行该命令后会出现下面一则消息：  
<div align=center><img src="/pic/getting-started/quest-successfully-created.png" alt="任务TheVirus已成功创建！"> 
</div>

## 1.任务描述&显示名称
现在，我们成功创建了一个名叫TheVirus的任务，TheVirus即是这个任务的**任务名称**，任务名称中不能有任何空格，它只是作为一个任务的**识别符**。不过，我们可用给它设定一个**显示名称**，显示名称顾名思义，就是玩家实际在游戏中能够看到的名称，这个名称中可用使用空格。在这里，我们为我们的任务设定一个显示名称*A Deadly Virus*（一个死亡病毒）。  
```/qa edit TheVirus displayName set A Deadly Virus```  
接下来，我们想要为该任务添加一个描述，这个描述会在很多地方显示出来，例如，玩家正打算尝试预览任务或是接受任务时显示。在这里，我们为我们的任务添加一个描述：*一个死亡病毒感染了临冬城的居民。你必须物理净化掉这些被感染的村民，从而阻止病毒的继续传播。*  
```/qa edit TheVirus description set A deadly virus has infected the people of Winterfell. You have to murder the infected villagers to prevent the virus from spreading further.```  
至此，你的玩家接取任务后就会看到这样一个漂亮的描述和显示名称：  
<div align=center><img src="/pic/getting-started/after-accepting-with-description.png" alt="任务描述：一个死亡病毒感染了临冬城的居民。你必须物理净化掉这些被感染的村民，从而阻止病毒的继续传播。  
[任务已接受]  
一个死亡病毒"> 
</div>  

## 2.前置
在没有设定任何前置的情况下，每个玩家都可以接受你的任务。不过，这个任务相当棘手！所以我们得要求玩家至少获得10点任务点数，才能接受这个任务：  
```/qa edit TheVirus requirements add QuestPoints moreOrEqualThan 10```  
任务点数可以通过完成任务获得，或者手动发放。  
如果玩家目前不满足前置条件，接取任务时会看到这个提示。  
<div align=center><img src="/pic/getting-started/quest-successfully-created.png" alt="您没有满足该任务的前置要求! 缺少要求:你至少需要10点任务点数。"> 
</div>  

为了进一步测试我们的任务，先给自己发放10点任务点数吧：  
```/qa questpoints putyourminecraftnamehere add 10```  


?> 如果你喜欢NotQuests插件，请在Modrinth上关注[NotQuests](https://modrinth.com/plugin/notquests/versions)😊这样能激励我为您带来更多更新和功能！  
<br/>  


## 3.目标
目标是每个任务的核心组成部分。那我们来添加第一个目标吧！  
首先，玩家需要清理被僵尸堵塞的道路：  
```/qa edit TheVirus objectives add BreakBlocks dirt 64```  
当玩家破坏完64个泥土时，该目标即达成👍如果你想，你还可以在这里指定多种方块作为任务目标。  
比如，如果你想将玩家破坏的方块指定为泥土或石头，就需要输入```dirt,stone```。  
现在，我们给我们的目标添加一条描述：*被感染的僵尸在街上拉屎了！你需要通过破坏64个泥土才能清理干净！*  
```/qa edit TheVirus objectives edit 1 description set The infected Zombies shat on the street. Clean it up by breaking 64 dirt blocks!```  
再设定目标的显示名称：*Stinky Street*  
```/qa edit TheVirus objectives edit 1 displayName set Stinky Street```  
然后就可以用命令```/q take TheVirus```接取我们的任务了！  
<div align=center><img src="/pic/getting-started/after-accepting-with-first-objective.png" alt="目标：1.Stinky Street：描述：被感染的僵尸在街上拉屎了！你需要通过破坏64个泥土才能清理干净！  破坏方块：泥土  进度：0/64  任务描述：一个死亡病毒感染了临冬城的居民。你必须物理净化掉这些被感染的村民，从而阻止病毒的继续传播。  
[任务已接受]  
一个死亡病毒"> "></div>  

这些都很简单对吧？  


### 第二目标

接下来就是我们的下一个任务目标！街道已经清理干净了！该物理净化一下这些被感染的村民了：  
```/qa edit TheVirus objectives add KillMobs zombie_villager 15```
在击杀15个僵尸村民后，该目标就会完成！那现在我们来给这个目标加上描述吧：*如你所见，你的面前都是被感染的村民！为了阻止病毒的传播，干掉他们！*  
```/qa edit TheVirus objectives edit 2 description set You can see the infected villagers in front of you! Murder them all to stop the virus from spreading!```  
然后还有显示名称：*僵尸突围！*  
```/qa edit TheVirus objectives edit 2 displayName set Zombies ahead!```  

### 目标依赖

现在，在接受这个任务后，你将看到以下内容：  
<div align=center><img src="/pic/getting-started/after-accepting-with-second-objective.png" alt="目标：1.臭街：描述：被感染的僵尸在街上拉屎了！你需要通过破坏64个泥土才能清理干净！ 破坏方块：泥土 进度：0/64  2.僵尸突围！：描述：如你所见，你的面前都是被感染的村民！为了阻止病毒的传播，干掉他们！ 击杀生物：僵尸村民 进程0/15  任务描述：一个死亡病毒感染了临冬城的居民。你必须物理净化掉这些被感染的村民，从而阻止病毒的继续传播。  
[任务已接受]  
一个死亡病毒"> "></div>  


如你所见，当前这个任务的两个目标都是可见的。可以按照任意顺序完成任务目标。  
不过，我们想让第二目标“僵尸突围！”在完成第一目标后才变得可见、可完成，换言之，就是预置目标进程的完成顺序。  
为了实现这一想法，我们需要给第二目标添加一个**条件**，让玩家先去完成第一目标才能解锁第二目标。在NotQuests中要想实现的话有两种方法（任选其一）：  

+  **简单一点的方法**：```/qa edit TheVirus objectives predefinedProgressOrder set firstToLast```。根据目标添加的前后顺序自动为任务设定目标顺序，后续添加的任务也会继续这样排序。  

+  **难一点的方法**：```/qa edit TheVirus objectives edit 2 conditions unlock add CompletedObjective 1```。设置解锁目标2的**条件**为完成目标1。如果有多个目标，你就需要挨个给它们设置。不过，这种方法有很高的灵活性。  
完成！现在要是你刚接受这个任务，你就会看见第二目标是隐藏着的。  

<div align=center><img src="/pic/getting-started/after-accepting-with-second-objective-and-dependency.png" alt="目标：1.臭街：描述：被感染的僵尸在街上拉屎了！你需要通过破坏64个泥土才能清理干净！ 破坏方块：泥土 进度：0/64  2.[隐藏]  任务描述：一个死亡病毒感染了临冬城的居民。你必须物理净化掉这些被感染的村民，从而阻止病毒的继续传播。  
[任务已接受]  
一个死亡病毒"> "></div>  

第二目标会在你完成第一目标后解锁。😀


## 4.触发器
通过触发器，我们可以给任务添加一些事件。  
当玩家做到第二个目标时，他需要去击杀一定数量的僵尸村民，然后他就会发现一件事，那就是**他没有僵尸村民可杀**。那咋办？  
为此，我们就让NotQuests在玩家**完成第一目标后为他生成一些僵尸村民以供击杀**。  
首先，我们需要创建**生成僵尸村民**的事件。事件在创建后，可以在该任务外的其它任意任务中重复使用。我们来创建一个SpawnMob的事件，将事件命名为```Spawn15ZombieVillagers```：  
```/qa actions add Spawn15ZombieVillagers SpawnMob zombie_villager 15 PlayerLocation```  
这个事件会在接取任务的玩家当前所在的位置生成15个僵尸村民😄  
现在，我们把这个事件添加进我们任务的触发器里：  
```/qa edit TheVirus triggers add Spawn15ZombieVillagers BEGIN --applyon O2 --world_name ALL```  
一旦我们开始（BEGIN）在所有世界（不限定世界）里进行第二目标（O2，O是Objective的缩写）时，就会运行“*Spawn15ZombieVillagers*”事件。请随意测试 - 会起效的。👍  
<div align=center><img src="/pic/getting-started/trigger-after-completing-first-objective.png" alt="右下角是完成任务目标的提示"></div>  

## 5.奖励
要是你的玩家完成这么艰难的任务后你都不给他一点奖励，那他就既浪费了时间又没有收获，他一定会恨你的。所以，我们来加一点奖励吧：  

+ +2任务点数：```/qa edit TheVirus rewards add QuestPoints add 2```  
+ 2把剑：```/qa edit TheVirus rewards add GiveItem hand 2```  
+ + 上面这个命令在输入时，由于你想设定奖励为剑，所以你手上必须手持剑。除此之外，你也可以用这个命令：```/qa edit TheVirus rewards add GiveItem wooden_sword 2```  
+ +300金钱（该功能必须安装Vault）：```/qa edit TheVirus rewards add Money add 300```  
+ 想通过命令给予玩家来自一些其它插件的奖励吗？你可以用{PLAYER}占位符表示玩家。举例：```/qa edit TheVirus rewards add ConsoleCommand cr give to {PLAYER} DailyCrate 2```  

### 奖励显示名称
玩家在完成任务后，会获得奖励，然而，这并不会通知玩家。这是因为在默认情况下奖励是隐藏着的（可以在config中修改），**除非你给它们添加一个显示名称**！所以，我们来添加吧：  
1.```/qa edit TheVirus rewards edit 1 displayName set +2 Quest Points```  
2.```/qa edit TheVirus rewards edit 2 displayName set +2 handcrafted Wooden Swords```  
3.```/qa edit TheVirus rewards edit 3 displayName set +300 Coins```  
完成！这下玩家在完成任务后，就会看见任务的奖励：  
<div align=center><img src="/pic/getting-started/quest-completed-rewards.png" alt="[任务完成]一个死亡病毒  
奖励：- +2任务点数 - +2handcrafted Wooden Swords - +300硬币"></div>   


## 6.更多任务设定
我们不希望玩家在完成任务后一遍一遍又一遍地接受该任务。我们就可以对其进行限制。  
首先，我们可以设置，玩家在完成任务后需要等待20个小时后才能再次接受该任务：  
```/qa edit TheVirus acceptCooldown complete set 20h```  
20h=20小时，现在，我们给任务再添加一个最多只能完成10次的硬性限制。在第10次完成任务后，玩家无论等待多久都不能再次接受该任务：  
```/qa edit TheVirus limits completions 10```  
要是你想限制玩家的失败次数，当玩家失败或放弃了3次以上任务的话，就不给他接受任务的话，简单：  
```/qa edit TheVirus limits fails 3```  
除此之外，你还可以在他第一次试图发起任务时阻止他：  
``` in the first place```  
最后，我们把takeEnabled设定为false：  
```/qa edit TheVirus takeEnabled false```  
这样会使玩家无法通过```/q take TheVirus```命令接受任务。因此，玩家们必须通过右击任务派发NPC或者任务派发盔甲架上。详细内容会在下一节讲述：  

## 7.NPC交互式接取任务
使用```/q take TheVirus```命令可以接受任务。不过你还可以使用```/qa edit TheVirus npcs add [NPC ID]```或者```/qa edit TheVirus armorstands add```命令将接受任务的操作绑定在某个CitizensNPC或者盔甲架上。  
任务文件将会储存在```plugins/NotQuests/default/quests.yml```以及```plugins/NotQuests/default/actions.yml```文件中。

# 高级概念
## 类别
你可以根据类别将任务进行分组。类别只是一种将任务划分到一起的方式。我们来创建一个名叫"Virus Quests"（病毒任务）的类别吧：  
```/qa categories create VirusQuests```  
现在将我们的任务移动到这个类别（默认情况下，新建任务都会被归类至"default"类别）。  
```/qa edit TheVirus category set VirusQuests```  
完成 - 就是这么简单！一个任务只能属于一个类别。值得一提的是，类别这个功能决定着NotQuests的文件夹结构 - 甚至还决定着GUI中的布局！  

### 子类别
每个类别都可以拥有子类别，并且子类别没有限制，你可以根据自己的需要随意套娃。下面这个是为"VirusQuests"（病毒任务）类别创建一个名为“Zombies”的子类别的示例：  
```/qa categories create VirusQuests.Zombies```  

### 类别显示名称
我上面创建时所输入的，只是作为类别的一种标识符。你可以添加一个显示名称（玩家实际在游戏中会看到的）。显示名称可以包含空格，甚至颜色代码，就跟前面所说的任务名称一样！下面是一个示例：  
```/qa categories edit VirusQuests displayName set <dark_green>Virus Quests <main>(dangerous)```  

### 预置类别的进程顺序
（待实现，但我仍要写这部分内容。这个功能类似于前文任务>目标依赖中所说的预置进程完成顺序，不过这项功能是应用于类别>任务。非常地有用，可以极大地简化你的工作，提升你的工作速度。）

## 子目标
<div align=center><img src="/pic/getting-started/sub-objectives.png" alt="目标：1.草坪的呻吟：破坏方块：草方块 进度：0/3 2.提升土壤质量：2.1.减少泥土会好一点：破坏方块：泥土 进度：0/5 2.2.跳跃：在泥土上蹦迪 进度：0/3 3.与Alessio对话 向Alessio反馈 进度：0/1 任务描述：给Bobby的一些清理任务 [任务已接受]我们的草坪"></div>   

NotQuests支持子目标，每个目标都可以有无数个子目标。而每个子目标也可以拥有无数个子子目标……以此类推！  
要创建子目标的话，你必须要先创建一个“Objective”目标作为它的父目标。在上面那个截图中，我们可以看到，子目标2.1和2.2归属于“Objective”目标2。  
如果你为“Objective”目标添加了子目标，那么当所有子目标完成后，该“Objective”目标就会被标记为完成。但如果你给其它类型的目标添加了子目标的话，那么你需要先完成子目标，才能继续进行父目标（即，子目标完成后，父目标不会被标记为完成，你需要在完成子目标后再去完成父目标的目标要求）。  

举例：  
1.```/qa edit quest objectives add Objective "<gold>Improve soil quality"```  
2.```/qa edit quest objectives edit 1 objectives add BreakBlocks dirt 5```  
3.```/qa edit quest objectives edit 1 objectives edit 1 displayName set Less dirt is good```  
4.```/qa edit quest objectives edit 1 objectives add Jump 3.0 --taskDescription "Jump on the soil to make it better"```  

## 目标条件类型
在前面的教程部分，我们讲述了如何通过条件来设定目标依赖。命令是：```/qa edit TheVirus objectives edit 2 conditions unlock add CompletedObjective```。  
不过，你可以给目标添加不同类型的条件。这里说到的是解锁条件（unclock），用于设定目标是否隐藏，隐藏的情况下，不会计入进度，也无法完成该目标。  
此外，你还可以添加目标条件用来检查你是否能够推进目标进度或完成目标，这一点也很有用！  
举例：  
+ ```/qa edit 任务名称 objectives edit 1 conditions unlock add Flying equals false``` - 解锁条件。如果你处于飞行状态，目标将会保持锁定/“隐藏”状态。  
+ ```/qa edit 任务名称 objectives edit 1 conditions progress add Flying equals false``` - 目标将一直处于显示状态，但当你处于飞行状态时，你无法推进目标进度。  
+ ```/qa edit 任务名称 objectives edit 1 conditions complete add Flying equals false``` - 目标将一直处于显示状态，你也可以推进目标进度，但是如果你不满足条件（根据命令可知，条件是不处于飞行状态），即便达成进度，目标也不会完成。  

## 目标变量
NotQuests还会提供一些变量，让你可以把一些意想不到的目标添加进任务里！举个例子，如果你想添加一个“游玩100分钟”（PlaytimeMinutes）的目标：  
```/qa edit 任务名称 objectives add NumberVariable PlaytimeMinutes moreOrEqualThan 100```  
那要是玩家已经玩了100分钟了该怎么办呢？那就这样设定，让玩家再玩100分钟 - 也就是说，从接受任务/解锁目标的那一刻才开始计时：  
```/qa edit 任务名称 objectives add NumberVariable PlaytimeMinutes moreOrEqualThan PlaytimeMinutes+100```  
此处```PlaytimeMinutes+100```的意思是要求玩家再游玩100分钟。在NotQuests中这是可以实现的，当然，你还能在很多地方用上这样的表达式（如数学、其它变量等）。  
发挥一下你的想象力，这么想象一下，我们是否可以根据玩家已完成的任务量/玩家的实力/玩家的NPC好感度/玩家所持有的任务点数/玩家赚取的金钱数，去设置一个动态的目标？这并不是什么难事，在NotQuests中这样的事情轻而易举。  

## 高级方块/材料选择器
在为BreakBlocks目标设定相应目标方块时，或是在为事件/奖励设定GiveItem的相应方块/材料时，你会用到这项功能。我们为此设计了一套方块选择工具，你可以随意指定你所需的方块/材料。并且，在NotQuests中，你不仅可以指定一种方块/材料，你还可以指定多种方块/材料！这里举个例子：  
```/qa edit 任务名称 objectives add BreakBlocks diamond_ore,deepslate_diamond_ore 20```  
没错！这样设定的话，无论是破坏钻石矿石，还是破坏深层钻石矿石，都会计入进度。  
再来个例子：  
```/qa edit 任务名称 objectives add PlaceBlocks hand,acacia_log,spruce_log,birch_log,dark_oak_log 15```  
你会发现这项功能有用，对吧？  
这项功能甚至可以用在GiveItem事件中，这样一来，你就可以一次给玩家发放多个物品！  

## NotQuests表达式非常强大！
如果你想，NotQuests甚至还有能力处理更为复杂的条件。现在你还可以在表达式中使用布尔比较。注意：条件可以用于任务需求/目标条件，它们是一样的。  
举几个实际的例子：  
+ ```/qa conditions add cname True equals (Money>10)&Flying```这个命令会检查你是否在飞行，同时检查你的当前财产是否大于10。  
+ + 还有其它方法同样能做到：```/qa conditions add cname True equals Condition(Conditions:Flying&IsRich)```  
+ + 再或者：```/qa conditions add cname Condition equals Flying&IsRich```  

在表达式内，你还可以在条件里使用```|（或者）```操作符或者```!（否定）```。  
再举个例子：  
```/qa conditions add moneyCondition Money moreThan 10+TagInteger(TagName:reputation)*TagInteger(TagName:level)```  
这个条件要求你拥有一定数量的金钱，金钱数=10+“好感度（Reputation）”标签值*“等级（Level）”标签值。  
这还有一个更为复杂的：  

```/qa actions add pp3 Money add ((TagInteger(TagName:points)>=4)*(10+30))+(!(TagInteger(TagName:points)>=4)*5)```  

如果你的“点数（Points）”标签（整数标签）大于等于4，这个事件将会被激活，然后给你40块钱。如果没有达到这个要求，将会给你5块钱。如果你想了解标签系统的更多内容，请查阅[标签系统指南](/教程/ReputationSystem.md)。  
[操作符大全](https://pastebin.com/raw/qZqQmL8x)。  
诸如此类的NotQuests表达式可以在很多地方使用 - 非常强大！  

## 个人资料
在NotQuests中，每个拥有“notquests.user.profiles”权限节点的玩家都会拥有一份**个人资料**！🔥每份个人资料都会记录**他们的任务点数、标签状况以及完成的任务等**信息。所以，如果玩家需要的话，这项功能可以让他们重头再来，以选择不同的路径，从而尝试竞速玩法，亦或者仅仅是为了重新体验RPG游戏的乐趣 - 再或者为了其它目的！  
显示你当前的个人资料：```/notquests profiles show```  
创建一份新的个人资料：```/notquests profiles create 个人资料名称```  
修改你的个人资料：```/notquests profiles change 个人资料名称```

# 接下来？
至此，你已经学会了如何创建任务了！开始上手吧！你可以在[文档](/文档/Documentation.md)部分获取到关于NotQuests的更多信息。如果你需要任何帮助，欢迎你加入我们的[Discord](https://discord.gg/7br638S5Ex)。