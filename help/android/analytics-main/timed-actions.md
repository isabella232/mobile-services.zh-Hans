---
description: 定时操作允许您测量某个操作从开始到结束之间的应用程序内时间和总时间。SDK计算每个会话中的时间量以及完成该操作所需的整个会话的总时间。 您可以使用定时操作定义区段，并比较购买时间、通过水平、结帐流程等。
seo-description: 定时操作允许您测量某个操作从开始到结束之间的应用程序内时间和总时间。SDK计算每个会话中的时间量以及完成该操作所需的整个会话的总时间。 您可以使用定时操作定义区段，并比较购买时间、通过水平、结帐流程等。
seo-title: 定时操作
solution: Experience Cloud,Analytics
title: 定时操作
topic: Developer and implementation
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 64%

---


# 定时操作 {#timed-actions}

定时操作允许您测量某个操作从开始到结束之间的应用程序内时间和总时间。SDK计算每个会话中的时间量以及完成该操作所需的整个会话的总时间。 您可以使用定时操作定义区段，并比较购买时间、通过水平、结帐流程等。

定时操作报告以下指标：

* 应用程序中开始和结束（交叉会话）之间的总秒数
* 开始和结束之间的总秒数（时钟时间）

可选回调允许您在定时操作完成时执行其他操作：

* 运行代码并添加任何逻辑——可选的自定义逻辑（基于持续时间结果）。
* 在传入持续时间之前添加上下文数据。
* 取消点击和尚未发送的持续时间。

## 跟踪定时操作 {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。
1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 调用 `trackTimedActionStart`，并提供定时操作名称和可选的上下文数据。

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. （可选）您可以随时通过定时操作名称调用 `trackTimedActionUpdate` 以添加其他上下文数据。

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. 事件完成时，调用 `trackTimedActionEnd`，并传递定时操作名称和 `TimedActionBlock`（回调），以查找所有数据并计算持续时间。

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   定时事件量度将保存在移动设备解决方案变量中，以便自动进行报告。

## 发送其他数据 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了定时操作名称之外，您还可以通过操作开始和操作更新调用发送其他上下文数据：

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

上下文数据值必须映射到 Adobe Mobile Services 中的自定义变量：

![](assets/map-variable-context-ltv.png)

## 示例 {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```

