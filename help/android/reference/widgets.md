---
description: 可以使用与应用程序相同的方法来跟踪 Android 小组件。小组件会与您的应用程序共享应用程序上下文，从而保留点击顺序和访客标识。
keywords: android；库；移动；sdk
seo-description: 可以使用与应用程序相同的方法来跟踪 Android 小组件。小组件会与您的应用程序共享应用程序上下文，从而保留点击顺序和访客标识。
seo-title: Android构件
solution: Marketing Cloud，Analytics
title: Android构件
topic: 开发人员和实施
uuid: a3718ff-967b-4c8e0b-ba15 bddbda0 a
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

可以使用与应用程序相同的方法来跟踪 Android 小组件。小组件会与您的应用程序共享应用程序上下文，从而保留点击顺序和访客标识。

以下准则将帮助您跟踪 Android 小组件：

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* 要在将小组件添加到主屏幕时进行跟踪，请向小组件的 `trackState` 方法添加 `trackEvent` 或 `onEnabled` 调用。

* 要在从小组件启动应用程序时进行跟踪，请在产生启动应用程序的意图之前，添加 `trackState` 或 `trackEvent` 调用。

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

