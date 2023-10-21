# 🎭 条件<!-- {docsify-ignore-all} -->
原始条件可以使用```/qa conditions```命令进行创建。这些都将保存在```plugins/notquests/categoryname/conditions.yml```。条件还可以作为任务前置、目标条件和事件条件。  
你可以通过```/qa conditions edit conditionname check <玩家ID(可选)>```命令“测试”你通过```/qa conditions```命令创建的条件。  
**所有条件通用命令参数：**  
+ **```(flags)```** - 可选Flag
+ + **```--negate```** - 否定条件，如果条件是True，那么就会转变为False，如果条件是False，那么就会转变为True。  
+ + **```--category <类别名称>```** - 如果是一个原始条件，储存于conditions.yml里的条件，你可以在这里为其设定类别。    
<br/>

# 默认变量条件
这些条件将会充当变量的“容器”，这是啥意思呢？  
好吧……举个例子，Number条件就是这样的变量条件。在游戏中，它会将Number变量像很多条件的那样，转化为相应的条件，所以条件的数量实际上比你所认为的要多得多。  
更多请参阅变量部分。  
## ❓ 布尔|Boolean

> **满足需求**：The Boolean variable equals the expression。Boolean的取值只有2种：True和False。换言之就是表达Yes和No。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定Boolean变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 当然，Boolean的运算符只有一种：```equals```（等于）
> **```<表达式>```** - 用于指定变量的输出结果。常见值为```true```和```false```，不过你也可以在这里将它与其它Boolean变量进行比较。  
> **示例**：  
> + ```/qa conditions add 条件名称 Flying equals false```（设定某条件为正在飞行时输出false） - 此条件中Flying为变量类型。  
> + ```/qa conditions add 条件名称 True equals (Money>10)&Flying```（设置某条件为金钱大于10且正在飞行时输出true） - 此条件中“True”为变量类型。
> + + 同样的条件还可以这样写：```/qa conditions add 条件名称 True equals Condition(Conditions:Flying&IsRich)```（设定某条件为同时满足条件Flying和IsRich时输出true）  - 你需要事先创建```Flying```和```IsRich```条件。  
> + + 再或者：```/qa conditions add 条件名称 Condition equals Flying&IsRich```（设定某条件为同时满足条件Flying和IsRich时输出true） - 你需要事先创建```Flying```和```IsRich```条件。  
<br/>

## 📙 列表|List

> **满足需求**：The List variable equals the expression。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定List变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 运算符有这些选择：```contains```（包含）、```containsIgnoreCase```（包含，不区分大小写）、```equals```（等于）和```equalsIgnoreCase```（等于，不区分大小写）。  
> **```<表达式>```** - 用于指定变量的输出结果。这取决于变量类型。  
> **示例**：```/qa conditions add 条件名称 ActiveQuests contains 任务名称```（设定某条件为名叫“任务名称”的任务处于激活状态） - 检测如果该玩家名叫“任务名称”的任务当前处于激活状态，条件即满足。该条件中ActiveQuests为List变量。  
<br/>

## 📖 ItemStackList

> **满足需求**：The ItemStackList variable equals the expression。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定ItemStackList变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 运算符有这些选择：```contains```（包含）和```equals```（等于）。  
> **```<表达式>```** - 用于指定变量的输出结果。这取决于变量类型，但必须是物品。  
> **示例**：``` /qa conditions add 条件名称 Inventory contains diamond 32```（设定某条件为检测玩家物品栏是否有至少32个钻石） - 该条件中Inventory为ItemStackList变量。  
<br/>

## 💯 数字|Number

> **满足需求**：The Number variable equals the expression。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定Number变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。  
> **```<运算符>```** - 运算符有这些选择：``` equals```（等于）、```lessOrEqualThan```（小于或等于）、```lessThan```（小于）、```moreOrEqualThan```（大于或等于）和```moreThan```（大于）。
> **```<表达式>```** - 用于指定变量的输出结果。此处的表达式很强大，因为你可以在这里输入任何类型的数学表达式，甚至可以包括其它Number变量。  
> **示例**：```/qa conditions add 条件名称 Health moreOrEqualThan 9.0```（设定某条件为检测玩家生命值是否大于或等于9） - 该条件中生命值Health为Number变量。**再举个包含了数学表达式和其他变量的例子**：```/qa conditions add 条件名称 Money moreThan QuestPoints*Money+500-30/2```（设定某条件为检测玩家金钱是否大于*任务点数×金钱+500-30÷2*这个表达式的运算结果） - 该条件中Money为Number变量。**再举个带有非常高级的表达式的例子**：```/qa conditions add 条件名称 Money moreThan 10+TagInteger(TagName:reputation)*TagInteger(TagName:level)```（设定某条件为检测玩家的金钱是否大于*10+整数标签“好感度”数值×整数标签“等级”数值*） - 该条件中Money为Number变量。  
<br/>

## 🆎 字符串|String

> **满足需求**：The String variable equals the expression。  
> **命令参数**：  
> **```<变量类型>```** - 用于指定String变量的类型。  
> **```<变量参数>```** - 有些变量类型可能存在附加参数，也可能不存在。 
> **```<运算符>```** - 运算符有这些选择：```contains```（包含）、```endsWith```（字符串尾部字符是……）、```equals```（等于）、```equalsIgnoreCase```（等于，不区分大小写）、```isEmpty```（字符串是否为空）和```startsWith```（字符串开头字符是……）。  
> **```<表达式>```** - 用于指定变量的输出结果。String的意思是字符串，所以表达式的取值范围取决于变量类型。  
> **示例**：```/qa conditions add 条件名称 Name equals Tom```（设定某条件为检测玩家ID是否为Tom） - 该条件中Name为String变量。  
<br/>

# 默认条件
这部分讲述的是默认条件，这些条件是“独立”存在的，不依附于变量。


## ~~🤓 条件|Condition~~
!> 该条件已于4.13.0版本被移除。取而代之的是Boolean变量```Condition```，可以提供更多的功能。
<br/>


> ~~**满足需求**：其它条件均满足。没错，这个条件仅仅会检查其下属在```conditions.yml```里的另外一些条件是否满足。~~  
> ~~**命令参数**：~~  
> ~~+ **```<其它条件名称>```** - 用于指定玩家需要满足的其它条件。~~  
> ~~**示例**：```/qa conditions add 条件名称 Condition 其它条件名称```（设定某条件为满足名叫“其它条件名称”的条件）~~  
<br/>

## ⏲️ 世界事件|WorldTime

> **满足需求**：玩家所处的世界时间处于某个时间段内。  
> **命令参数**：  
> + **```<最小时间>```** - 用于指定时间段的最小时间（24小时制）。
> + **```<最大时间>```** - 用于指定时间段的最大时间（24小时制）。
> **示例**：```/qa conditions add 条件名称 WorldTime 11 20 ```（设定某条件为玩家当前所处世界的时间为上午11点至下午8点之间）
<br/>

## 📅 日期|Date

> **满足需求**：当前日期处于指定日期，可以通过操作符指定在日期之前，还是之后。  
> **命令参数**：  
> + **```<日期操作符>```** - 可以通过使用比较操作符将当前日期和指定日期进行比较。操作符有：```before```（之前）和```after```（之后）。比如：想要指定在2023年之后，那么就应当使用```after```。  
> + **```(flags)```** - 可选Flag  
> + + **```--year <年>```** - 用于指定具体哪年。
> + + **```--month <月>```** - 用于指定具体哪月。
> + + **```--day <日>```** - 用于指定具体哪日。
> + + **```--hours <时>```** - 用于指定具体是当天几时。
> + + **```--minutes <分>```** - 用于指定具体几分（需要指定几时才能指定几分）。
> + + **```--seconds <秒>```** - 用于指定具体几秒（需要指定几分才能指定几秒）。
> + + **```--timeZone <时区名称>```** - 用于指定该指定日期的时区名称。
> **示例**：
> + ```/qa conditions add 条件名称 Date after --year 2022 --timeZone Europe/Berlin```（设定某条件为当前处于2022年之后，时区为欧洲/柏林时间） - 设定一个条件，需要当前处于2022年后才满足，时区为欧洲/柏林时间
> + ```/qa conditions add 条件名称 Date after --month 11```（设定某条件为当前处于11月份之后） - 季节性条件！每年12月才能满足
> + ```/qa conditions add 条件名称 Date before --month 11 --year 2022```（设定某条件为当前处于2022年11月份之前） - 设定截至日期，直至2022年10月底，在那之后将不再满足条件  
<br/>

# 特殊默认条件
## 🎖️ 完成目标|CompletedObjective

> 这个条件在使用时需要附上一个目标。和其它条件可能不一样，这个条件会直接绑定在现有任务上。  
> **满足需求**：玩家需要完成当前任务指定的目标。  
> **```<目标ID>```** - 用于指定需要完成的目标ID。想要查询目标ID，需要使用```/qa edit 任务名称 objectives list```命令。  
> **示例**：```/qa edit 任务名称 objectives edit 1 conditions add CompletedObjective 2```（设定某任务的目标2解锁条件为完成目标1）
<br/>