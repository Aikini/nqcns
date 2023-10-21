# 👩‍❤️‍👨用标签制作好感度系统<!-- {docsify-ignore-all} -->
![featuredImage.png](https://s2.loli.net/2023/10/21/4CnDA1dNwO9pJeo.png) 
本篇教程将教会你如何使用标签系统制作一个好感度系统 - 用权力的游戏作例子😊  
让我们来创建我们的好感度系统吧  
# 构思
在你完成任务的时候，该NPC对你的好感度会提升 - 不仅如此，该NPC所属的“家族”对你的好感度也会随之提升。在你获得一定好感度时，你将会解锁更多来自他们家族的任务，获得更好的奖励。家族里的NPC还会邀请你进入他们的家，届时，你将会获得额外秘密地点的访问权限。  
# 如何实现
这个构思大体上都可以通过NotQuests插件中强大的标签功能实现，我们可以很巧妙的运用起事件、条件和对话系统，将它们结合起来就可以实现这个构思。  
# 标签系统
NotQuests可以保存每个玩家的标签系统数据，就是这样，听起来很简单，而且非常有用，可以保存的玩家数据包括整数（=数字）、单精度浮点数/双精度浮点数（=带小数的数字）、字符串（=文本）和布尔值（=true或false）。  
你可以通过事件功能，修改玩家的标签，你也可以通过条件功能，检查玩家的标签。甚至，你还可以通过数学计算这些标签，或者将这些标签与其它变量和标签比较。  

?> 由于下面标签类型需要输入英文，所以这里给出几个标签类型的英文：  整数（Integer）、单精度浮点数（Float）、双精度浮点数（Double）、字符串（String）和布尔值（Boolean）。

# 创建我们的第一个标签
![npcs.png](https://s2.loli.net/2023/10/21/3wYLWA1X7ygGbOT.png)  

我们这有几个现成的NPC：Jon Snow（ID=0）、Arya Stark（ID=1）和Cersei Lannister（ID=2），Jon Snow和Arya Stark都归属于家族Stark。Cerse Lannister归属于家族Lannister。  
首先，我们来创建一个叫做JonSnowReputation。这个标签将会记录Jon Snow这位NPC对玩家的好感度。用于记录好感度应该使用整数，这个标签应该属于整数（Integer）标签：  
```/qa tags create Integer JonSnowReputation```  
然后再照着这个逻辑给其它NPC，以及它们的家族创建标签  
```/qa tags create Integer AryaStarkReputation```  
```/qa tags create Integer CerseiLannisterReputation```  
```/qa tags create Integer HouseStarkReputation```  
```/qa tags create Integer HouseLannisterReputation```  
![整数标签JonSnowReputation已成功创建  整数标签AryaStarkReputation已成功创建  整数标签CerseiLannisterReputation已成功创建  整数标签HouseStarkReputation已成功创建  整数标签HouseLannisterReputation已成功创建](https://s2.loli.net/2023/10/21/12Hg95MkGrAD8hV.png)  

# 创建事件用于修改好感度标签
好了，那我们来创建一些事件，先创建提升10点家族好感度的事件，再创建降低10点好感度的事件（更多详情请看下方命令）：  
```/qa actions add HouseStarkReputationAdd10 TagInteger housestarkreputation add 10```  
```/qa actions add HouseStarkReputationDeduct1 TagInteger housestarkreputation deduct 1```  
```/qa actions add HouseLannisterReputationAdd10 TagInteger houselannisterreputation add 10```  
```/qa actions add HouseLannisterReputationDeduct1 TagInteger houselannisterreputation deduct 1```  
现在，我们再来创建一个真实事件，当玩家为一个家族完成任务时，就会运行该事件。要是想让这两个家族敌对，那我们就设定，为Stark家族完成任务时，该家族对玩家的好感度+10，同时Lannister家族对玩家的好感度-1。  
这个命令将会调用刚才创建的事件```HouseStarkReputationAdd10```（Stark家族好感度+10）和```HouseLannisterReputationDeduct1```（Lannister家族好感度-1）。  
```/qa actions add HouseStarkQuestCompleted Action HouseStarkReputationAdd10,HouseLannisterReputationDeduct1 1```  
当这个“实际”的事件触发时，我们所创建的另外两个事件也会随之执行。然后，我们同样也给Lannister家族也整个事件：  
```/qa actions add HouseLannisterQuestCompleted Action HouseLannisterReputationAdd10,HouseStarkReputationDeduct1 1```  
## 把真实事件添加到NPC：更多事件嵌套
不过，照这样想，我们还可以设定在玩家完成任务时增加NPC个人对玩家的好感度，对吧？那我们来创建最后的几个事件吧！首先是好感度事件：  
```/qa actions add JonSnowReputationAdd5 TagInteger jonsnowreputation add 5```  
```/qa actions add AryaStarkReputationAdd5 TagInteger aryastarkreputation add 5```  
```/qa actions add CerseiLannisterReputationAdd5 TagInteger cerseilannisterreputation add 5```  
然后，创建最后的真实事件：  
```/qa actions add JonSnowQuestCompleted Action HouseStarkQuestCompleted,JonSnowReputationAdd5 1```  
```/qa actions add AryaStarkQuestCompleted Action HouseStarkQuestCompleted,AryaStarkReputationAdd5 1```  
```/qa actions add CerseiLannisterQuestCompleted Action HouseLannisterQuestCompleted,CerseiLannisterReputationAdd5 1```  
# 把事件添加到我们的任务
好耶！现在我们只需将最后的两个事件当作任务的奖励添加进做好的任务里就好了。我们在之前已经为此创建了```HelpJonSnow```、```HelpAryaStark```和```HelpCerseiLannister```这三个任务。（偷摸建的，自己建去，你应该知道该怎么创建任务了，如果不知道，去再读一遍[入门教程](/教程/GettingStarted.md)）。  
```/qa edit HelpJonSnow rewards add Action JonSnowQuestCompleted 1```  
```/qa edit HelpAryaStark rewards add Action AryaStarkQuestCompleted 1```  
```/qa edit HelpCerseiLannister rewards add Action CerseiLannisterQuestCompleted 1```  
噢我的老天爷，我们可算做完了！快去完成一下任务，看看你的好感度有没有变化。  
# 查看你的好感度（标签）
这里是一个查看Stark家族好感度的例子：  
```/qa variables check TagInteger housestarkreputation```  
# 让我们为我们的好感度系统增加一些特权和奖励：条件
这里举一个例子，这是一条检查Stark家族对你是否有至少50点的好感度的条件 - 可以用于任何地方，比如任务前置、目标或条件：  
```/qa conditions add HouseStarkReputation50 TagInteger housestarkreputation moreOrEqualThan 50```  
未完待续……等我有时间再来摸这部分内容。随时欢迎您对这篇教程或者其它教程做出贡献：[为文档作贡献](https://github.com/AlessioGr/NotQuests-Docs/blob/main/docs/tutorials/creating-a-reputation-system-with-tags.md)  