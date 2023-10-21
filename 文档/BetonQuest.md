# 🪨 BetonQuest<!-- {docsify-ignore-all} -->
你可以在BetonQuest里使用NotQuests的所有条件和事件。同时，你也可以在NotQuests里使用BetonQuest的所有事件、条件和目标。仅支持[BetonQuest 2.x及以上版本](https://docs.betonquest.org/1.12/)
# ❤️ 在BetonQuest里使用NotQuests对话拦截器
效果展现：[https://youtu.be/uKFuSV1CLFo](https://youtu.be/uKFuSV1CLFo)  
使用方法：在BetonQuest config里使用```default_interceptor: notquests```。同时，还需要确保你的```default_conversation_IO:```设定的是```menu```或者```simple```。

# ❤️ 在NotQuests里使用BetonQuest事件
示例：```/qa actions add 事件名称 BetonQuestFireEvent default tag_wood_done```  
或  
示例：```/qa actions add 事件名称 BetonQuestFireInlineEvent tag add wood_done```

# ❤️ 在NotQuests里使用BetonQuest条件
示例：```/qa conditions add 条件名称 BetonQuestCondition default wood_done equals true```

# 💛 你也可以在BetonQuest事件里使用NotQuests事件
+ ```nq_action <事件类型> <该NotQuests事件的内联参数>``` - 内联参数后续将在相应的类型页面中进行文档化。  
+ + 示例1：```nq_action Beam test world -15140 85 2234```
+ + 示例2：```nq_action Beam test -15140;85;2234;world```
+ ```nq_triggerobjective <触发器名称>```
+ ```nq_startquest <任务名称> (可选flag: -force -silent -notriggers)```
+ ```nq_failquest <任务名称>```
+ ```nq_abortquest <任务名称>``` - 如果该任务处于激活状态，这只是移除玩家的任务，不算做失败。  
+ ```nq_questpoints <set/add/remove> <数量> (可选flag: -silent)```

# 💛 你也可以在BetonQuest条件里使用NotQuests条件
+ ```nq_condition <条件类型> <该NotQuests条件的内联参数>```
