# Flutter从入门到实战
![Mon icon](https://github.com/Terrybthvi/my_flutter_app/blob/master/ezgif.com-video-to-gif.gif)
## Flutter概述
　　Flutter是一款移动应用程序SDK，一份代码可以同时生成iOS和Android两个高性能、高保真的应用程序。
　　Flutter目标是使开发人员能够交付在不同平台上都感觉自然流畅的高性能应用程序。我们兼容滚动行为、排版、图标等方面的差异。
　　无需移动开发经验即可开始使用。应用程序是用Dart语言编写的，如果您使用过Java或JavaScript之类的语言，则该应用程序看起来很熟悉。使用面向对象语言的经验绝对有帮助，但一些Flutter应用程序甚至是没有编程经验的人写的！
## Flutter的优势
* 提高开发效率
  * 同一份代码开发iOS和Android
  * 用更少的代码做更多的事情
  * 轻松迭代
    * 在应用程序运行时更改代码并重新加载（通过热重载）
    * 修复崩溃并继续从应用程序停止的地方进行调试
* 创建美观，高度定制的用户体验
  * 受益于使用Flutter框架提供的丰富的Material Design和Cupertino（iOS风格）的widget
  * 实现定制、美观、品牌驱动的设计，而不受原生控件的限制
## Flutter环境搭建
　　Flutter可以在Windows、MacOS、Linux操作系统都可以安装，本文主要以MacOS为例。
### Flutter 安装
#### １、获取Flutter SDK
1、首先，点击下面的链接下载flutter SDK
* [flutter_macos_v0.4.4-beta.zip](https://storage.googleapis.com/flutter_infra/releases/beta/macos/flutter_macos_v0.4.4-beta.zip)

2、将下载的flutter解压到指定目录，在终端执行下面命令

    $ cd ~/development
    $ unzip ~/Downloads/flutter_macos_v0.4.4-beta.zip

3、添加flutter到环境变量
   在终端执行第一句，打开配置文件，然后在末尾加上flutter的环境变量，然后再编译配置文件使之生效。

    $ open -e .bash_profile
    $ export PATH=`pwd`/flutter/bin:$PATH
    $ source .bash_profile

#### ２、设置IOS
##### １、安装Xcode
1、通过App Store下载安装Xcode 9.0以后的版本。
２、配置Xcode命令行工具以使用新安装的Xcode版本 `sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer`
3、确保Xcode许可协议是通过打开一次Xcode或通过命令`sudo xcodebuild -license`同意过了。
使用Xcode，您可以在iOS设备或模拟器上运行Flutter应用程序。
##### 2、设置IOS 模拟器
如果要在IOS模拟器上测试程序，请按一下步骤：
１、在终端输入命令打开模拟器 `open -a Simulator`
2、检查模拟器中的设置，确认模拟器是64位版本并且不低于Iphone5s
３、根据您的开发机器的屏幕大小，模拟的高清屏iOS设备可能会使您的屏幕溢出。在模拟器的 Window> Scale 菜单下设置设备比例
4、运行`flutter run`启动您的应用。
##### ３、安装到IOS 设备
要将您的Flutter应用安装到iOS真机设备，您需要一些额外的工具和一个Apple帐户，您还需要在Xcode中进行设置。
1、安装 [homebrew](https://brew.sh/) （如果已经安装了brew,跳过此步骤）。
2、打开终端并运行这些命令来安装用于将Flutter应用安装到iOS设备的工具

    brew update
    brew install --HEAD libimobiledevice
    brew install ideviceinstaller ios-deploy cocoapods
    pod setup
如果这些命令中的任何一个失败并出现错误，请运行brew doctor并按照说明解决问题。
#### 3、安装Android Studio
至于安装Android Studio及相关环境变量的配置，这个就很简单了，这里就不做说明了。有一点就是在Android Studio安装完成之后要安装**Flutter插件**；步骤**Preference>plugins>Browes repositories** 搜索`Flutter` 安装并重启Android Studio，就OK了。
#### 检查Flutter环境配置
如果您做完了上述的所有准备工作，那么我们可以在终端运行一下命令检查环境是否OK。　　

    flutter doctor

如果出现下面的结果说明已全部安装完成

    [✓] Flutter (Channel beta, v0.4.4, on Mac OS X 10.13.4 17E202, locale zh-Hans-CN)
    [✓] Android toolchain - develop for Android devices (Android SDK 27.0.3)
    [✓] iOS toolchain - develop for iOS devices (Xcode 9.3.1)
    [✓] Android Studio (version 3.1)
    [✓] Connected devices (2 available)
    • No issues found!

##### 踩过的坑
###### Missing Xcode dependency: Python module "six".
如果有其他问题按照提示一步一步做就可以了。不过我遇到一个很坑的东西，就是明明已经安装了Python但是提示说`Missing Xcode dependency: Python module "six".`按照提示安装`sudo easy_install six`但是又提示已安装。找了好久最终在GitHub上找到解决办法，就是在终端执行下面的命令，在此附上链接[解决办法](https://github.com/flutter/flutter/issues/16428)

    $ python2.x -m pip install six by
    or
    $ brew reinstall python@2
    $ pip install six

##  Flutter实战
前面介绍了好多可能大家没啥概念，光说不练假把式，下面我们就来构建一个简单的Flutter工程。  
如果我们Android Studio 安装了Flutter插件，那么我们打开Android Studio 的时候会看到如下图所示有，第二行多了一个`start a new Flutter project`
![Mou icon](https://github.com/Terrybthvi/my_flutter_app/blob/master/9A0FBA3D-9D4E-4900-9CFD-8D5D02B3696D.png)  
点击我们创建一个新的Flutter程序  
![Mou icon](https://github.com/Terrybthvi/my_flutter_app/blob/master/CF5EF84A-2502-461F-8379-7FECDC1FBA92.png)  
![Mou icon](https://github.com/Terrybthvi/my_flutter_app/blob/master/8B259C1A-1E42-4C18-98E0-506960B7E5FA.jpeg)  
我们创建完进入编辑界面后，我们可以看到主要有４块区域:  
１、工程文件目录.  
２、构建区域在这里可以选择，运行IOS Android 模拟器。
![Mou icon](https://github.com/Terrybthvi/my_flutter_app/blob/master/69FD643E-BEAA-4B22-8E2B-A8289807B1DE.png)
３、Flutter 程序当前页面的组件树，Flutter 程序的核心原则是`一切都是组件(Widget)`，所以他的所有都是组件。  
４、dart语法分析，我们通过前面的介绍知道，Flutter程序是通过dart语言来写的。

这样创建完成之后，我们会看到`lib`目录下有一个`main.dart`文件，这个就是源代码：

    import 'package:flutter/material.dart';
    
    void main() => runApp(new MyApp());
    
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return new MaterialApp(
          title: 'Flutter Demo',
          theme: new ThemeData(
        
            primarySwatch: Colors.blue,
          ),
          home: new MyHomePage(title: 'Flutter Demo Home Page'),
        );
      }
    }
    
    class MyHomePage extends StatefulWidget {
      MyHomePage({Key key, this.title}) : super(key: key);
    
      final String title;
    
      @override
      _MyHomePageState createState() => new _MyHomePageState();
    }
    
    class _MyHomePageState extends State<MyHomePage> {
      int _counter = 0;
    
      void _incrementCounter() {
        setState(() {
          _counter++;
        });
      }
    
      @override
      Widget build(BuildContext context) {
        return new Scaffold(
          appBar: new AppBar(
            title: new Text(widget.title),
          ),
          body: new Center(
            child: new Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: <Widget>[
                new Text(
                  'You have pushed the button this many times:',
                ),
                new Text(
                  '$_counter',
                  style: Theme.of(context).textTheme.display1,
                ),
              ],
            ),
          ),
          floatingActionButton: new FloatingActionButton(
            onPressed: _incrementCounter,
            tooltip: 'Increment',
            child: new Icon(Icons.add),
          ), 
        );
      }
    }
    
这段代码其实很简单，首先我们看到`main()`函数调用了`runAPP()`,这里简单说下
    
    runApp函数接受指定的控件(Widget)，并使其作为控件树(widget tree)的根控件。

runAPP的入参是下面定义的MyAPP,在MyAPP里面创建了`_MyHomePageState`的对象作为首页，我们可以看到下面`_MyHomePageState`里面定义了中间是两个个Text ，底部是一个floatingActionButton。关于dart的语法后续文章详细说明，这里就简单了解一下这个demo：就是点击一次下面的悬浮按钮，中间的数字会加１。
完了之后我们就可以运行，根据上面的介绍我们选择模拟器运行,如下图所示：  
![Mon icon](https://github.com/Terrybthvi/my_flutter_app/blob/master/ezgif.com-video-to-gif.gif)
## 小结
总的来说Flutter入门还是非常简单的，dart语法也比较容易上手，个人觉得是一项非常不错的技术。以上如有哪些写的不对的地方欢迎指正。最后附上几个Flutter学习的相关链接   
[flutter官网](https://flutter.io/setup-macos/)  
[flutter中文开发者论坛](http://flutter-dev.cn/)  
[dart中文社区](https://www.dart-china.org/)