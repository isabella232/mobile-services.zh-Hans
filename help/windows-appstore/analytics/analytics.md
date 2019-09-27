---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Marketing Cloud,Analytics
title: Analytics
topic: 开发人员和实施
uuid: fa0ef6c4-c04d-4695-9eb4-ada4e9920e6c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Analytics {#analytics}

After you add the library to your project, you can make any of the Analytics method calls anywhere in your app.

>[!TIP]
>
>Ensure that you import  to your class.`ADBMobile.h`

## Enable mobile application reports in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

在添加代码之前，请让您的 Analytics 管理员完成以下步骤来启用移动设备应用程序生命周期跟踪。这可确保您的报表包已做好准备，可以在您开始开发时捕获量度。

1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Click **[!UICONTROL Enable Latest App Reports]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** and **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

现在便可以捕获生命周期量度，“移动设备应用程序报表”会出现在市场营销报告界面的“**报表**”菜单中。


### 新版本

移动设备应用程序报表的新版本将会定期发布。新版本不会自动应用于您的报表包，您必须重复这些步骤以执行升级。在您每次向应用程序中添加新的 Experience Cloud 功能时，我们建议您重复这些步骤以确保您具有最新的配置。


## Lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

要在您的应用程序中收集生命周期量度，请添加应用程序被激活时的调用，如以下示例中所示。


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

If `CollectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. SDK 会在应用程序关闭时设置一个标记，以指示成功退出。If this flag is not set, `CollectLifecyleData()` reports a crash.


## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}


If you've looked at the ADBMobile Class and Method Reference, you are probably wondering where to set events, eVars, props, heirs, and lists. [](/help/windows-appstore/c-configuration/methods.md)在版本 4 中，您不能再在应用程序中直接分配这些类型的变量。SDK 而是会使用上下文数据和处理规则将您的应用程序数据映射到 Analytics 变量以供报告。

处理规则具有以下几个好处：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响甚微。这些值在使用处理规则映射后才会显示在报表中。

您直接分配到变量的任何值都应当添加到上下文数据中。


## 处理规则 {#section_66EE762EEA5E4728864166201617DEBF}

处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。

2013 年峰会上的[处理规则培训](https://tv.adobe.com/embed/1181/16506/)

[处理规则概述](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

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

将定义计数器事件的上下文变量设置为值“1”：

```js
"logon":"1"
```

定义增量器事件的上下文数据变量可以使用以下递增值：

```js
"levels completed":"6"
```

>[!NOTE]
>
>Adobe reserves the namespace . `a.`除了这一小限制之外，上下文数据变量只需要在您的登录公司内是唯一的，以便避免冲突。

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

To set  in the mobile SDK, you must use a special syntax. *`products`* See Products Variable.[](/help/windows-appstore/analytics/products/products.md)

## (Optional) Enable offline tracking {#section_955B2A03EB854742BDFC4A0A3C287009}

To store hits when the device is offline, you can enable offline tracking in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md). Before you enable offline tracking, Pay attention to the timestamp requirements described in the config file reference.

## Geo-location and points of interest {#section_BAD34A8DD013454DB355121316BD7FD4}

地理位置允许您测量位置数据（纬度/经度）和预定义的目标点。Each `TrackLocation` call sends:

* 纬度/经度，以及 POI（如果位于在 `ADBMobileConfig.json` 配置文件中定义的 POI 内）。这些信息将被传递到移动设备解决方案变量以便自动进行报告。
* 作为上下文数据传递的到中心的距离以及精确度。使用处理规则捕获。

要跟踪位置，请执行以下操作：

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

如果在 `ADBMobileConfig.json` 配置文件中定义了以下 POI：

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

如果设备位置确定位于以定义点为圆心的 7000 米半径范围内，则会随 `a.loc.poi` 点击发送具有值“San Francisco”的 `TrackLocation` 上下文数据变量。另外，还将发送 `a.loc.dist` 上下文变量，其中包含到定义坐标的距离（以米为单位）。

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

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

## Timed actions {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

定时操作允许您测量某个操作从开始到结束之间的应用程序内时间和总时间。SDK 将计算完成该操作所用的会话内时间量以及总时间（跨会话）。这可用于定义区段以按时比较购买、通过水平、结帐流程等。

* 在应用程序内开始和结束之间的总秒数 - 跨会话
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
