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
只需一条命令即可更新资产文件的自动管理自动映射。
