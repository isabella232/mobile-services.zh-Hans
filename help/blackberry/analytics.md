---
description: 在将库添加到项目后，您可以在应用程序中的任何位置进行任何 Analytics 方法调用（确保已将 ADBMobile.h 导入到您的类中）。
seo-description: 在将库添加到项目后，您可以在应用程序中的任何位置进行任何 Analytics 方法调用（确保已将 ADBMobile.h 导入到您的类中）。
seo-title: Analytics
title: Analytics
uuid: de018edet-b37 d-4afe-83a0-801181d7 aff
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

在将库添加到项目后，您可以在应用程序中的任何位置进行任何 Analytics 方法调用（确保已将 ADBMobile.h 导入到您的类中）。

## Enable mobile application reports in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

在添加代码之前，请让您的 Analytics 管理员完成以下步骤来启用移动设备应用程序生命周期跟踪。这可确保您的报表包已做好准备，可以在您开始开发时捕获量度。


1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Click **[!UICONTROL Enable Latest App Reports]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** and **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Lifecycle metrics are now ready to be captured, and Mobile Application Reports] appear in the **[!UICONTROL Reports]** menu in the marketing reports interface.

## 收集生命周期指标 {#task_25D469C62DF84573AEB5E8E950B96205}

1. To collect lifecycle metrics in your app, call `collectLifecycleData()` in the `ApplicationUI` constructor.

   例如：

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   If `collectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. SDK 会在应用程序关闭时设置一个标记，以指示成功退出。If this flag is not set, `collectLifecyleData()` reports a crash.

## Events, props, and eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


如果您查看 [了AdbMobile类和方法参考](/help/blackberry/methods.md)，您可能想知道如何设置事件、eVar、prop、heories和列表。在版本 4 中，您不能再在应用程序中直接分配这些类型的变量。SDK 而是会使用上下文数据和处理规则将您的应用程序数据映射到 Analytics 变量以供报告。

处理规则具有以下几个好处：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响甚微。这些值在使用处理规则映射后才会显示在报表中。

您直接分配到变量的任何值都应当添加到 `data` 哈希映射中。

## 处理规则 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。

2013 年峰会上的[处理规则培训](https://tv.adobe.com/embed/1181/16506/)

[处理规则](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[获得使用处理规则的授权](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

我们建议使用“命名空间”对您的上下文数据变量进行分组，因为它能帮助您保持逻辑顺序。例如，如果您要收集有关某个产品的信息，则可以定义以下变量：

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

上下文数据变量在处理规则界面中按字母顺序进行排序，这样命名空间便能使您快速查看哪些变量位于同一命名空间。

此外，我们还听说有些人使用 eVar 或 prop 编号命名上下文数据键：

```js
"eVar1":"jimbo"
```

在处理规则中执行一次性映射时，这或许会&#x200B;*稍微*&#x200B;提供一些便利，但在调试期间，您将会失去可读性，并且日后也更难以进行代码更新。我们强烈建议为键和值使用描述性名称：

```js
"username":"jimbo"
```

定义计数器事件的上下文变量可以具有相同的键和值：

```js
"logon":"logon"
```

定义增量器事件的上下文数据变量可以使用事件作为键，使用递增量作为值：

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe保留命名空间 `a.`。除了这一小限制之外，上下文数据变量只需要在您的登录公司内是唯一的，以便避免冲突。

## 启用脱机跟踪 {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

To store hits when the device is offline, you can optionally enable offline tracking in the `ADBMobileConfig.json` file.

在启用离线跟踪之前，请密切注意此配置文件引用中所述的时间戳要求。

## 分析方法

有关可用于BlackBerry的Analytics方法列表，请参阅 *Adobe Mobile类和方法参考* 中 [的分析方法](/help/blackberry/methods.md)。