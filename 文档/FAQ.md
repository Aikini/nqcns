# ❓ 常见问题<!-- {docsify-ignore-all} -->
HELP！我的所有奖励都显示[已隐藏]
> 默认情况下，奖励都会处于隐藏状态，除非你为它们添加一个显示名称，需要使用命令```/qa edit [任务名称] rewards edit [奖励ID] 显示名称```，显示名称将会替换掉[已隐藏]。  
> 这样一来你就可以更好地指定奖励是些什么
  
我需要弄一个MySQL数据库吗？
> 不！普通的SQLite数据库（将会在你的```plugins/NotQuests```文件夹里创建）就可以支撑插件的正常工作吗。不过，MySQL更快，我也更推荐。数据库查询的设计也是适配MySQL的。  
  
如何将玩家数据从SQLite迁移到MySQL，或者二者相互迁移？
> 我建议你通过DBEaver或类似的工具手工操作。这并不难，因为不管是SQLite还是MySQL，NotQuests都使用着相同的SQL查询。还有一种目前处于实验性阶段的自动化迁移方式。我并不能保证其是否生效，因此请在那之前做好数据备份：  
> 1. 在general.yml设定load-playerdata-on-join和save-playerdata-on-quit为false
> 2. 使用旧数据库启动服务器
> 3. 添加新数据库到general.yml
> 4. 输入/qa reload命令（可能不需要）
> 5. 输入/qa debug loadDataManagerUnsafe命令
> 6. 关闭服务器
> 7. 撤销你在第一步所做的操作