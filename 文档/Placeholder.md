# 📄 占位符<!-- {docsify-ignore-all} -->
# 玩家占位符
这些是你可以使用的所有玩家占位符（需要安装[PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI/releases)）：  
+ %notquests_player_has_completed_quest_QUESTNAME%
+ %notquests_player_has_current_active_quest_QUESTNAME%
+ %notquests_player_is_objective_unlocked_and_active_OBJECTIVEID_from_active_quest_QUESTNAME%
+ %notquests_player_is_objective_unlocked_OBJECTIVEID_from_active_quest_QUESTNAME%
+ %notquests_player_is_objective_completed_OBJECTIVEID_from_active_quest_QUESTNAME%
+ %notquests_player_questpoints%
+ %notquests_player_active_quests_list_horizontal%
+ %notquests_player_active_quests_list_vertical%
+ %notquests_player_completed_quests_amount%
+ %notquests_player_active_quests_amount%
+ %notquests_player_tag_TAGNAME%
+ %notquests_player_variable_VARIABLENAME%
+ %notquests_player_expression_EXPRESSION%
+ %notquests_player_rounded_expression_EXPRESSION%
+ %notquests_player_quest_cooldown_left_formatted_QUESTNAME%
+ %notquests_player_objective_progress_OBJECTIVEID_from_active_quest_QUESTNAME%
+ %notquests_player_objective_progress_percentage_OBJECTIVEID_from_active_quest_QUESTNAME%
应用时，需要将占位符中的```QUESTNAME```换作任务名称，将```OBJECTIVEID```换作目标的ID（可在```/qa edit questname objectives list```中查看），因此，占位符中的大写字母部分都需要进行替换，诸如此类，还有```TAGNAME```要换作标签名称，```VARIABLENAME```要换作变量名称，```EXPRESSION```要换作表达式。  
