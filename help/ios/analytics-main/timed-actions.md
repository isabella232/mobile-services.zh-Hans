---
description: 定时操作允许您测量某个操作从开始到结束之间的应用程序内时间和总时间。SDK 将计算完成该操作所用的每个会话内时间量以及跨会话总时间。您可以使用定时操作定义区段，并比较购买时间、通过水平、结帐流程等。
seo-description: 定时操作允许您测量某个操作从开始到结束之间的应用程序内时间和总时间。SDK 将计算完成该操作所用的每个会话内时间量以及跨会话总时间。您可以使用定时操作定义区段，并比较购买时间、通过水平、结帐流程等。
seo-title: 定时操作
solution: Marketing Cloud,Analytics
title: 定时操作
topic: 开发人员和实施
uuid: dbcbac5a-6345-49f6-b050-0db05292f005
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Timed actions {#timed-actions}

定时操作允许您测量某个操作从开始到结束之间的应用程序内时间和总时间。SDK 将计算完成该操作所用的每个会话内时间量以及跨会话总时间。您可以使用定时操作定义区段，并比较购买时间、通过水平、结帐流程等。

将为定时操作报告以下量度：

* 在应用程序内开始和结束之间的总秒数 - 跨会话
* 开始和结束之间的总秒数（时钟时间）

通过可选回调，您可以在定时操作完成时执行其他操作：

* 运行代码并添加任何逻辑 - 基于持续时间结果的可选自定义逻辑。
* 在传入持续时间之前添加上下文数据。
* 取消尚未发送的点击和持续时间。

## Tracking timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. 将库添加到您的项目并实施生命周期。

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 调用 `trackTimedActionStart`，并提供定时操作名称和可选的上下文数据。

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. （可选）要随时添加其他上下文数据，您可以通过定时操作名称调用 `trackTimedActionUpdate`。

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. 事件完成时，调用 `trackTimedActionEnd`，并传递定时操作名称和 `TimedActionBlock`（回调），以查找所有数据并计算持续时间。

   定时事件量度将保存在移动设备解决方案变量中，以便自动进行报告。

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了定时操作名称之外，您还可以通过操作开始和操作更新调用发送其他上下文数据：

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

上下文数据值必须映射到自定义变量：

![](assets/map-variable-context-ltv.png)

## 示例 {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```

