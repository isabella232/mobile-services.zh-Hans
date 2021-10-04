---
description: 可以使用与应用程序相同的方法跟踪 Android 小组件。小组件与应用程序共享应用程序上下文，因此会保留点击顺序和访客标识。
keywords: Android;库;移动;SDK
solution: Experience Cloud,Analytics
title: Android 小组件
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%

---

# Android 小组件 {#android-widgets}

可以使用与应用程序相同的方法跟踪 Android 小组件。小组件与应用程序共享应用程序上下文，因此会保留点击顺序和访客标识。

以下准则将有助于您跟踪 Android 小组件：

* 不要在小组件中实施生命周期量度 (`startActivity`/`stopActivity`) 调用。

* 要在将小组件添加到主屏幕时进行跟踪，请向小组件的 `onEnabled` 方法添加 `trackState` 或 `trackEvent` 调用。

* 要在从小组件启动应用程序时进行跟踪，请在产生启动应用程序的意图之前，添加 `trackState` 或 `trackEvent` 调用。

* 要跟踪操作的上下文，您可以定义一个 `ContextData` 变量，以便提供相应选项来单独对每个操作进行分段（例如，`AppExperienceType="widget"` 与 `app`）。
