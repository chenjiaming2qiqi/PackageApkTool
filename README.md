# PackageApkTool

## 项目介绍
PackageApkTool 为手游SDK联运系统打包系统核心模块，用于快速便捷的帮助游戏包打入渠道SDK资源生成游戏-渠道包，快速上架渠道上线。

致敬易接打包工具！！！


## 项目前提
使用该项目的前提条件是，游戏包体已经接入手游SDK框架Demo的SDK接口及申请好了对应的渠道参数信息。

* [手游SDK — 第一篇（序言）](https://www.jianshu.com/p/44e844ad7308)
* [手游SDK — 第二篇（SDK架构设计篇）](https://www.jianshu.com/p/0d27ee9f7f3a)
* [手游SDK — 第三篇（SDK架构设计代码实现篇（上）- 基础库）](https://www.jianshu.com/p/152fd3af1193)
* [手游SDK — 第四篇（SDK架构设计代码实现篇（下）- 项目需求开发）](https://www.jianshu.com/p/4d513b93dc3d)

及开源项目地址：
[手游SDK框架Demo](https://github.com/Bzaigege/GameSDKFrameDemo)

另外还需要安装好java和python环境。注意，当前项目时基于python2.7编写的，如果需要在python3环境中运行，需要自行修改适配部分代码

## 项目实现功能

* 实现游戏和渠道assets/libs/res/AndroidManifest.xml资源的动态合并
* 实现整体UI界面的可视化配置。
* 实现渠道资源的服务器下载功能。（注意：当前下载资源只是用于模拟下载功能，没有实际用途，需开发者自行配置）
* 支持渠道参数可视化差异性配置，及支持多种类型解析及修改，如xml/text/ini/pro/json等类型文件
* 支持游戏Icon和角标的可视化配置，及Icon和角标的合并
* 支持游戏闪屏可视化配置，及游戏闪屏和渠道闪屏逻辑兼容处理
* 支持游戏的包体输出路径，签名信息的可视化配置。
* 支持动态修改游戏的minSdk、TargetSdk、包名等配置
* 支持游戏第三方库多包名R文件资源引用配置,在渠道参数栏填写 R_package为字符数组["a","b"] 即可。
* 支持打包过程的日志信息显示及日志输出


## 项目功能使用示例

首先下载PackageApkTool项目中的DeskDemo.zip和PackageResource.zip两个压缩包，解压后，目录结构如下：

DeskDemo： 

![image text](https://github.com/Bzaigege/PackageApkTool/blob/master/git/DeskDemoDir.png)

WorkSpace为工作目录，UIMain.exe为可执行文件

PackageResource：内置打包示例资源

![image text](https://github.com/Bzaigege/PackageApkTool/blob/master/git/PackageResourceDir.png)

GameSDKFrame.apk 为模拟已接入测试渠道SDK的游戏母包

lexiang_1_1.0.0.zip 为渠道资源包，格式为：渠道名_渠道ID_渠道版本。 内置为渠道资源目录

启动UIMain.exe后依次选择资源。然后打包运行。

![image text](https://github.com/Bzaigege/PackageApkTool/blob/master/git/%E6%89%93%E5%8C%85.gif)

### 配置参数说明：

不同的渠道配置可通过参数配置栏填写，包括动态修改游戏的minSdk、TargetSdk、包名等配置。配置完毕后会写到对应的配置文件里，
编译过程用到的参数都可以在这里配置对应的Key_Value值。

目前只适配十多常用渠道适配修改，如有额外渠道适配或当前适配参数Key不满足需求时，需要修改渠道适配代码[代码地址](https://github.com/Bzaigege/PackageApkTool/tree/master/channel/special)还有UI配置项[代码地址](https://github.com/Bzaigege/PackageApkTool/blob/master/ui/JChannelConfig.py)。如果有拓展，可自行添加代码修改，也可以贡献代码上传到该库

### 渠道资源包说明：
格式为：渠道名_渠道ID_渠道版本。 内置为渠道资源目录 
![image text](https://github.com/Bzaigege/PackageApkTool/blob/master/git/channelresource.png)

* assets 为渠道assets资源目录，与游戏assets目录合并
* config 为配置文件资源目录，可根据需求拓展
* icon 为渠道角标资源目录，与游戏自有Icon合并
* libs 为渠道.jar和.so文件资源目录，与游戏lib目录合并
* res 为渠道res资源目录,与游戏res资源目录合并
* splash 为渠道闪屏资源目录，打包时，拷贝到assets对应目录下
* wxcallback 为渠道处理微信登录、支付特殊处理的类文件，打包时会编译成jar文件，最终打包到游戏包内
* AndroidManifest.xml 为渠道配置文件，与游戏AndroidManifest.xml合并

## 项目打包成exe文件
首先需要安装pyinstaller模块，可自行搜索安装。
然后进入到项目的根目录，在当前目录下找到UIMain.spec文件，修改pathex=['项目根目录路径']为当前项目目录根路径，执行pyinstaller -F UIMain.spec即可

## 项目资料参考

* [手游SDK — 第五篇（游戏打包篇（上）- 打包系统设计）](https://www.jianshu.com/p/e86e106304d3)
* [手游SDK — 第六篇（游戏打包篇（中）- 自动化打包）](https://www.jianshu.com/p/e75dceb6c7f2)
* [手游SDK — 第七篇（游戏打包篇（下）- 自动化打包踩坑记录）](https://www.jianshu.com/p/16f852b3aabb)
* [手游SDK — 第八篇（游戏打包番外篇-  桌面UI设计）](https://www.jianshu.com/p/0621aa8704b7)


## 项目适配H5游戏打包

打包项目适配H5游戏打包，可参考资源实现
* [手游SDK — 第九篇（浅谈适配H5游戏）](https://www.jianshu.com/p/d2e7738b4efc)



