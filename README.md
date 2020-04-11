# game-hot-update
Java游戏服务器热更例子。此热更新方法采用启用后更新。即游戏服务器在运行中如果出现bug,采用pid绑定的方式更新。此更新方法只允许更新方法体内的代码。比如一个类某个方法有bug，在方法体内修改完之后可以热更，但是如果新的类中添加了新的字段，新的方法或者父类发生变化了，是不行的。不过大部我们的bug都是方法内的逻辑bug,使用此方法还是可以的。

windows上面用ideal调试的时候，里面需要设置为绝对路径，不然会提示找不到 jar或者 class文件

操作步骤：
0. 需要安装JDK 1.8 ，因为里面用了 lib/tools.jar , JDK 1.9之后的版本删除了 lib/tools.jar 
1. 打开IntelliJ ，加载maven project file pom.xml build project
2. cp .\LoadAgent\target\LoadAgent-0.0.1-SNAPSHOT.jar .\GameServer\config\
3. 运行 GameServerMain.java
4. 将GameServerMain的pid 替换到 HotUpdateMain.java 的15行 pid = "123", recompile file
5. 将TestHot.java 里面的 输出改一下， recompile file
6. 运行 HotUpdateMain.java 即可看到热更成功的输出
