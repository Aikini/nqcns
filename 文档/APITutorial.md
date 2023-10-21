# 💻 API示例项目教程<!-- {docsify-ignore-all} -->

?> 此教程基于插件版本5.17.1，Paper版本1.20.1编写的。  该部分内容超出了我的能力范围，推荐查看原帖：https://www.notquests.com/docs/documentation/api/api-tutorial

<br/>
让我们来用NotQuests API创建我们的第一个项目吧！  

# 步骤1：添加NotQuests API到你的项目
首先，在你的项目中先创建一个libs文件夹，并将NotQuests jar文件放入其中。*你还可以使用我们的GitHub packages仓库，不过它目前还无法很好地运作，因为你需要生成你自己的Github密钥且无法公开。至于JitPack，它们不支持Java 17*。  
<div align=center><img src="/pic/API/libsfolder.png" alt="libs文件夹"> 
</div>  

如果你使用gradle作为构建工具（你就该这么做），那么请打开您的```build.gradle```文件，在你的dependencies部分添加这些内容：  
```
dependencies {
    compileOnly 'io.papermc.paper:paper-api:1.20.1-R0.1-SNAPSHOT'
    compileOnly files('libs/notquests-5.17.1.jar')
}
```  
接下来，打开你的plugin.yml文件，并将NotQuests添加为depend或softdepend。在示例中，我们将其添加到了depend中：  

<div align=center><img src="/pic/API/pluginyml.png" alt="plugin.yml文件"> 
</div>  

# 步骤2：获取NotQuests实例
NotQuests有一个适用于Spigot的模块和一个适用于Paper的模块。二者大相径庭，Spigot模块非常古老。在本教程中，我们将只使用Paper模块来创建我们的目标、条件和事件。只有在使用Paper核心的服务器上，它们才能正常运行，而在Spigot上，Paper模块的NotQuests.getInstance()会返回空值，请在注册任何内容前都检查一下。  
无论如何你都不应该使用Spigot模块，不过不用担心，你的插件依旧可以在Spigot服务器上加载。  
请确保只使用来自Paper模块的类：  
<div align=center><img src="/pic/API/paperspigot.png" alt="paperspigot"> 
</div>   
好了，然后我们来在主类里创建一个NotQuests实例：  

```
public final class NotQuestsAPIExample extends JavaPlugin {

    private NotQuests notQuestsInstance;
    
    @Override
    public void onEnable() {
        // Plugin startup logic
        notQuestsInstance = NotQuests.getInstance();
    }

    @Override
    public void onDisable() {
        // Plugin shutdown logic
    }
}
```  

NotQuests几乎没有使用任何静态内容，所以我们将会在几乎所有地方使用实例。  

# 通过变量创建一个事件和条件（=前置）
在NotQuests中，你可以分别创建条件（Conditions）和事件（Actions）。不过，你也可以使用变量（Variable）来同时创建二者！  
能用到变量的话尽可能地使用变量。只有在使用变量无法做出你想要的功能时，再考虑直接注册条件和事件。  
我们来给玩家的饥饿值（Food Level）创建一个变量。创建一个名叫“FoodLevelVariable”新类，并使其继承Variable。饥饿值的取值范围是整数，而Variable类使用泛型（Generics）。  
然后，如果你的IDE没有出现问题，可以使所有必要的机制都生效的话，应该是这个样子：  

```
public class FoodLevelVariable extends Variable<Integer> {
    private final NotQuests main;
    
    public FoodLevelVariable(NotQuests main) {
        super(main);
        this.main = main;
    }

    @Override
    public Integer getValue(QuestPlayer questPlayer, Object... objects) {
        return null;
    }

    @Override
    public boolean setValueInternally(Integer newValue, QuestPlayer questPlayer, Object... objects) {
        return false;
    }

    @Override
    public List<String> getPossibleValues(QuestPlayer questPlayer, Object... objects) {
        return null;
    }

    @Override
    public String getPlural() {
        return null;
    }

    @Override
    public String getSingular() {
        return null;
    }
}
```  

All we need to do is fill out the each and every method. Let's start with getValue. This method will be used for the Condition which is generated from this variable. Here, we need to return the player's current food level. Pretty simple:  

```
@Override
public Integer getValue(QuestPlayer questPlayer, Object... objects) {
    return questPlayer.getPlayer().getFoodLevel();
}
```  

Next, in setValueInternally, that's what's used internally for the action. By default, a variable only needs the getValue method filled out. Only SOME variables can also change the value. It works here, so let's fill it out:  

```
@Override
public boolean setValueInternally(Integer newValue, QuestPlayer questPlayer, Object... objects) {
    questPlayer.getPlayer().setFoodLevel(newValue);
    return true;
}
```  

Always return true there if the setting-of-the-value is successful. Now we need to enable setting the value in the constructor. Otherwise, the corresponding action will not be generated:  

```
public FoodLevelVariable(NotQuests main) {
    super(main);
    this.main = main;
    setCanSetValue(true);
}
```  

As for getPossibleValues, let's leave it at null. NotQuests will just use the default integer auto-completion there. For getSingular and getPlural, use this:  

```
    @Override
    public String getPlural() {
        return "Food level";
    }

    @Override
    public String getSingular() {
        return "Food levels";
    }
```  

And we're done! Now just register this variable in the onEnable method in your Main:  

```
@Override
public void onEnable() {
    // Plugin startup logic
    notQuestsInstance = NotQuests.getInstance();
    if(notQuestsInstance != null){ //For Spigot compatibility
        notQuestsInstance.getVariablesManager().registerVariable("FoodLevel", FoodLevelVariable.class);
    }
}
```  

Done! Let's see how it looks in-game. During startup, you should be able to see this "Registering Variable" line in the console:  
<div align=center><img src="/pic/API/consoleregistering.png" alt="控制台注册"> 
</div>  
这是创建条件的方法：  
<div align=center><img src="/pic/API/foodlevelconditioncommand.png" alt="FoodLevel条件命令"> 
</div>  
还有事件：  
<div align=center><img src="/pic/API/foodlevelactioncommand.png" alt="FoodLevel事件命令"> 
</div>  
你还可以通过```/qa actions edit actionname4 execute```命令执行：  
<div align=center><img src="/pic/API/actionexecuted.png" alt="事件执行效果"> 
</div>  
For many simple values you can use the variable system. Not only is it easier, it also gives you access to the advanced comparison operators (like being able to use Math and other variables in the expression for Integer variables).  

# 创建一个目标
Create the class called ```TakeDamageObjective``` and make it extend ```Objective``` . Then implement everything. It should look like this:  

```
public class TakeDamageObjective extends Objective {
    private final NotQuests main;

    public TakeDamageObjective(NotQuests main) {
        super(main);
        this.main = main;
    }

    @Override
    public String getObjectiveTaskDescription(QuestPlayer questPlayer) {
        return null;
    }

    @Override
    public void save(FileConfiguration fileConfiguration, String initialPath) {

    }

    @Override
    public void load(FileConfiguration fileConfiguration, String initialPath) {

    }

    @Override
    public void onObjectiveUnlock(ActiveObjective activeObjective, boolean unlockedDuringPluginStartupQuestLoadingProcess) {

    }

    @Override
    public void onObjectiveCompleteOrLock(ActiveObjective activeObjective, boolean lockedOrCompletedDuringPluginStartupQuestLoadingProcess, boolean completed) {

    }
}
```  
Let's already register it in our onEnable in our Main:  

```
@Override
public void onEnable() {
    // Plugin startup logic
    notQuestsInstance = NotQuests.getInstance();
    if(notQuestsInstance != null){ //For Spigot compatibility
        notQuestsInstance.getVariablesManager().registerVariable("FoodLevel", FoodLevelVariable.class);
        notQuestsInstance.getObjectiveManager().registerObjective("TakeDamage", TakeDamageObjective.class);
    }
}
```

Now back to our ```TakeDamageObjective``` , just fill out each method. You can see how other Objectives do it [here](https://github.com/AlessioGr/NotQuests/tree/main/paper/src/main/java/rocks/gravili/notquests/paper/structs/objectives).

Then, you'll need to register and handle your own Bukkit events to add Progress (and eventually complete) your objective. For the internal objectives, I'm doing that [here](https://github.com/AlessioGr/NotQuests/blob/main/paper/src/main/java/rocks/gravili/notquests/paper/events/QuestEvents.java). Feel free to copy the boilerplate code.

I'll add a more explanatory tutorial on Objective Creation later, feel free to ask for help on our Discord. You can find the API example project [on GitHub](https://github.com/AlessioGr/NotQuestsAPIExample). Not that it might not have been updated to the latest NotQuests API yet.