---
description: 在将库添加到项目后，您可以在应用程序中的任意位置进行任何Analytics方法调用（确保将ADBMobile.h导入到类中）。
seo-description: 在将库添加到项目后，您可以在应用程序中的任意位置进行任何Analytics方法调用（确保将ADBMobile.h导入到类中）。
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 14%

---


# Analytics {#analytics}

在将库添加到项目后，您可以在应用程序中的任意位置进行任何Analytics方法调用（确保将ADBMobile.h导入到类中）。

## 在Analytics中启用移动应用程序报告 {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

在添加代码之前，请让Analytics管理员完成以下操作以启用移动应用程序生命周期跟踪。 这可确保您的报表包在您开始开发时能够捕获指标。


1. 打 **[!UICONTROL 开“管理]** 工具” **[!UICONTROL >“报表包]** ”，然后选择移动报表包。
1. 单击 **[!UICONTROL “编辑设置]** ”>“ **[!UICONTROL 移动管理]** ”>“移 **[!UICONTROL 动应用程序报告]**”。

   ![](assets/mobile-settings.png)

1. 单击“ **[!UICONTROL 启用最新的应用程序报告]**”。

   或者，您也可以单击“启 **[!UICONTROL 用移动位置跟踪]** ” **[!UICONTROL 和“启用旧版报告和归因”获取后台点击]**。

   ![](assets/enable-lifecycle.png)

生命周期指标现在可以捕获，移动应用程序报表显示在营销 **[!UICONTROL 报表界]** 面的“报表”菜单中。

## 收集生命周期指标 {#task_25D469C62DF84573AEB5E8E950B96205}

1. 要在应用程序中收集生命周期指标，请在构 `collectLifecycleData()` 造函数中 `ApplicationUI` 调用。

   例如：

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   如果 `collectLifecycleData()` 在同一会话中调用两次，则您的应用程序将在第一次呼叫之后的每次呼叫时报告崩溃。 SDK在应用程序关闭时设置一个标志，指示成功退出。 如果未设置此标志，则 `collectLifecyleData()` 报告崩溃。

## Event、Prop 和 eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


如果您查看过ADBMobile类 [和方法参考](/help/blackberry/methods.md)，您可能会想知道在哪里设置事件、eVar、prop、继承者和列表。 在版本4中，您无法再直接在应用程序中分配这些类型的变量。 反而，SDK 使用上下文数据和处理规则将应用程序数据映射到 Analytics 变量以便进行报告。

处理规则为您提供了几个优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响很小。这些值只有在使用处理规则映射后才会显示在报告中。

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## 处理规则 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

处理规则用于将您在上下文数据变量中发送的数据复制到evar、prop和其他变量以进行报告。

2013 年峰会上的[处理规则培训](https://tv.adobe.com/embed/1181/16506/)

[处理规则](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[获得使用处理规则的授权](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

我们建议使用“命名空间”对上下文数据变量进行分组，因为这有助于您保持逻辑顺序。 例如，如果要收集有关产品的信息，您可以定义以下变量：

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

上下文数据变量在处理规则界面中按字母顺序排序，因此命名空间允许您快速查看处于同一命名空间的变量。

此外，我们听说有些人使用evar或prop编号命名上下文数据键：

```js
"eVar1":"jimbo"
```

This might make it *slightly* easier when you perform the one time mapping in processing rules, but you lose readability during debugging and future code updates can be more difficult. 我们强烈建议对键和值使用描述性名称：

```js
"username":"jimbo"
```

定义计数器事件的上下文变量可以具有相同的键和值：

```js
"logon":"logon"
```

定义增量事件的上下文数据变量可以以事件为键，以增量为值：

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe 会保留命名空间 `a.`。除了这一小的限制，上下文数据变量在登录公司中只需是唯一的，即可避免冲突。

## 启用脱机跟踪 {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

要在设备脱机时存储点击，您可以选择在文件中启用脱机跟 `ADBMobileConfig.json` 踪。

在启用脱机跟踪之前，请非常注意配置文件引用中描述的时间戳要求。

## Analytics 方法

有关BlackBerry可用的Analytics方法的列表，请参阅 *AdobeMobile类和方* 法参考 [](/help/blackberry/methods.md)中的Analytics方法。