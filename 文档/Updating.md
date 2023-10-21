# 🆙 从v3及以下版本升级<!-- {docsify-ignore-all} -->
在NotQuests的4.x版本中，我对条件（包括前置）、事件（包括奖励）和整个文件夹结构（类别的原因）进行了诸多更改。  
为此编写一个自动转换器什么的既困难又耗时。这就是为什么早期版本的NotQuests与4.x不完全兼容。  
# 如何升级
## 最简单的方法：清除安装
最简单的方法当然就是将服务器关闭，然后删除```plugins/NotQuests```文件夹，下载新版本的NotQuests插件，然后重新启动服务器。这样一来，你会丢失所有的进度，不过这样更新非常地干净，不会出现什么问题。尽管如此，如果你像保留之前的对话的话，你可以看看下方较难的步骤3，这非常简单，只需要移动文件夹即可。  
## 较难的方法：尝试尽可能地保留一些数据
1. 关闭服务器并删除```plugins/NotQuests/translations```文件夹。
2. 升级插件.jar文件，启动服务器，然后再次关闭。  
3. 移动```plugins/NotQuests/conversations```文件夹到```plugins/NotQuests/default/conversations```。这样一来，就可以保留先前的对话。  
4. 移动```plugins/NotQuests/quests.yml```文件到```plugins/NotQuests/default/quests.yml```，然后打开quests.yml文件，清除文件中所有奖励/前置（事件/条件）内容。如果觉得太难了，可以直接删除quests.yml，然后再启动再关闭服务器。 
5.  启动服务器，重新创建所有事件和条件。大多数事件和条件在此更新中已被破坏，我不觉得这值得我去尝试修复。```plugins/NotQuests/actions.yml```和```plugins/NotQuests/conditions.yml```可以删除，因为插件只会读取```plugins/NotQuests/default```文件夹中的文件。  
6. 服务器启用时查看控制台是否有警告或错误。如果有，请尝试阅读并解决他们。执行到第4步的时候困难会发生这种情况。  
