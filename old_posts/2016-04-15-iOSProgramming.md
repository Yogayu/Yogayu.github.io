---
layout:     post
title:      "iOS Programming Reading Notes"
date:       2016-04-15 20:40:54
author:     "Youxinyu"
categories:    tech
header-mask: 0.1
header-img: "img/home-bg-2.jpg"
catalog:    true
tags:
    - iOS
    - Tech
    - Books
---

iOS 8 Programming Fundamental with Swift

# Part 2 IDE

## Chapter 6. Anatomy of an Xcode Project

## 从项目到可运行的App
App文件其实就是一个特殊的叫作*package*的文件夹。
假设应用名为Empty Window
![package](/img/package.png)

Empty window: 编译的文件。
Main.Storyboard:Storyboard 文件，a bundle of nibs files.按需加载。
Info.list : 配置文件。
Frameworks: 需添加的框架。
PkgInfo: 历史遗留物。
## Build Settings
属性列表文件就是一系列的键对值。

- 修改Info.plist文件 Editor->Show raw values.

## Nib Files
一个Nib文件是一部分用户界面描述，它以已编译的格式包含在一个以*.nib结尾*的文件里。

它是在编译过程中由`.xib`文件生成的,相应的，包含多个nib文件的`.storyboardc`由
`.storyboard`文件生成。

## Code File and App Launch Process

### The entry point

写过C语言的都知道，程序进入开始执行的地方是main函数。同样的在Objective-C中也是。

	int main(int argh, char *argv[]) {
	        @autoreleasepool {
	            return UIApplicationMain(argh, argue, nil,
	                NSStringFromClass([AppDelegate class]));
	} } 

做了两件事情:

- 设置了内存管理环境
- 调用了UIApplicationMain函数

但在swift中你找不到main函数：

	@UIApplicationMain
	class AppDelegate: UIResponder, UIApplicationDelegate {...}


上面的@UIApplicationMain属性，就实现了main函数的功能。你也可以自定义，新建main.swift(必须以main命名)，在其中写：

	import UIKit
    UIApplicationMain(
        Process.argc, Process.unsafeArgv, nil, NSStringFromClass(AppDelegate))

### UIApplicationMain

其实你的App不过就是对单个巨大的UIApplictionMain函数的调用。（想一想C语言中main函数的调用执行）

UIApplicationMain主要做的事：

1. 创建你app的第一个实例——共享应用实例(the shared application instance)。之后，你可以很容易的通过调用UIApplication.sharedApplication()得到该实例。UIApplicationMain调用的第三个参数，指定了应该实例化哪一个共享应用实例。默认是nil，如果你想使用一个自己写的子类，就可以改为NSStringFromClass(MyUIApplicationSubclass)（MyUIApplicationSubclass是你自己的子类名）。
2. 创建你的第二个实例—— 应用实例的代理(delegate)。同理，它对应第四个参数。
3. 如果Info.list指定了一个主故事板文件(main storyboard file)，UIApplicationMain就会加载并查找它的初始视图控制器(initial view controller)。UIApplicationMain会实例化该视图控制器。
4. 如果有一个主故事板文件，UIApplicationMain就会开始创建窗口(`Window`)。它是你app的第四个实例，是UIWindows的实例。赋给应用代理的window属性，初始化视图控制器赋给窗口实例（window instance）的rootViewController属性。
5. UIApplicationMain转向app delegate instance并开始调用其中的代码。终于，你可以在其中写自己的代码了。但是，最好只做一些**不费时**的初始化工作，因为这个时候应用的界面还没有显示。
6. 如果有一个主故事板，UIApplicationMain现在回让它显示出来了。它通过调用UIWindow实例中的`makeKeyandVisible`方法来实现。
7. 现在窗口马上就会显示了。


如果没有指定一个主故事板，你也可以自己写：

		class AppDelegate: UIResponder, UIApplicationDelegate {
		    var window: UIWindow?
		
		    // look, ma, no storyboard!
		    fun application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {
		        self.window = UIWindow()
		        self.window!.backgroundColor = UIColor.whiteColor()
		        self.window!.rootViewController =
		            MyViewController(nibName:"MyViewController", bundle:nil)
		        self.window!.makeKeyAndVisible()
		        return true
		    }
		}

`framework`:已编译的代码库。
对设备系统framework子集的复制叫做`SDK`(software development kit)。

链接(`Linking`)是将你的已编译代码与所需框架挂钩的过程。

Swift使用Modules。Modules会自动编译。
Modules是缓存信息，存放在Library/Developer/Xcode/DrivedData/ModulesCache.它精巧而方便，但也有缺点，你无法确切的指定自己使用了哪些框架。响应的头文件也不会在导航中显示。

有些情况下你也需要手动添加框架：
![linking](/img/linking.png)


---

## Cocoa

在进行iOS编程时，多数情况下是在与Cocoa进行交互。
Cocoa是一个很庞大的库，它分为了几个小库。



## Subclassing

Cocoa会提供给你一些可以直接使用的对象，比如UIButton。有时候，你会想要自定义这些对象。在对其继承之前，最好查一查，可不可以直接进行更改。比如UIButton就可以更改其标题，背景图片等。

但是，不管怎样，你都有更改属性和方法还是不能满足的时候。这种时候，Cocoa会提供给你一些方法可以进行子类化(subclassing)和重载。

比如UIView，你继承UIView之后，可以对drawRect进行重载，绘制自定义视图。

但是，继承是你在和cocoa交互时，极少会使用到的方式。知道什么时候使用继承是需要技巧的，但是更通用的规则是，如果不是确切的知道该继承，你最好不要使用它。

不使用继承的一个重要原因是，大多数自带的Cocoa类使用委托(delegation)来自定义行为(方法)。

(纯粹看理论会没有实际认知，需要编码去理解。
知识编码却会陷入似懂非懂的状态，需要整合理论去理解。)

## Categories and Extensions
OC中Categories指直接在已存在的类上添加方法，Swift中叫作Extensions。
### Swift中如何使用extension？
例子，Array<T>，多使用extension加少量的protocol。多个extension，把函数体分为多个部分不不是全部在一起，这样使得代码更容易被理解，同时相关联的函数也聚集在一起。
eg. Core Graphic
### 你如何使用extension？
在已存在的对象类型中添加函数。
而且它使用于Swift三种类型对象，比如enum和struct不能继承却可以extension。
一次改变，处处改变。

会在不同的头文件中都有categories的声明，但文档之间没有链接，这也许是cocoa框架结构的问题之一吧。

## Document
- Inherits from 继承自何处，不断的向上查看父类，以寻找到你需要的信息。
- Conforms to 这怎么翻译，不断的查看其实现的协议(Protocal),以寻找到你需要的信息。
- Framework  看该类属于哪个框架，在使用时，需要将框架import你的代码中。
- Availability   在什么版本开始可以使用。
- Declared in  类被声明在哪一个头文件中。
- Related document 相关文档，提高给你有用的信息，比如代码示例。orient your thinking and provide you optionals
- Sample code 下一章具体介绍
- Body

