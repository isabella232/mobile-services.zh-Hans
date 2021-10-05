---
description: 将库添加到项目后，您可以在应用程序中的任意位置进行任何Analytics方法调用（确保将ADBMobile.h导入类）。
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
exl-id: 4cd27e1a-e806-4dbb-84f5-63902ca2003f
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 12%

---

# Analytics {#analytics}

将库添加到项目后，您可以在应用程序中的任意位置进行任何Analytics方法调用（确保将ADBMobile.h导入类）。

## 在Analytics中启用移动设备应用程序报表 {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

在添加代码之前，请让Analytics管理员完成以下操作以启用移动设备应用程序生命周期跟踪。 这些操作可确保在您开始开发时，您的报表包已准备好捕获量度。

1. 打开&#x200B;**[!UICONTROL 管理工具]** > **[!UICONTROL 报表包]**，然后选择您的移动设备报表包。
1. 单击&#x200B;**[!UICONTROL 编辑设置]** > **[!UICONTROL 移动设备管理]** > **[!UICONTROL 移动设备应用程序报表]**。

   ![移动设备设置](assets/mobile-settings.png)

1. 单击&#x200B;**[!UICONTROL 启用最新的应用程序报表]**。

   或者，您也可以选择单击&#x200B;**[!UICONTROL 启用移动位置跟踪]**&#x200B;和&#x200B;**[!UICONTROL 启用后台点击量的旧版报告和归因]**。

   ![启用生命周期](assets/enable-lifecycle.png)

生命周期量度现已准备就绪，可以捕获，移动设备应用程序报表显示在市场营销报告界面的&#x200B;**[!UICONTROL 报表]**&#x200B;菜单中。

## 收集生命周期量度 {#task_25D469C62DF84573AEB5E8E950B96205}

1. 要在应用程序中收集生命周期量度，请在`ApplicationUI`构造函数中调用`collectLifecycleData()`。

   例如：

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   如果在同一会话中调用了`collectLifecycleData()`两次，则您的应用程序将在第一次调用后的每次调用时报告崩溃。 SDK会在应用程序关闭时设置一个标志，指示成功退出。 如果未设置此标志，则`collectLifecyleData()`会报告崩溃。

## Event、Prop 和 eVar {#concept_B885D5A71A5D45129CE7C1C3426A7D28}

如果您查看了[ADBMobile类和方法引用](/help/blackberry/methods.md)，您可能很想知道在何处设置事件、eVar、prop、继承人和列表。 在版本4中，您无法再在应用程序中直接分配这些类型的变量。 反而，SDK 使用上下文数据和处理规则将应用程序数据映射到 Analytics 变量以便进行报告。

处理规则为您提供了以下几个优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响很小。这些值在使用处理规则映射后才会显示在报表中。

您直接分配到变量的任何值都应添加到`data`哈希映射中。

## 处理规则 {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

处理规则用于将您在上下文数据变量中发送的数据复制到eVar、prop和其他变量以供报告。

[处理规则](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

Adobe建议使用“命名空间”对上下文数据变量进行分组，因为这有助于保持逻辑顺序。 例如，如果要收集有关产品的信息，可以定义以下变量：

```js
"product.type":"hat";
"product.team":"mariners";
"product.color":"blue";
```

上下文数据变量在处理规则界面中按字母顺序排序，因此命名空间允许您快速查看位于同一命名空间中的变量。

此外，我们还听说，有些人正在使用eVar或prop编号命名上下文数据键：

```js
"eVar1":"jimbo";
```

虽然在处理规则中执行一次性映射时，这可能会使其&#x200B;*略微*&#x200B;变得更轻松，但在调试过程中会失去可读性，并且将来更新代码可能会更加困难。 我们强烈建议改用描述性名称来表示键和值：

```js
"username":"jimbo";
```

定义计数器事件的上下文变量可以具有相同的键和值：

```js
"logon":"logon";
```

定义增量事件的上下文数据变量可以以事件为键，以增量为值：

```js
"levels completed":"6";
```

>[!TIP]
>
>Adobe 会保留命名空间 `a.`。除了这一小限制之外，上下文数据变量在您的登录公司中只需要是唯一的，才能避免冲突。

## 启用离线跟踪 {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

要在设备离线时存储点击量，您可以选择在`ADBMobileConfig.json`文件中启用离线跟踪。

在启用离线跟踪之前，请非常密切地注意配置文件引用中描述的时间戳要求。

## Analytics 方法

有关可用于BlackBerry的Analytics方法列表，请参阅[Adobe移动类和方法引用](/help/blackberry/methods.md)中的&#x200B;*Analytics方法*。
