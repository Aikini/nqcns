# ⏰日常任务<!-- {docsify-ignore-all} -->
很多人会来问如何创建日常任务 - 这个问题说难也难，说简单也简单，这得根据你的想法来。
# 选择1：每天可接受或完成一个任务的次数不得超过1次
如果你所说的“日常”任务是想让玩家每天只能完成或接受某个任务一次，那么做起来非常简单！只需要简单地将接受任务冷却事件设定为1天即可。  
```/qa edit 任务名称 acceptCooldown complete set 1d```  
# 选择2：从预设任务池里抽选日常任务
如果你想创建一个由多个任务组成的任务池，然后玩家每天都可以在这个任务池里抽选一个任务做，这种想法实现起来比较难，但还是能做到的！值得一提的是，最近我们正在为此开发一个系统，用于简化这个过程。  
NotQuests这款插件的功能非常强大，虽说是能做到的，但这个过程非常复杂。以下是设计构思：  
加入你创建了一个日常任务池，里面有2个任务，一个是A，一个是B。（除此之外，你还可以为每周和每月都设计一下周常任务和月常任务）  
1. 给2个任务都先设置1天接受任务冷却时间：```/qa edit A acceptCooldown complete set 1d```、```/qa edit B acceptCooldown complete set 1d```。  
2. 创建2个事件（giveQuestA、giveQuestB），该事件执行时会给予玩家任务：```/qa actions add giveQuestA GiveQuest A```、```/qa actions add giveQuestB GiveQuest B```。  
3. 创建一个事件，事件命名为Action，该事件执行时将随机执行giveQuestA事件或giveQuestB事件：```/qa actions add giveDailyQuest Action giveQuestA,giveQuestB 1 --minRandom 1 --maxRandom 1```。这里使用了--minRandom 1和--maxRandom 1两个Flag，用于限制执行的事件数量，最小是1，最大也是1。如果没有这两个Flag，该事件执行时会执行2个事件，给予玩家2个任务，加上这两个Flag后，就只会在这2个事件中随机选择1个事件，即为玩家随机提供1个任务。  
4. 前面我们给2个任务都添加了接受任务冷却时间，那这里我们为Action事件添加2个条件，使其在任务A和任务B都不在冷却时间内时才能执行：```/qa actions edit giveDailyQuest conditions add QuestOnCooldown A equals false```、```/qa actions edit giveDailyQuest conditions add QuestOnCooldown B equals false```。  
5. 像这样执行事件，这下就能够实现先前构想出的任务池功能：```/qa actions edit giveDailyQuest execute```。
