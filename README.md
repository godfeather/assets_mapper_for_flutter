# flutter项目的资产映射器
### 版本：PYTHON 3.9

flutter资产映射器用于自动在pubspec.yaml文件中定义资产列表并且生成对应的类方便代码层面的调用。
脚本运行将在./lib下生成assets.dart文件，该文件中定义了所有资产（assets/文件夹下的所有资源）的常量；并且设计为通过和目录结构类似的层级进行调用；这类似于安卓开发中的R.java文件；通过访问该文件我们不再需要使用纯字符串访问资产，这可以大大降低错误率；
## 系统配置：
  与其他python 程序一样，使用python 常规的方法执行即可。Linux/Unix系统可以赋予该脚本可执行权限后通过`./assets_mapper`在脚本文件的目录中执行；或者将该脚本的路径配置到环境变量*PATH*中后在任何地方输入`assets_mapper`执行\[推荐\];命令的执行应该在flutter根目录中
  Windows中可以安装python 环境后在命令行中执行;
 

### 详细逻辑：
  1. 首先,程序运行会递归扫描当前目录下的./assets目录中的所有文件，同时新建assets.dart文件；并在其中建立类和成员变量
  2. 在assets的扫描过程中，文件夹名称会首字母大写并增加下划线（Ast类除外)后作为类名, 因此文件名称的定义必须在类名允许的正确范围内; 其下的文件被定义为String类型并包含资产访问字符串（路径）；
  3. 子文件夹的表示方式为：在父类中定义该子类类型的常量（final)；所有的目的只有一个，那就是让调用看起来和目录结构一致(因为dart不支持内部类，所以)；比如访问images下的background.png文件；调用方式则为Ast.images.BANKGROUND;
  4. 更新pubspec.yaml文件中的flutter.assets节点的资源列表
  5. everything's done;
