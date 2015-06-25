EventBus
========
#### 该说明文件为个人翻译版，水平有限，可能部分内容翻译错误，疑问可以参考[【英文版】](https://github.com/GcsSloop/EventBus/blob/master/README%20-%20EN.md)

EventBus 是安卓系统上一个优秀的事件总线处理机制。
<img src="EventBus-Publish-Subscribe.png" width="500" height="187"/>

EventBus...
-----------

 * 简化了组件之间的通信
    * 使事件发送者和接收者解耦
    * 可以很好的在 Activities, Fragments, and background threads(后台线程) 中执行
    * 避免了复杂和容易出错的依赖以及生命周期问题
 * 使你的代码更简单
 * 速度快
 * 体积小 (<50k jar)
 * 目前已经在 100,000,000 个以上的APP中使用该功能
 * 拥有先进的功能，例如：传递线程，用户优先权 等...


 [![Build Status](https://travis-ci.org/greenrobot/EventBus.svg?branch=master)](https://travis-ci.org/greenrobot/EventBus)


使用步骤:
-------------------
1. 定义事件(Event):<br/>
<code>public class MessageEvent { /* Additional fields if needed */ }</code><br/><br/>
2. 准备订阅:<br/>
<code>eventBus.register(this);</code><br/>
<code>public void onEvent(AnyEventType event) {/* Do something */};</code><br/><br/>
3. 发布事件:<br/>
<code>eventBus.post(event);</code>


添加 EventBus 到你的项目中
----------------------------
EventBus is available on Maven Central. 确保你使用的版本是最新版请 [点击这里检查](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22de.greenrobot%22%20AND%20a%3A%22eventbus%22)

Gradle:
```
    compile 'de.greenrobot:eventbus:2.4.0'
```

Maven:
```
<dependency>
    <groupId>de.greenrobot</groupId>
    <artifactId>eventbus</artifactId>
    <version>2.4.0</version>
</dependency>
```

[或者在 Maven Central 下载](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22de.greenrobot%22%20AND%20a%3A%22eventbus%22)


使用方法以及原理介绍
----
为了不重复制造已经存在的东西(其实是偷懒)，我这里摘选了两篇比较好的博客，第一篇适eventbus入门使用，第二篇适合学习框架原理。<br/>
[EventBus使用详解](http://blog.csdn.net/harvic880925/article/details/40660137)<br/>
[Android 框架炼成 教你如何写组件间通信框架EventBus](http://blog.csdn.net/lmj623565791/article/details/41096639)<br/>

How-to, Developer Documentation
-------------------------------
Details on EventBus and its API are available in the [HOWTO document](HOWTO.md).

How does EventBus compare to other solutions, like Otto from Square? Check this [comparison](COMPARISON.md).

Additional Features and Notes
-----------------------------

* **NOT based on annotations:** Querying annotations are slow on Android, especially before Android 4.0. Have a look at this [Android bug report](http://code.google.com/p/android/issues/detail?id=7811).
* **Based on conventions:** Event handling methods are called "onEvent".
* **Performance optimized:** It's probably the fastest event bus for Android.
* **Convenience singleton:** You can get a process wide event bus instance by calling EventBus.getDefault(). You can still call new EventBus() to create any number of local busses.
* **Subscriber and event inheritance:** Event handler methods may be defined in super classes, and events are posted to handlers of the event's super classes including any implemented interfaces. For example, subscriber may register to events of the type Object to receive all events posted on the event bus.

FAQ
---
**Q:** How is EventBus different to Android's BroadcastReceiver/Intent system?<br/>
**A:** Unlike Android's BroadcastReceiver/Intent system, EventBus uses standard Java classes as events and offers a more convenient API. EventBus is intended for a lot more uses cases where you wouldn't want to go through the hassle of setting up Intents, preparing Intent extras, implementing broadcast receivers, and extracting Intent extras again. Also, EventBus comes with a much lower overhead.

 **Q:** How to do pull requests?<br/>
 **A:** Ensure good code quality and consistent formatting. EventBus has a good test coverage: if you propose a new feature or fix a bug, please add a unit test.

Release History, License
------------------------
[CHANGELOG](CHANGELOG.md)

EventBus binaries and source code can be used according to the [Apache License, Version 2.0](LICENSE).

More Open Source by greenrobot
==============================
[__greenrobot-common__](https://github.com/greenrobot/greenrobot-common) is a set of utility classes and hash functions for Android & Java projects.

[__greenDAO__](https://github.com/greenrobot/greenDAO) is an ORM optimized for Android: it maps database tables to Java objects and uses code generation for optimal speed.

[Follow us on Google+](https://plus.google.com/b/114381455741141514652/+GreenrobotDe/posts) to stay up to date.
