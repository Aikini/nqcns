# 🎨自定义<!-- {docsify-ignore-all} -->
# GUI物品
你可以自定义在GUI界面中类别（默认：箱子）和任务（默认：书）的物品显示。任务的话，需要使用命令```/qa edit 任务名称 guiItem ...```，类别的话，需要使用```/qa categories edit 类别名称 guiItem ...```。  
## 高级物品（例如：自定义模型数据）
NotQuests支持任意物品 - 不管这些物品有多么复杂，比如其它插件的那些特殊物品！NotQuests使用了Bukkit物品序列化API，因此，只要那些插件的物品支持该API，NotQuests就支持这些插件的物品。  
如果你有符合这个条件的复杂物品（不仅是材料），要想将它们加进GUI里，只需将该物品拿在手中，然后使用"hand"替代其名称。例如，如果你想将GUI中的类别物品槽的材质换成你那炫酷吊炸天的自定义模型数据物品，只需手拿该物品，然后输入```/qa categories edit 类别名称 guiItem hand```。就是这么简单！  
# 语言  
在NotQuests中，你可以修改大部分字符串和翻译（目前还不是全部，但都是最重要的部分）。你可以在NotQuests的“languages”文件夹里找到对应语言进行修改。  
# 自定义整个GUI
GUI中的所有物品的材料及其位置都是可以在“languages”文件夹的翻译文件中进行某种程度上的自定义。  
# 颜色代码
NotQuests几乎所有地方都支持颜色代码 - 不过可能和你所熟知的颜色代码有所差异。像&6或&c之类的颜色代码不会给你带来太大帮助 - 毕竟它们早已被Mojang遗弃，现如今是由Spigot进行维护 - 而由于NotQuests致力于现代化和创新，所以也遗弃了这些被Mojang遗弃的颜色代码。  
与此相对的，我们现如今使用的是MiniMessages，相比之前的颜色代码，它能做一些更高级的东西，而且更简单一些。比如RGB颜色、渐变、甚至还能做到点击命令和悬停消息！你可以在[这里](https://docs.advntr.dev/minimessage/)查看MiniMessages文档。  
现在，我们来给我们的任务添加一个带颜色的显示名称：  
```/qa edit TheVirus displayName set <red>A <bold>Deadly</bold> <#eb34a1>Virus```  
<div align=center><img src="/pic/Customization/displayname-1.png" alt="任务TheVirus已成功创建！"> 
</div>  
或者，甚至还可以这样：  

```/qa edit TheVirus displayName set <rainbow>A <bold>Deadly</bold></rainbow> <gradient:#eb34a1:#ffffff>Virus</gradient>```  
<div align=center><img src="/pic/Customization/displayname-2.png" alt="任务TheVirus已成功创建！"> 
</div>   
超级酷，对吧？你甚至可以在很多命令上用自动补全功能补全MiniMessage颜色标签。同时，NotQuests还内置了一些颜色，让你能使用它们来实现一些统一的外观。例如```<highlight>```、```<highlight2>```或```<main>```。这些都可以在config里自定义，以调整NotQuests整体的颜色主题。

**举例**：在任务的第一目标描述中添加可点击的链接：  
```/qa edit 你的任务名称 objectives edit 1 description set <click:OPEN_URL:此处放入url链接>Click here</click>```