<p align="center">
  <img src="ART/android_god_eye_logo.png" width="256" height="256" />
</p>

<h1 align="center">AndroidGodEye</h1>
<p align="center">
<a href="https://travis-ci.org/Kyson/AndroidGodEye" target="_blank"><img src="https://travis-ci.org/Kyson/AndroidGodEye.svg?branch=master"></img></a>
<a href="https://jitpack.io/#Kyson/AndroidGodEye" target="_blank"><img src="https://jitpack.io/v/Kyson/AndroidGodEye.svg"></img></a>

</p>
<br />

> Android开发者在性能检测方面的工具一直比较匮乏，仅有的一些工具，比如Android Device Monitor，使用起来也有些繁琐，使用起来对开发者有一定的要求。而线上的App监控更无从谈起。所以需要有一个系统能够提供Debug和Release阶段全方位的监控，更深入地了解对App运行时的状态。

## 概览

AndroidGodEye是一个可以在PC浏览器中实时监控Android数据指标（比如性能指标，但是不局限于性能）的工具。

系统分为四部分：

1. Core 核心部分，提供所有模块
2. Debug Debug部分，提供Debug阶段开发者面板
4. Toolbox 快速接入工具集，给开发者提供各种便捷接入的工具

目前，AndroidGodEye提供了11种监控模块，比如cpu、内存、卡顿、内存泄漏等等，并且提供了Debug阶段的Monitor看板实时展示这
些数据。而且提供了api供开发者在release阶段进行数据上报。

## 快速开始

### STEP1

引入依赖，使用gradle

```
dependencies {
  compile 'cn.hikyson.godeye:godeye-core:1.0-SNAPSHOT'
  compile 'cn.hikyson.godeye:godeye-monitor:1.0-SNAPSHOT'
  compile 'cn.hikyson.godeye:godeye-monitor-no-op:1.0-SNAPSHOT'
  compile 'cn.hikyson.godeye:godeye-toolbox:1.0-SNAPSHOT'
}
```

### STEP2

模块安装，GodEye类是AndroidGodEye的核心类，所有模块由它提供。

在应用入口安装所有模块：

```java
GodEye.instance().installAll(getApplication());
```

> 安装完之后相应的模块就开始输出数据了

在不需要的时候可以卸载所有模块：

```java
GodEye.instance().uninstallAll(getApplication());
```

> 开发者也可以根据自己的需求安装模块,注意：network和startup模块不需要安装和卸载,leak detector不需要卸载

### STEP3

Debug面板安装，GodEyeMonitor类是AndroidGodEye的Debug监控面板的主要类，用来开始或者停止Debug面板的监控。

开始监控：

```java
GodEyeMonitor.work(context)
```

结束监控：

```java
GodEyeMonitor.shutDown()
```

### STEP4

完成！开始使用：

手机与pc连接同一网段，在pc浏览器中访问 手机ip+端口 即可看到Debug面板!

> 端口默认是5390，也可以在`GodEyeMonitor.work(context)`中指定，一般在开发者在调用`GodEyeMonitor.work(context)`之后可以看到日志输出 'Open AndroidGodEye dashboard ...' 中包含了访问地址。

## Debug开发者面板

###### Click  ↓  to preview
<p>
<a href="https://player.youku.com/embed/XMzIwMTgyOTI5Mg==">
<img border="0" src="ART/android_god_eye_play.png" width="128" height="128" />
</a>
</p>

### 基本信息展示

![android_godeye_part1](ART/android_godeye_part1.png)

### 内存泄漏展示

![android_godeye_part5](ART/android_godeye_part5.png)

## 关于我

- Github: [Kyson](https://github.com/Kyson)
- Weibo: [hikyson](https://weibo.com/hikyson)
- Blog: [tech.hikyson.cn](https://tech.hikyson.cn/)









