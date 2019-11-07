---
description: 可以使用与应用程序相同的方法来跟踪 Android 小组件。小组件会与您的应用程序共享应用程序上下文，从而保留点击顺序和访客标识。
keywords: Android;库;移动;SDK
seo-description: 可以使用与应用程序相同的方法来跟踪 Android 小组件。小组件会与您的应用程序共享应用程序上下文，从而保留点击顺序和访客标识。
seo-title: Android 小组件
solution: Marketing Cloud,Analytics
title: Android 小组件
topic: 开发人员和实施
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android 小组件 {#android-widgets}

可以使用与应用程序相同的方法来跟踪 Android 小组件。小组件会与您的应用程序共享应用程序上下文，从而保留点击顺序和访客标识。

以下准则将帮助您跟踪 Android 小组件：

* 不要在小组件中实施生命周期量度 (`startActivity`/`stopActivity`) 调用。

* 要在将小组件添加到主屏幕时进行跟踪，请向小组件的 `onEnabled` 方法添加 `trackState` 或 `trackEvent` 调用。

* 要在从小组件启动应用程序时进行跟踪，请在产生启动应用程序的意图之前，添加 `trackState` 或 `trackEvent` 调用。

* 要跟踪操作的上下文，您可以定义一个 `ContextData` 变量，以便提供相应选项来单独对每个操作进行分段（例如，`AppExperienceType="widget"` 与 `app`）。

