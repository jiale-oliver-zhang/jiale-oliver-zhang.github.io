---
layout: default
title: 自动化提交bug单（一）
nav_order: 3
---

# 自动化提交bug单 in Unreal Engine

## 需求
在我们的流程里，美术师经常需要设置曲线或者polygon作为PCG工具的输入，比如拿道路工具举例，美术需要在unreal里设置曲线，然后cook生成道路，有时候会发现cook完之后，生成的道路跟预想的不一样，或者有很明显的错误，这时候就需要call TA同学来检查了，一般是截图+position告诉TA，然后TA打开UE打开关卡，然后找到那根曲线，cook并打开houdini。。流程特别长，有时候TA没空等闲下来后去找聊天记录都不知道在哪个群里了。

所以决定设计一个bug提交单，它能解决：

* 可以作为规范的信息留存下来。
* 缩短TA debug流程。
* 后续可以作为重点关照对象来验证PCG工具。

它需要具备哪些功能：

导出：
* 快速的选择atom
* 具有截图功能
* 快速记录相关信息（tile,level,position等）
* 需要将曲线写出成json

导入：
* unreal可以根据json信息快速的找到位置
* houdini可以快速fetch到曲线信息

## 方法
主要是将数据导出并随带一些相关数据(unreal)，数据导入（houdini,unreal），导出的话需要美术手动pick up曲线和截图。现在有三种方式，editor utility widget; editor utility blurprint; python.


editor utility blurprint 似乎不能有按钮变量，似乎可以把截图，填参一气呵成，最后输出json和图片到指定位置。但是它似乎只能用于actor或者asset上。我们的曲线系统，貌似不是actor还需要验证，如果是actor的话那就最好了。

editor utility widget 功能齐全，控件也齐全，做起来没什么问题，可能就是ui太丑了，然后连节点效率比较低。

python 功能齐全，控件也齐全，但是需要加载pyside或者pyqt，美术机器不一定都有，比较麻烦，写代码效率会比较高。

如果曲线是actor或者可以用 actor action utility，那就用editor utility blurprint，如果不能，那就用editor utility widget来写UI，python来写具体功能。
