---
description: 您可以使用此信息通过 Adobe Mobile iOS SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。
seo-description: 您可以使用此信息通过 Adobe Mobile iOS SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。
seo-title: 跟踪深层链接
solution: Experience Cloud,Analytics
title: 跟踪深层链接
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---


# 跟踪深层链接 {#tracking-deep-links}

您可以使用此信息通过 Adobe Mobile iOS SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。

有关营销人员如何在其应用程序中使用深层链接的更多信息，请参阅 Mobile Services 文档中的[客户获取](/help/ios/acquisition-main/acquisition.md)。

## 跟踪深层链接

1. 将 SDK 添加到您的项目并实施生命周期量度。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的项目”**。
1. 注册应用程序以处理应用程序间通信或支持通用链接。

   有关更多信息，请参阅[应用程序间通信](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10)或[支持通用链接](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. 跟踪 openURL 中的深层链接。

   以下是跟踪深层链接的一个示例：

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

Adobe Mobile SDK 可以解析附加到任何深层链接或通用链接的数据键值对，前提是这些链接包含带有 `a.deeplink.id` 标签的键，且其对应的值为用户生成的非空值。附加到链接的数据的所有键值对都将进行解析，附加到生命周期点击，然后发送到 Adobe Analytics，前提是该链接包含 `a.deeplink.id` 键和值。

您还可以选择将以下一个或多个保留键（具有用户生成的值）附加到深层链接或通用链接：

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

这些键是用于在 Adobe Analytics 中进行报告的预映射变量。有关映射和处理规则的更多信息，请参阅[处理规则和上下文数据](/help/ios/getting-started/proc-rules.md)。

### 跟踪延期深层链接

1. 注册 Adobe 数据回调。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. 在 `AdobeDataCallback` 中处理 `ADBMobileDataEventDeepLink`。

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## 深层链接公用信息 {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### 方法

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### 常量

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```

