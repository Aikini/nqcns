# 💻 API使用方法<!-- {docsify-ignore-all} -->
# 添加API到你的项目中
## Gradle Kotlin DSL（推荐）
添加这个到你的build.gradle：  
```
repositories{
    maven {
        url = "https://maven.pkg.github.com/alessiogr/NotQuests"
        content{
            includeGroup("rocks.gravili.notquests")
        }
        credentials {
            username = System.getenv("GITHUB_PACKAGES_USERID") ?: "alessiogr"
            password = System.getenv("GITHUB_PACKAGES_IMPORT_TOKEN") ?: "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"
        }
    }
}

dependencies {
    compileOnly 'rocks.gravili.notquests:paper:5.17.1'
}
```
注意：请确保你使用的是最新版本的API。  
注意：上述所写的Github Packages令牌将不再起作用。因为每次我重新搞一个令牌Github都会撤销掉它。你可以自己在Github上生成自己的令牌并使用它，或是直接将NotQuests jar添加到你的项目中。  
完成！如果你想用自己的Github用户ID或是令牌，请随意。  

# Paper和Spigot模块
安装完API后，你会发现，我们有两个几乎相同的模块：Paper和Spigot。请使用Paper模块，而不是Spigot。这里的Spigot模块仅仅是为了遵守spigot.org资源指南而存在，一旦spigot.org噶了就会被删除，且由Hangar替代。  
我将不再会Spigot模块进行任何维护和更新，请使用Paper模块。  
为什么？  
因为Spigot API很古老，并且还使用着很多早就被遗弃的上古时期的特性。NotQuests可是一个想要跟上时代的插件，使用着现代化的API特性，Spigot不仅没有还拒绝添加。（更重要的一点是连Kyori components，甚至是Bukkit.getTPS()这样简单的东西都没有）

# 使用API
首先，将```NotQuests```在你的plugin.yml文件中添加为```depend:```或是```softdepend:```。  
然后，使用```NotQuests.getInstance()```访问实例（使用Paper模块的NotQuests），而后根据需要进行操作。😄  
请确保在NotQuests.getInstance()为空时禁用你的NotQuests integration。由于你希望使用的是Paper模块，它在Spigot服务器上会返回空值。  

# 注册你自己的目标
你可以轻松地将目标添加到NotQuests中（直接添加或通过API），示例：  
```NotQuests.getInstance().getObjectiveManager().registerObjective("jumpobjective", JumpObjective.class);```  
使用JumpObjective继承“Objective”，与其它目标类相似。只需复制结构即可。