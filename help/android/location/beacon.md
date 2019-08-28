---
description: 通过信标跟踪，您可以使用 iBeacon 和低功耗蓝牙测量并定位微位置。
keywords: android；库；移动；sdk
seo-description: 通过信标跟踪，您可以使用 iBeacon 和低功耗蓝牙测量并定位微位置。
seo-title: 信标跟踪
solution: Marketing Cloud，Analytics
title: 信标跟踪
topic: 开发人员和实施
uuid: 16c1d267-85f4-4a6a6d6d3d3d6ffb0f80b29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 信标跟踪 {#beacon-tracking}

通过信标跟踪，您可以使用 iBeacon 和低功耗蓝牙测量并定位微位置。

在调用 `trackBeacon` 时，会将以下信标数据发送到 Analytics 和 Target：

* `a.beacon.uuid` - proximityYIÉ of the信标
* `a.beacon.major` - 信标的主编号（如存储编号）
* `a.beacon.minor` - 信标的次编号（如存储内的唯一编号）
* `a.beacon.prox` - 值 0 至 3 表示用户与信标的接近度。

下面介绍了这些值的含义：

* 0 = 未知
* 1 = 非常近
* 2 = 近
* 3 = 远

此信标数据是在移动设备解决方案变量中捕获的。

## 跟踪信标 {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参阅 *在核心实施和生命周期* 中 [将SDK和Config文件添加到IntelliJ IDEA或Eclipse项目](/help/android/getting-started/dev-qs.md)。

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 收集信标位置。

   许多第三方库可用来扫描低功耗蓝牙信标，具体使用哪个库取决于信标的制造商。
1. 获取信标信息后，使用以下调用跟踪位置：

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. 当用户远离信标时，清除当前信标：

   ```java
   Analytics.clearBeacon();
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了信标数据之外，您还可以通过每个 `trackBeacon` 调用发送其他上下文数据：

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

在Adobe Mobile服务中，上下文数据值必须映射到自定义变量：

![](assets/map-variable-context-ltv.png)

