# flutter项目的资产映射器
### 版本：PYTHON 3.9

## 开发背景：
&nbsp;&nbsp;&nbsp;在您的flutter app中是否会使用大量的素材，包括图片、音频、语言文件等，根据官网的方式，这些文件您至少需要执行一下操作：
1. 将资产文件放到一个固定的目录下，例如项目的根目录/assets。
2. 在pubspec.yaml 的assets中列出所有需要使用的文件相对路径例如下面这样。
flutter:
  assets:
  - assets/images/old-password.png
  - assets/images/search.png
  - assets/images/battery-cell.png
  - assets/images/plant-filled.png
  - assets/images/me-filled.png
  ...
3. 在代码中使用相同的相同的路径来引用这些文件。
以上为在flutter app中访问资产文件的完整方式，有经验的开发者应该能体会到这里的痛点：
- 当有大量资产文件需要映射时，您可能会原地崩溃。
- 路径非常容易错，错误不易发现。
- 文件与pubspec.yaml定义很难保持一致。
基于以上原因，由此开发了assets_mapper程序

# 使用方式
  assets_mapper基于python编写，因此python运行环境必不可少；完成后只需要在flutter项目根目录中新建assets后，并在项目根目录运行assets_mapper即可自动完成资源文件的映射。这个过程通常很快。完成后没有任何输出则说明程序执行成功；此时我们可以看到在lib目录下生成了assets.dart文件，该文件中定义了一个Ast类；接下来，我们访问文件的方式就由纯字符串的路径变为了带自动补全的类访问方式了，哈哈；打开该文件我们可以看到所有的路径已经被定义为字段了，并且我们可以通过和目录结构相同的调用结果去访问指定资源了。
  
# 使用示例：
  assets/img/logo.png
  现在`Ast.img.LOGO`

我们发现这里的文件名都转为大写了，其实这是定义常量的标准写法；并且不止转大写任何特殊字符都会转为下划线（_)，因此为了更规范，我们遵循一下原则：
1. 使用统一的风格符作为文件分割符，例如-_等
2. 不要使用重复的文件名（后缀不同但前缀一致），因为为了保证使用方便，省去了后缀的声明；
