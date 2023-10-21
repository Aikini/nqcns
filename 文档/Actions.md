# 🧨 事件<!-- {docsify-ignore-all} -->
可以使用```/qa actions```命令创建原始事件。这些事件都会保存在```plugins/notquests/categoryname/actions.yml```。事件也可以作为任务奖励或者目标奖励。事件（Action），顾名思义，就是会“发生”的一些事情。  
你可以通过```/qa actions edit actionname execute <玩家ID(可选)>```命令“测试”你通过```/qa actions```命令创建的条件。如果你想无视这个事件下的条件限制，你可以使用一个可选Flag：```--ignoreConditions```  

**所有事件通用命令参数：**  
+ **```(flags)```** - 可选Flag
+ + **```--category <类别名称>```** - 如果是一个原始事件，储存于actions.yml里的事件，你可以在这里为其设定类别。 
+ + **```--delay <delay>```** - 如果是一个原始事件，储存于actions.yml里的事件，你可以在这里为其设定执行延迟。比如：如果输入1s，那么事件将会在1秒后执行，而不是立即执行。  

# 默认变量事件
这些事件将会充当变量的“容器”，这是啥意思呢？  
好吧……举个例子，Number事件就是这样的变量事件。在游戏中，它会将Number变量像很多事件的那样，转化为相应的事件，所以事件的数量实际上比你所认为的要多得多。然而，有些变量适用于条件，而不适用于事件。例如，DayOfWeek变量就只适用于条件，而不适用于事件。  
有道理吧？在现实生活中，你不能单纯靠一个Minecraft的插件就做到穿越时空。不过，“Money”这个变量既适用于条件，也适用于事件。因为你可以查看玩家的金钱，也可以改变他们的金钱。当然，我说的只是游戏中的金钱🥲  
更多请参阅变量部分。  

## ❓ 布尔|Boolean

> **发生事件**：Boolean的取值只有2种：True和False。换言之就是表达Yes和No。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定Boolean变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 可用运算符：```equals```（等于）
> **```<表达式>```** - 用于指定变量的输出结果。常见值为```true```和```false```，但你也可以在这里设定一个不同的Boolean变量。  
> **示例**：  
> + ```/qa actions add 事件名称 Flying set true```（设定某事件为开启飞行） - 此条件中Flying为变量类型。  
> + ```/qa actions add 事件名称 Money add ((TagInteger(TagName:points)>=4)*(10+30))+(!(TagInteger(TagName:points)>=4)*5)```（设定某事件为给予玩家金钱，如果玩家的整数标签“points”数值大于等于4，那么该事件将给予玩家40的金钱。否则，就给予5）
<br/>

## 📙 列表|List

> **发生事件**：The value of this List variable is changed。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定List变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 可选操作符：```add```（增加）、```clear```（清空）、```remove```（删除）和```set```（设置）。  
> **```<表达式>```** - 用于指定变量的输出结果。这取决于变量类型。  
> **示例**：```/qa actions add 事件名称 ActiveQuests add 任务名称```（设定某事件为强制给予玩家名叫“任务名称”的任务） - 该条件中ActiveQuests为List变量。  
<br/>

## 📖 ItemStackList

> **发生事件**：The value of this ItemStackList variable is changed。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定ItemStackList变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 可选操作符：```add```（增加）、```clear```（清空）、```remove```（删除）和```set```（设置）。  
> **```<表达式>```** - 用于指定变量的输出结果。这取决于变量类型，但必须是物品。  
> **示例**：``` /qa actions add 事件名称 Inventory remove hand 3``` - 该条件中Inventory为ItemStackList变量。  
<br/>

## 💯 数字|Number

> **发生事件**：The value of this Number variable is changed。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定Number变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 可选操作符：```add```（增加）、```deduct```（减去）、```divide```（除以）、```multiply```（乘以）和```set```（设置）。  
> **```<表达式>```** - 用于指定变量的输出结果。此处的表达式很强大，因为你可以在这里输入任何类型的数学表达式，甚至可以包括其它Number变量。  
> **示例**：```/qa actions add 事件名称 Money multiply 2```（设定某事件为玩家金钱乘以2） - 该事件中Money为Number变量。**再举个包含了数学表达式和其他变量的例子**：```/qa actions add 事件名称 Money set QuestPoints*Money+500-30/2```（设定某事件为设置玩家金钱=*任务点数×金钱+500-30÷2*这个表达式的运算结果） - 该条件中Money为Number变量。**再举个带有非常高级的表达式的例子**：```/qa actions add 条件名称 Money set 10+TagInteger(TagName:reputation)*TagInteger(TagName:level)```（设定某事件为设置玩家的金钱为*10+整数标签“好感度”数值×整数标签“等级”数值*） - 该条件中Money为Number变量。  
<br/>

## 🆎 字符串|String

> **发生事件**：The value of this String variable is changed。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定String变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。 
> **```<运算符>```** - 可选操作符：```set```（设置）和```append```（句未加字符串）。  
> **```<表达式>```** - 用于指定变量的输出结果。这取决于变量类型，但必须是字符串（即文本）。  
> **示例**：```/qa actions add 事件名称 CurrentWorld set world```（设定某事件为将玩家传送到世界world） - 该条件中CurrentWorld为String变量。  
<br/>

# 默认事件
这部分讲述的是默认事件，这些事件是“独立”存在的，不依附于变量。

## 🤓事件|Action

> **发生事件**：执行其它一个或多个事件。没错，这个事件会执行其下属在actions.yml里的其它事件。  
> **命令参数**：  
> + **```<其它事件名称>```** - 用于指定其它会一同执行的事件。
> + **```<数量>```** - （可选）用于指定该事件的执行次数。  
> + **```(flags)```** - 可选Flag  
> + + **```--ignoreConditions```** - 若设置了此Flag，那么被附加到其下属的其它事件执行时所需的条件都会被无视，无论其下属的事件需要什么样的条件，都会强制执行事件。  
> + + **```--minRandom <数量>```** - 若设置了此Flag，那么被附加到其下属的其它事件将会被随机执行，此Flag用于指定随机执行的最少数量。  
> + + **```--maxRandom <数量>```** - 若设置了此Flag，那么被附加到其下属的其它事件将会被随机执行，此Flag用于指定随机执行的最多数量。  
> + + **```--onlyCountForRandomIfConditionsFulfilled```** - 若设置了此Flag，那么只有满足条件的事件会被随机执行所选中。  
> + + **```--executedActionDelay```** - 若设置了此Flag，那么其下属的事件均会出现执行延迟。这可能会覆盖现有的延迟。  
> **示例**：
> + ```/qa actions add 事件名称 Action a1 2 --ignoreConditions```（设定某事件为执行名叫“a1”的事件2次，无视事件a1的条件）
> + ```/qa actions add 事件名称 Action a1,a2,money10 1```（设定某事件为执行名叫“a1”、“a2”、“money10”的事件1次）
> **带随机事件Flag的示例**：我事先创建了事件sm1、sm2、sm3、……、sm10，他们都是不同的SendMessage事件。
> + ```/qa actions add sendAllMessages Action sm1,sm2,sm3,sm4,sm5,sm6,sm7,sm8,sm9,sm10 1```（设定sendAllMessages事件为依照顺序依次执行事件sm1、sm2、……sm10）
> + ```/qa actions add sendAllMessagesInRandomOrder Action sm1,sm2,sm3,sm4,sm5,sm6,sm7,sm8,sm9,sm10 1 --minRandom 10 --maxRandom 10```（设定sendAllMessagesInRandomOrder事件为从10个事件中随机抽选*最少10个、最多10个*事件执行）
> + ```/qa actions add sendRandomMessage Action sm1,sm2,sm3,sm4,sm5,sm6,sm7,sm8,sm9,sm10 1 --minRandom 1 --maxRandom 1```（设定sendRandomMessage事件为从10个事件中随机抽选*最少1个、最多1个*事件执行）
> + ```/qa actions add sendGuaranteedRandomMessage Action sm1,sm2,sm3,sm4,sm5,sm6,sm7,sm8,sm9,sm10 1 --minRandom 1 --maxRandom 1 --onlyCountForRandomIfConditionsFulfilled```（设定sendGuaranteedRandomMessage事件为从10个事件中随机抽选*最少1个、最多1个*事件执行，只有满足条件的事件会被抽选，若玩家并不满足某个事件的条件，那么该事件就不会被纳入抽选范围内）
> + ```/qa actions add sendOneOrTwoRandomMessage Action sm1,sm2,sm3,sm4,sm5,sm6,sm7,sm8,sm9,sm10 1 --minRandom 1 --maxRandom 2```（设定sendOneOrTwoRandomMessage事件为从10个事件中随机抽选*最少1个、最多2个*事件执行）
<br/>

## ℹ️ Beam
## ℹ️ Boolean
## ℹ️ BroadcastMessage
## ℹ️ Chat
## ℹ️ CompleteQuest
## ℹ️ ConsoleCommand
## ℹ️ FailQuest
## ℹ️ GiveItem
## ℹ️ GiveQuest
## ℹ️ PlayerCommand
## ℹ️ PlaySound
## ℹ️ SendMessage
## ℹ️ SpawnMob
## ℹ️ StartConversation
## ℹ️ TriggerCommand

# [BetonQuest](https://dev.betonquest.org/)联动事件
## ℹ️ BetonQuestFireEvent
## ℹ️ BetonQuestFireInlineEvent