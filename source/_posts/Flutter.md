



title: Flutter 系列教程

------



# Flutter



**如果你直接安装flutter就不需要安装dart了，因为flutter已经包含了dart环境了**

所以推荐直接安装flutter即可



## 安装dart

首先你需要先安装homebrew，homebrew是一个软件资源包管理工具

### 安装homebrew

#### 外网环境

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```



#### 推荐国内镜像

```
/bin/bash -c "$(curl -fsSL https://gitee.com/wejectchan/brew/raw/master/install.sh)"
```



### 安装dart

```dart
brew tap dart-lang/dart
brew install dart
```



## 安装Flutter

苹果电脑芯片有两种，一种是intel芯片（X86），一种是M系列芯片（Arm）

### 查看系统芯片

```
uname -a
```



**注意安装一定要根据系统芯片来安装**



具体查看

```
https://flutter.cn/docs/get-started/install/macos
```



#### **第一步先下载对应系统版本的压缩包**

##### Intel芯片

```
intel：https://storage.flutter-io.cn/flutter_infra_release/releases/stable/macos/flutter_macos_3.13.7-stable.zip
```



##### M系列芯片

```
https://storage.flutter-io.cn/flutter_infra_release/releases/stable/macos/flutter_macos_arm64_3.13.7-stable.zip
```



#### **第二步解压到某一个文件路径**

```
 cd ~/development
 unzip ~/Downloads/flutter_macos_3.13.7-stable.zip
```



#### **第三步配置环境变量**

```
export PATH="$PATH: 文件路径/flutter/bin"
```

这里需要注意，这样配置仅仅在当前命令窗生效，要永久生效则需要配置到shell文件中



##### **永久配置具体看这里**

```
https://flutter.cn/docs/get-started/install/macos#update-your-path
```

```
打开或者创建 shell 的 rc 文件，比如，在 Linux 和 macOS Mojave 或 Mojave 之前的系统里，是默认使用 Bash 的，所以需要修改 $HOME/.bashrc 文件。 macOS Catalina 操作系统默认使用 Z Shell，所以需要修改 $HOME/.zshrc 文件。请知晓，如果你使用不同的 shell，文件目录或文件名可能会有所不同。
```

```
老旧的版本
vim ~/.bash_profile 
或者open ~/.bash_profile


最新版的系统都使用zshrc 
vim ~/.zshrc 
或者open ~/.zshrc


export PATH="$PATH: 文件路径/flutter/bin"
source $HOME/.bash_profile 来刷新当前命令行窗口。
```

```
通过运行以下命令来验证 flutter/bin 文件夹是否已经添加到 PATH 环境变量中：
 echo $PATH
```

```
验证 flutter 命令是否可用，可以执行下面的命令检测：
which flutter
```



### 安装苹果模拟器

你只需要从应用商店下载Xcode进入之后会提示你下载模拟器，按要求下载即可



不过通常会下载失败，因为模拟器镜像在国外，如果你有苹果开发者帐号可以通过抓取下载链接的形式去进行直接下载



没有开发者帐号下载失败就多次重试，一般3到4次即可



## 开发工具

可以使用vscode或者Xcode（苹果）||Android Studio（安卓）





## 推荐使用VScode

使用vscode可以在扩展中搜索flutter相关扩展和dart，以便代码提示和自动导入文件



```
Dart

Flutter

Awesome Flutter Snippets
```





# 创建项目



如果你有Xcode或者Android Studio，直接创建Flutter项目即可



如果你是用vscode则需要使用命令行去进行创建

```
flutter create flutter02
code .
flutter run
flutter devices //使用真机运行
```



最重要的就是**lib文件夹**以及**pubspec.yaml**文件，平台文件一般不需要理会



我们编写代码都是在lib文件夹下进行编写



![image-20231012112958050](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20231012112958050.png)



# 使用第三方插件

  进入官方网站搜索插件（推荐使用加速器）：

```
https://pub.dev/
```

进入之后搜索所需插件的安装方式即可

**这里的重点是安装之后运行到模拟器这一步可能会出现cocospods安装失败甚至安装之后无法使用的问题。**



## cocospods安装问题

首先你需要安装`homebrew`，这里前面有教程不再赘述

第二步，检查ruby版本，输入命令`ruby -v`，这里m系列芯片的电脑默认是自带ruby的，但是版本过低，我们需要更新ruby

使用：

```
brew install ruby
```

默认会下载最新的版本

同时记得要去bash_profile编辑环境变量，否则可能会出现ruby系统版本没有改变的问题

```
export PATH=/opt/homebrew/opt/ruby@3.2/bin:$PATH
```

查看ruby安装路径，可以在`/opt/homebrew/opt`目录中查看

最关键的就是更新gem版本，这一步就会下载cocoapods

```
sudo gem update --system -n /usr/local/bin
```

可以通过查看命令判断cocoapods是否成功下载

```
gem list
```

如果出现cocoapods相关多个软件，说明安装成功

输入命令：判断是否安装成功，如果成功，只会返回版本号，否则都算不成功

```
pod --version
```

### 注意

如果输入pod --version出现报错，很可能是由于gem中的activeSupport版本有bug，这个时候你需要安装稳定版的activeSupport 7.0.8，有问题的版本就是7.1.0之后的版本

```
sudo gem install activesupport -v 7.0.8 
```

```
sudo gem uninstall activesupport -v 最新版
```

这样就可以使用第三方插件并运行在模拟器上面了。



# Flutter 教程系列

与其说是教程，不如说是讲**如何站在前端的角度**去看待Flutter框架，推荐安装`Getx`配合使用，Flutter是一款轻量级的框架，很多额外的功能都使用插件来配合完成。

GetX：

```
https://github.com/jonataslaw/getx/blob/master/README.zh-cn.md
```





所以，你可以像这样安装我的依赖

```
dependencies:
  fluttertoast: ^8.2.2
  get:
  dio: ^5.3.3
  webview_flutter: ^4.4.1
```



## 配置环境变量

```
FLUTTER_STORAGE_BASE_URL ：https://storage.flutter-io.cn
```

这样使用Flutter run命令可能会出现如下情况：

`Flutter assets will be downloaded from https://storage.flutter-io.cn. Make sure you trust this source!`

无需理会！

### 配置安卓gradle环境

第一处：

```
buildscript {
    ext.kotlin_version = '1.7.10'
    repositories {
    	//看这里
        // google()
        // mavenCentral()
        maven { url 'https://maven.aliyun.com/repository/public' }
        maven { url 'https://maven.aliyun.com/repository/google' }
        // maven { url 'http://maven.aliyun.com/nexus/content/groups/public'}
        maven { url 'https://maven.aliyun.com/repository/gradle-plugin'} 
    }

    dependencies {
        classpath 'com.android.tools.build:gradle:7.3.0'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}
```

第二处：

```
allprojects {
    repositories {
    //看这里
        // google()
        // mavenCentral()
        maven { url 'https://maven.aliyun.com/repository/google' }
        maven { url 'https://maven.aliyun.com/repository/public' }
        // maven { url 'http://maven.aliyun.com/nexus/content/groups/public'}
        maven { url 'https://maven.aliyun.com/repository/gradle-plugin'}
    }
}
```

### 配置苹果环境变量

```
open ~/.bash_profile

export path：flutter安装路径：PATH
```

## 路由

原生Flutter有自己的路由方式

### 跳转到下一个页面

#### **第一种方式：（要传递参数直接放入即可）**

```
Navigator.of(context).push(MaterialPageRoute(builder: (context) {
      //跳转并传参
      return const SearchPage(
         title: '你好',
        );
      }))
```

#### **第二种方式：通过路由名称,也可以传递参数**

```
Navigator.of(context).pushNamed("/pagebuilder",arguments: {})
```

注意，这种方式需要提前定义好**路由栈**和**初始化路由**

在main.dart中进行定义：

```
class MyApp extends StatelessWidget {
  MyApp({super.key});


  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "Flutter Demo",
      //初始化路由
      initialRoute: "/",
      //定义路由栈
       routes: router(context),
    );
  }
}

router(context) {
  return {
    "/pageanmation": (context) => const MyAnmationList(),
    "/pagefull": (context) => const PageFullDemo(),
    "/pagebuilder": (context) => const PageBuilderDemo(),
    "/pageview": (context) => const MyPageView(),
    "/dialog": (context) => const DialogPage(),
    "/login": (context) => const LoginPage(),
    "/register": (context) => const RegisterPage(),
    "/search": (context) => const SearchPage(),
    "/": (context) => const MyTabs(),
    "/categroy": (context) => const CatrgroyPage()
  };
}

```



#### **第三种方式:推荐使用Getx**

Getx拥有强大的统一的路由管理：

```
 Get.toNamed("/search?hello=11111", arguments: {"msg": "hello"});
 
 Get.to(NextScreen());
```

在main.dart中这样配置：

`getPages`引入路由文件，使用`GetMaterialApp`强化MaterialApp

```
//引入路由
import './router/index.dart';

class MyApp extends StatelessWidget {
  MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return GetMaterialApp(
      //去除debug
      debugShowCheckedModeBanner: false,
      title: "Flutter Demo",
      //初始化路由
      initialRoute: "/",
      // 以后统一使用这种方式去管理路由
      getPages: AppPage.routes,
    );
  }
}
```

新建一个router文件夹统一管理

```
import 'package:get/get.dart';
//导入页面
import '../page/tabs.dart';
import '../page/search.dart';
import '../page/tabs/categroy.dart';
import '../page/login.dart';
import '../page/register.dart';
import '../page/dialogdemo.dart';
import '../page/pageviewdemo.dart';
import '../page/pageviewbuilder.dart';
import '../page/pageFulldemo.dart';
import '../page/anmationListDemo.dart';
import '../page/getxstatedemo.dart';
import '../page/inputdemo.dart';
import '../page/webviewdemo.dart';
import '../page/i18ndemo.dart';
//引入中间件
import 'middleware/shopMiddleware.dart';

class AppPage {
  static final routes = [
    GetPage(
      name: "/",
      page: () => const MyTabs(),
      transition: Transition.leftToRight, //设置单个页面跳转的方式
      // middlewares: [MiddlePageVC()],//设置中间件(GetPage),可以根据优先级设置多个中间件
    ),
    GetPage(
        name: "/pagefull",
        page: () => const PageFullDemo(),
        transition: Transition.rightToLeft, //设置单个页面跳转的方式
        middlewares: [shopMiddleware()]), //设置中间件(GetPage),可以根据优先级设置多个中间件
    GetPage(
        name: "/pageanmation",
        page: () => const MyAnmationList(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/pagebuilder",
        page: () => const PageBuilderDemo(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/pageview",
        page: () => const MyPageView(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/dialog",
        page: () => const DialogPage(),
        transition: Transition.rightToLeft //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/login",
        page: () => const LoginPage(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/register",
        page: () => const RegisterPage(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/search",
        page: () => const SearchPage(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/categroy",
        page: () => const CatrgroyPage(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/mygetx",
        page: () => MyGetXState(),
        transition: Transition.leftToRight //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/myinput",
        page: () => MyInputPage(),
        transition: Transition.rightToLeft //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/mywebview",
        page: () => const MyWebviewPage(),
        transition: Transition.rightToLeft //设置单个页面跳转的方式
        ),
    GetPage(
        name: "/myi18n",
        page: () => const MyI18NPage(),
        transition: Transition.rightToLeft //设置单个页面跳转的方式
        ),
  ];
}


```

最重要的是它可以每一个页面不同的跳转动画和方式以及中间件，非常适合企业级业务需求，例如跳转登录。

```
import 'package:flutter/material.dart';
import 'package:get/get.dart';
import 'package:flutter/cupertino.dart';

class shopMiddleware extends GetMiddleware {
  @override
  RouteSettings? redirect(String? route) {
    print(route);
    // return null;
    //没有权限跳转到登录页面
    return const RouteSettings(name: "/login", arguments: {"msg": "你还未登录！"});
  }
}

```



### 获取数据

**如果你使用Getx**

```
Get.arguments
```

```
Get.parameters
```

**如果不使用Getx，你需要提前定义对应的变量，注意把const移除掉，因为你已经不属于一个静态页面了**

```
final String title;

  SearchPage({Key? key, required this.title}) : super(key: key);
  
  
  //使用
  (title: Text(widget.title)
```



### 返回上一个页面

#### 第一种方式

```
Navigator.pop(context)
```

#### 第二种方式

```
Navigator.of(context).pop("好的");

//直接跳转到message页面，这种跳转方式相当于redirect，会删除前面一个页面
Navigator.of(context).pushAndRemoveUntil(
     MaterialPageRoute(builder: (context) {
                  return const MessagePage();
                }), (route) => false);
                
//使用替换路由跳转，相当于干掉前一个页面
Navigator.of(context).pushReplacementNamed("/home")
```



#### 第三种方式（Getx推荐）

要关闭snackbars, dialogs, bottomsheets或任何你通常会用Navigator.pop(context)关闭的东西。

```
Get.back();
```

进入下一个页面，但**没有返回上一个页面的选项**（用于闪屏页，登录页面等）。

```
Get.off(NextScreen());
```

进入下一个页面并**取消之前的所有路由**（在购物车、投票和测试中很有用）

如果你熟悉uniapp的话，这个相当于redirect

```
Get.offAll(NextScreen());
```



## 状态管理

**注意：这里仅仅站在前端的角度去做**



这里仅使用Getx进行状态管理，如果你熟悉前端的话，这一步相当于vue的vuex，react的redux。

新建一个store文件夹

index.dart，这是一个统一管理所有状态的文件，

Get.put方法运行放入一个控制器，这个控制器你可以把它当成一个全局的公共变量，放入之后Getx会进行内部的管理和追踪

```
//类似于vuex

import 'package:get/get.dart';

import './user.dart';

//统一管理所有的store
class Store {
  static final Store _instance = Store._internal();

  factory Store() {
    return _instance;
  }
  //将所有的store都放入这里
  Store._internal() {
    Get.put(UserController());
  }
}

```

通过继承GetxController使其变成一个可以追踪的控制器，并暴露出**响应式变量和函数**，这一步相当于暴露出所有的**state**，函数就是用来改变state的函数，相当于**mutation**

```
import 'package:get/get.dart';

class UserController extends GetxController {
  //这里定义变量
  RxInt count = 0.obs;

  //重置函数
  void reset() {
    count.value = 0;
  }

  //这里定义函数
  void increment() {
    count.value++;
  }
}

```

最后，在main.dart进行引入

```
import './store/index.dart';

void main() {
  Store(); // 初始化Store实例
  runApp(MyApp());
}

```

这样，你就可以在App所有的页面拿到这些数据了，如何获取呢，

既然有put的操作，就有find的操作

Get.find函数非常强大，他能找到对应的控制器



```
  final UserController userController = Get.find<UserController>();
```

所有的数据就在userController中：



注意：为了改变数据能够响应式的变化布局，因此，你需要使用Obx函数对响应式数据进行追踪，相当于**前端的观察者模式**

```
import 'package:flutter/material.dart';
import 'package:get/get.dart';

import '../../store/user.dart';

class CatrgroyPage extends StatefulWidget {
  const CatrgroyPage({super.key});

  @override
  State<CatrgroyPage> createState() => _CatrgroyPageState();
}

class _CatrgroyPageState extends State<CatrgroyPage> {
  //通过Get.find获取同一个控制器实例，可以使用数据,注意，只有先put控制器，才能find，否则会报错
  final UserController userController = Get.find<UserController>();

  @override
  Widget build(BuildContext context) {
    return Center(
      child: Column(children: [
        Obx(() => Text('分类当前store里面的数值: ${userController.count.value}')),
        ElevatedButton(
            onPressed: () {
              //不建议这么改，这样会导致数据的改变无法追踪，尽量调用方法去使用
              // userfind.count.value = 10;
              //建议这么修改
              userController.reset();
            },
            child: const Text("重置"))
      ]),
    );
  }
}

```



看到这里，如果你是一名前端，你可以简单的把它理解成，通过定义一个函数，把函数放入Getx（put）中，Getx就可以自动帮你管理，要使用就拿出来（find），同时数据的改变要引起页面的重新渲染，需要使用观察者（Obx）通知Getx对页面进行改变，是不是有vue的双向绑定的意思了。



**如果你不使用Getx，但是你的数据改变没有引起页面的变化，你需要看看是否使用了setState函数，这跟React的思路是一样的，如果你了解React，你就明白什么意思了。**



## Webview

这里使用Webiew_Flutter插件来实现，这是官方提供的webview插件

这里仅使用于安卓或苹果移动端设备，不适用于web

### 下载依赖

```
 webview_flutter: ^4.4.1
```

### 开启权限

安卓需要开启网络权限，默认是开启的

苹果需要配置ios/Runner/info.plist文件，加上这个

```
	<!-- 使ios运行运行webview -->
 	<key>io.flutter.embedded_views_preview</key>
    <string>YES</string>
```

### 使用

**第一步，先声明一个weviewController**

```
  late WebViewController controller;
```

**第二步，在 initState 中初始化 controller**

```
  void initState() {
    //第二步，在 initState 中初始化 controller
    controller = WebViewController()
	      //默认是不开启的，手动开启支持js
      ..setJavaScriptMode(JavaScriptMode.unrestricted)
     ..loadRequest(Uri.parse('https://www.csdn.net/'), headers: {})
    super.initState();
  }
```

**第三步，使用WebViewWidget,使用sizebox可以控制大小**

```
        SizedBox(
            height: 400,
            child: WebViewWidget(
                //控制器
                controller: controller,
   )),
```

这样就大功告成了，你就可以在页面上面看到webview页面了



手势操作，在WebViewWidget配置第二个参数

```
                //手势操作
                gestureRecognizers: {
                  Factory<VerticalDragGestureRecognizer>(
                    () {
                      return VerticalDragGestureRecognizer()
                        ..onStart = (DragStartDetails details) {
                          print("start");
                        }
                        ..onDown = (DragDownDetails details) {
                          print("down: $details");
                        };
                    },
                  )
                }
```



设置UA

```
 ..setUserAgent(
          // "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/94.0.4606.81 Safari/537.36"
          "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36")
```



路由操作：这个非常种要，可以追踪链接变化，注入JS，拦截等操作

```
      ..setNavigationDelegate(NavigationDelegate(
        //   //页面开始请求,获取页面请求
        onNavigationRequest: (requset) {
          print("页面请求参数 ${requset.url}");
          return NavigationDecision.navigate;
        },
        //   //页面开始加载
        //   onPageStarted: (url) {},
        //页面加载完毕,注入js,既使 WebView 加载的页面中可能还有链接，跳到另一个地址，js 注入的代码依然有效！
        onPageFinished: (url) async {
          var cookie = await controller
              .runJavaScriptReturningResult('document.cookie') as String;

          var ua = await controller
              .runJavaScriptReturningResult('navigator.userAgent;') as String;
          print("当前页面的cookie：$cookie,当前的ua是 $ua");
        },
        //   //加载错误
        //   onWebResourceError: (error) {
        //     print(error);
        //   },
      ));
```



## 国际化



使用Getx进行国际化配置非常简单，这里站在前端角度去进行配置



建立一个i18n文件夹，统一管理在index

```
import 'package:get/get.dart';
import './zh_CN.dart';
import './en_US.dart';

class Messages extends Translations {
  @override
  Map<String, Map<String, String>> get keys => {
        ...ZhCN().keys,
        ...EnUS().keys,
      };
}

```

en_US

```
import 'package:get/get.dart';

class EnUS extends Translations {
  @override
  Map<String, Map<String, String>> get keys => {
        'en_US': {
          'hello': 'hello world',
        },
      };
}

```

zh_CN

```
import 'package:get/get.dart';

class ZhCN extends Translations {
  @override
  Map<String, Map<String, String>> get keys => {
        'zh_CN': {
          'hello': '你好 世界',
        },
      };
}

```

在main.dart进行配置

```
 import 'i18n/index.dart';
 
 
 @override
  Widget build(BuildContext context) {
    return GetMaterialApp(
      //去除debug
      debugShowCheckedModeBanner: false,
      title: "Flutter Demo",
      //初始化路由
      initialRoute: "/",
      //命名路由
      // routes: router(context),
      // 以后统一使用这种方式去管理路由
      getPages: AppPage.routes,
      translations: Messages(), // 你的翻译
      locale: Locale('zh', 'CN'), // 将会按照此处指定的语言翻译
      fallbackLocale: Locale('en', 'US'), // 添加一个回调语言选项，以备上面指定的语言翻译不存在
      // locale: ui.window.locale,  //读取系统语言
    );
  }
```

使用：

```
 Text('hello'.tr)
```



改变语言

```
 Get.updateLocale(Locale('en', 'US'))；
 Get.updateLocale(Locale('zh', 'CN'));
```



非常简单，这样，你只需要在不同地区配置不同文件即可。



## 样式和布局

样式和布局可以查看我项目代码中的demo，每一个样式文件都有命名标识，如果要运行查看，直接复制替换到main.dart进行运行查看即可，这里不多赘述，样式和布局多敲就可以。



或者运行项目，点击查看对应的效果，结合代码进行查看。



## 网络Api



具体可以看我代码中的api部分



# 真机测试

## 安卓机型

如果你使用安卓设备进行测试的话，仅需要开启`开发者模式`并将手机连接到电脑设备上选择传输文件即可

## 苹果机型

如果你是iOS设备的话，请仔细看以下步骤：

**第一步，你需要描述文件和p12证书**，这两个东西你只能从开发者账号中去获取

双击打开p12证书，这时候系统会弹出弹窗，请输入证书密码，并将证书放入登录（在弹窗的右下角有选项）

第二步，打开Flutter项目，点击ios/Runner.xcworkspace文件，这个时候会自动打开Xcode，请你配置上对应的包名以及p12文件，没有出现红色警告说明配置成功，这个时候只需要点击左上角的运行命令即可。



第三步，后续就可以直接在vscode中运行即可，可以不需要在xcode中打开。



