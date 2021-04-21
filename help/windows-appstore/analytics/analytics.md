---
description: 在将库添加到项目后，您可以在应用程序中的任意位置进行任何Analytics方法调用。
solution: Experience Cloud,Analytics
title: Analytics
topic-fix: Developer and implementation
uuid: fa0ef6c4-c04d-4695-9eb4-ada4e9920e6c
exl-id: 1a7b32b8-731d-4ae3-9feb-dafbb7495590
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 20%

---

# Analytics {#analytics}

在将库添加到项目后，您可以在应用程序中的任意位置进行任何Analytics方法调用。

>[!TIP]
>
>确保将`ADBMobile.h`导入到您的类。

## 在Analytics {#section_F2F9234009184F20BA36B5CDE872B424}中启用移动应用程序报告

在添加代码之前，请让Analytics管理员完成以下操作以启用移动应用程序生命周期跟踪。 这可确保您的报表包在您开始开发时能够捕获量度。

1. 打开&#x200B;**[!UICONTROL 管理工具]** > **[!UICONTROL 报表包]**&#x200B;并选择移动报表包。
1. 单击&#x200B;**[!UICONTROL 编辑设置]** > **[!UICONTROL 移动设备管理]** > **[!UICONTROL 移动应用报告]**。

   ![](assets/mobile-settings.png)

1. 单击&#x200B;**[!UICONTROL 启用最新应用程序报告]**。

   或者，您也可以单击&#x200B;**[!UICONTROL 启用移动位置跟踪]**&#x200B;和&#x200B;**[!UICONTROL 启用后台报告和归因以获取后台点击]**。

   ![](assets/enable-lifecycle.png)

生命周期量度现在已准备好捕获，移动应用程序报表显示在营销报表界面的&#x200B;**[!UICONTROL 报表]**&#x200B;菜单中。


### 新版本

会定期发布新版本的移动应用程序报告。 新版本不会自动应用到您的报表包，您必须重复这些步骤以执行升级。 每次您向应用程序添加新的Experience Cloud功能时，我们建议您重复这些步骤以确保您具有最新的配置。


## 生命周期量度 {#section_532702562A7A43809407C9A2CBA80E1E}

要在应用程序中收集生命周期量度，请在激活应用程序时添加调用，如以下示例中所示。


### default.js中的WinJS


```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### App.xaml.cs中的C#

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming *= OnResuming; 
    this.Suspending *= OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### App.xaml.cpp中的C/CX

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming *= ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending *= ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

如果在同一会话中调用了两次`CollectLifecycleData()`，则应用程序将在第一次调用后的每次调用中报告崩溃。 SDK在应用程序关闭时设置一个标志，指示成功退出。 如果未设置此标志，`CollectLifecyleData()`将报告崩溃。


## Event、Prop 和 eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}


如果您查看过[ADBMobile类和方法参考](/help/windows-appstore/c-configuration/methods.md)，您可能会想知道在哪里设置事件、eVar、prop、继承和列表。 在版本4中，您无法再直接在应用程序中分配这些类型的变量。 反而，SDK 使用上下文数据和处理规则将应用程序数据映射到 Analytics 变量以便进行报告。

处理规则为您提供了几个优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响很小。使用处理规则映射这些值之前，这些值不会显示在报表中。

您直接分配给变量的任何值都应添加到上下文数据中。


## 处理规则 {#section_66EE762EEA5E4728864166201617DEBF}

处理规则用于将您在上下文数据变量中发送的数据复制到evar、prop和其他变量以进行报告。

2013 年峰会上的[处理规则培训](https://tv.adobe.com/embed/1181/16506/)

[处理规则概述](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[获得使用处理规则的授权](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

我们建议使用“命名空间”对上下文数据变量进行分组，因为这有助于您保持逻辑顺序。 例如，如果要收集有关产品的信息，您可以定义以下变量：

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

上下文数据变量在处理规则界面中按字母顺序排序，因此命名空间使您能够快速查看处于相同命名空间的变量。

此外，我们听说有些人正在使用evar或prop号命名上下文数据键：

```js
"eVar1":"jimbo"
```

这样，在处理规则中执行一次性映射时，它会&#x200B;*稍微*&#x200B;更简单，但在调试过程中会丢失可读性，而将来的代码更新可能会更困难。 我们强烈建议对键和值使用描述性名称：

```js
"username":"jimbo"
```

将定义计数器事件的上下文变量设置为值“1”：

```js
"logon":"1"
```

定义增量事件的上下文数据变量可以具有要增量的值：

```js
"levels completed":"6"
```

>[!NOTE]
>
>Adobe 会保留命名空间 `a.`。除了这一小的限制，上下文数据变量在登录公司中只需是唯一的即可避免冲突。

## Products 变量 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

要在移动SDK中设置&#x200B;*`products`*，必须使用特殊语法。 请参阅[产品变量](/help/windows-appstore/analytics/products/products.md)。

## （可选）启用脱机跟踪{#section_955B2A03EB854742BDFC4A0A3C287009}

要在设备脱机时存储点击，可以在[ADBMobileConfig.json配置](/help/windows-appstore/c-configuration/methods.md)中启用脱机跟踪。 在启用脱机跟踪之前，请注意配置文件引用中描述的时间戳要求。

## 地理位置和目标点 {#section_BAD34A8DD013454DB355121316BD7FD4}

地理位置允许您测量位置数据（经纬度）和预定义的目标点。 每个`TrackLocation`调用发送：

* 纬度/经度和POI（如果在`ADBMobileConfig.json`配置文件中定义的POI中）。 这些变量将传递给移动解决方案变量以实现自动报告。
* 与中心之间的距离和作为上下文数据传递的准确度。 使用处理规则进行捕获。

要跟踪位置：

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

如果在`ADBMobileConfig.json`配置文件中定义了以下POI:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

当设备位置被确定为在定义点的7000米半径内时，将随`TrackLocation`点击发送值为“San Francisco”的`a.loc.poi`上下文数据变量。 将发送`a.loc.dist`上下文变量，其距离定义的坐标以米为单位。

## 生存期值{#section_D2C6971545BA4D639FBE07F13EF08895}

您可以使用生命周期值测量和定位每个用户的生命周期值。每当您通过 `TrackLifetimeValueIncrease` 发送值时，该值都会添加到现有值。生命周期值存储在设备上，并可随时通过调用 `GetLifetimeValue` 进行检索。此值可用于存储生命周期购买、广告查看、视频完成、社交分享、照片上载等。

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## 定时操作 {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

定时操作可让您衡量开始和操作结束之间的应用程序内时间和总时间。 SDK计算会话中的时间量以及完成操作所花费的总时间（跨会话）。 这可用于定义区段以按时进行购买、通过级别、结帐流等比较。

* 应用程序开始和结束之间的总秒数 - 跨会话
* 开始和结束之间的总秒数（时钟时间）

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
