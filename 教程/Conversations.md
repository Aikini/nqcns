# 💬对话<!-- {docsify-ignore-all} -->
NotQuests有一个特别棒的对话系统，你可以创建无数个对话，每个对话中，发言者、选项、路径和结果都是无限的。这也是整个插件中最难以理解的功能，因为对话系统是通过创建YAML文件来完成的。  
在这之前，请先了解一下YAML（yml），先对它有一个基本的认识，[这里](https://spacelift.io/blog/yaml)有一个教程可供你学习。确保在继续往下阅读之前，先理解yaml的层级关系（例如，在下面的这段演示用的对话代码中，你要一眼就看得出来，“greeting”是发言者“Atlas”的一部分，而“Atlas”又是“Lines”的一部分。在YAML中，通常使用缩进来表示层级关系，某个位置的缩进多了或少了，都会破坏整个层级关系，进而破坏整个句法）。  
接下来，安装一个合适且支持YAML的编辑器。这里我推荐使用[Visual Studio Code](https://code.visualstudio.com/download)。如果没有一个合适的编辑器，YAML的句法会很容易被破坏（特别是空格、标签和缩进），这会导致你的对话系统无法工作。况且Visual Studio Code会在你打错句法的时候提示你。  
# 创建一个演示对话
如果你还不知道这么创建对话，那么跟着我们先用命令```/qa conversations create test --demo```创建一个演示对话。在命令的句尾输入--demoFlag可以创建一个填充了演示数据的对话，而不是空白文件。命令中的**test**是这个对话的名称。创建完名叫test的对话后，将会生成一个对话文件，你可以在```plugin/notquests/default/conversations/test.yml```找到这个对话的文件 - 去找这个文件，然后用Visual Studio Code打开！这个文件应该是这个样子的：  
 
```

start: Atlas.specialgreeting,Atlas.greeting1
Lines:
  Atlas:
    color: "<BLUE>"
    delay: 200
    greeting1:
      text: "Hello traveler! I am atlas, the keeper of time!"
      next: Player.greeting1,Player.greeting2
      shout: true
    specialgreeting:
      text: "I don't wanna talk to you while you fulfill this condition. Bye!"
      conditions:
        - condition replaceThisWithTheNameOfYourCondition
    answer1:
      text: "That's a secret, but without me, you all wouldn't exist."
      next: Atlas.answer3
    notime:
      text: "Time is a rare good. Au revoir!"
    answer3:
      text: "Anyways though, what are you doing here?"
      next: Player.three,Player.four,Player.five
    answer4:
      text: "Oooh I see! I'm sure you are in need for some time, then. Should I lend you some?"
      next: Player.lend,Player.nolend
    answer5:
      text: "Here it is!"
      next: Atlas.answer6
    answer6:
      text: "[Hands time]"
      next: Player.bye
    nicebye:
      text: "You're very welcome. Good luck on your ventures!"
      actions:
        - "action replaceThisWithTheNameOfYourAction"
        - "action anotherAction"
  Player:
    delay: 200
    greeting1:
      text: "Nice to meet you! Why do you need to keep time?"
      next: Atlas.answer1
    greeting2:
      text: "I have no time for you."
      next: Atlas.notime
    three:
      text: "I'm just exploring the area!"
      next: Atlas.answer4
    four:
      text: "I'm on a mission."
      next: Atlas.answer4
    five:
      text: "I'm here to meet the king."
      next: Atlas.answer4
    lend:
      text: "Yes, please! I could use some time"
      next: Atlas.answer5
    nolend:
      text: "No, sorry, I have enough time. Thank you for the offer, though!"
      next: Atlas.notime
    bye:
      text: "Thank you a lot, time keeper. See you around!"
      next: Atlas.nicebye

```  
用你刚学到的YAML知识，尝试着去理解一下这个文件中的句法，以及它是如何运作的。动动你的小脑瓜，从头到尾看一遍。尝试改动一点东西，看看会发生什么。  
每当你修改完文件并保存后，你可以在游戏内使用```/qa reload conversations```命令去加载你的改动。还请留意你的控制台，看看是否有警告和错误，如果有，看一下哪里出错了。然后，你可以使用```/qa conversations start 你的对话名称```命令开始这段对话，本篇内容创建的对话名称叫做test，所以我们这里应该输入```/qa conversations start test```命令。  
# 一些解释
我没有太多时间，所以我暂时做不出100%详尽的教程 - 不过，你应该自己尝试去实验并理解这些功能。这篇教程我会在后续慢慢优化，那我们先来讲一些解释：  
## 专业术语
这份文件是一个**对话**（test）。一个对话可以包含多个**发言者**（本篇举例Atlas和玩家）。每个发言者都有多个**对话行**，格式是“```<发言者>.<对话行名称>```”。举例：```Atlas.greeting1```。  
## start
在第一行，你应该可以看见```start: Atlas.specialgreeting,Atlas.greeting1```这一行。这行设定了对话会从何处开始，并指定了2个对话行：Atlas.specialgreeting、Atlas.greeting1。  
这行句法的运行原理是先运行Atlas.specialgreeting对话行，那我们先来看这个对话行：  
```
specialgreeting:
    text: "I don't wanna talk to you while you fulfill this condition. Bye!"
    conditions:
    - condition replaceThisWithTheNameOfYourCondition
```  
正如你所见，这个对话行包含着文本（text）和条件（conditions）。文本的内容就是会发给玩家的内容。而条件则是要求玩家必须满足这个条件，才能播放对话行的文本。你可以在游戏中使用```/qa conditions create 你的条件名称 ...```命令创建条件 - 演示对话中的条件显然不可能存在（演示对话中的条件一栏翻译过来是“在这里替换成你的条件”），所以你可以替换掉它。  
那么，如果不满足这个条件，会发生什么？当然，由于这是对话的开头部分，而且在开头部分的```start: Atlas.specialgreeting,Atlas.greeting1```指定了2个对话行，第一个不满足条件，那么对话系统就会尝试播放逗号后的下一个对话行 - 也就是Atlas.greeting1：  
```
answer1:
    text: "That's a secret, but without me, you all wouldn't exist."
    next: Atlas.answer3
```  
所以说，开头部分的设定是按照前后顺序依次进行的，基本上只会播放第一个对话行（示例中是Atlas.specialgreeting），并且忽略掉第二个对话行（Atlas.greeting1），但是，如果玩家不满足第一个对话行的条件，那么就会按顺序进行下一个对话行。这就是将对话分支成多个路径的方法！  
## next
每个对话行都有一个```next: 对象```。我们用Atlas.answer1来做个例子：  
```
answer1:
    text: "That's a secret, but without me, you all wouldn't exist."
    next: Atlas.answer3
```  
**next**属性的对象决定了该对话行之后播放哪个对话。在这个示例中，接下来会播放的是```Atlas.answer3```。这点应该一眼就看得出吧。类似于前面所说的start，你也可以在此处用逗号分隔的方式指定多个对话行，从而根据所指定的对话行的条件进行分支。  
要是一个对话行里没有**next**属性的话，会发生什么呢？  
很简单！  
对话将会结束。没有下一步，对话会直接结束。  
# 时间和条件
每个对话行都可以添加**action**事件属性和**conditions**条件属性。当播放到此对话行时，就会执行该对话行下所指定的所有事件。只有对话行中指定的所有条件都满足时，才会播放该对话行。  
看看上面的演示对话 - 上面有关于事件属性和条件属性的示例。  
条件属性的句法通常是“condition 你的条件名称”。以“condition”作为开头，可以让它查询你在游戏中事先创建的条件，后面再写上指定的条件名称。事件的运作原理也相似。
## 否定条件
你在条件前面加上“!”用以否定条件。示例：  
+ "!condition 你的条件名称"
确保使用引号（""）将这个条件全部包裹起来。  
## 排列式事件/条件
根据上面所说的，在前面加上“condition”可以让它查询你在游戏中事先创建的条件。你还可以这样：  
```
conditions:
- Money moreThan 100
```  
或者：  
```
actions:
- StartConversation 其它对话名称
```  
而不能：  
```
actions:
- action 你在游戏中实现创建的用于触发另一个对话行的事件名称
```
我非常不推荐使用第三个句法，因为这部分内容没有相关文档，并且没有任何东西会检查你做的是否正确，不像在游戏里那样可以准确地告知你是否有错误（```/qa conditions create```和```/qa actions create```）。  
# 常见问题
**Q：对话系统延迟功能无法正常运作**  
A：这个功能处于一个“半损坏”的状态，预计在未来的版本中修复。  
**Q：一些东西发生了错误**   
A：请阅读下一部分（“一些东西无法正常运作”）。   
**Q：我先前的对话正在消失，消息也正在消失，出现了一些奇怪的问题，非常奇怪**  
A：你所遇到的问题可能是插件的对话神奇封包/对话修整功能导致的，这个功能可以简化你的对话历史记录！有人喜欢有人爱，但也有人觉得这很奇怪，这是可以理解的，你可以在NotQuests的config文件里禁用这个功能！  
**Q：为什么我在Discord里无法获得任何帮助？**  
A：对话系统复杂的要命，我可能需要很长事件才能搞懂问题的所在。并且，我是真的真的没啥时间。不过别担心！99%的问题最后都会被证明是用户自己的问题，而不是NotQuests插件本身的问题，所以说，问题的关键不在插件，而在你本身，这是可以解决的！对话系统非常容易出错，这也能引出另一个问题：  
**Q：既然对话系统那么难，那能搞个GUI界面吗？**  
A：不会的，绝对不会。要真用上这玩意儿的话情况不会变好，反而会更加糟糕。相反，我正计划着弄一个漂亮的Web UI。  
**Q：feature XY何时可以实现？**  
A：或许需要一周时间，或许永远也不能。我给不出一个大体的时间，也无法预测。因为我不知道我何时才能摸一摸NotQuests，也不知道这一摸能摸出多少进度。  
**Q：这篇教程何时更新更多内容？**  
A：上面一些答案或许已经说明了，很显然，我没有太多时间去更新这篇内容。这个插件是开源的，但可悲的是，掌握这个插件使用方法的人并不愿意与这个社区的其它玩家进行分享，或许屏幕前的你也会做出这样的选择。这里的文档和教程都是开源的，每个人都可以参与到其中，但没有人这样做，所以不要职责我！很多人都有足够的知识编写这样的教程，但我没有看见有人这样做。文档和教程都是公益性质的，我和玩家们（包括你）一样，无法从中获得任何煲粥。因此，如果你可以，请为他人考虑，来贡献出自己的一份力吧！❤️  
# 一些东西无法运作
如果你每次使用```/qa reload conversations```时，如果出现任何错误，都会在服务器控制台上弹出警告。所以请看看控制台的内容，看看这些该死的警告，它们会告诉你到底出了什么错误。  
所以，每次重载对话系统时，要是出现了什么错误，多看看服务器控制台会是一个很好的习惯。如果控制台说出现了一个**大**错误，并且字体颜色不是黄色的，那么错误就肯定涉及到了YAML句法，你绝对哪个句法搞错了。正如我在本篇内容的第二段和第三段所说的，你得使用一个合适的编辑器，它会在你出现句法错误时给你提示（比如Visual Studio Code），然后再去看看YAML教程吧。TAML对语法要求非常严苛 - 如果你的空格多了或是少了，都会引发错误。  
再加一个温馨提示：引号还是多用点比较好。  