---
description: 使用 iOS SDK 实施第三方延期深层链接跟踪。
seo-description: 使用 iOS SDK 实施第三方延期深层链接跟踪。
seo-title: 跟踪第三方延期深层链接
title: 跟踪第三方延期深层链接
uuid: 5525b609-e926-44b9-b0 f5-38e9 dd7 c9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# 跟踪第三方延迟深层链接 {#tracking-third-party-deferred-deep-links}

使用 iOS SDK 实施第三方延期深层链接跟踪。

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

The Adobe Mobile SDK currently supports deep linking where the app developer is expected to call the `trackAdobeDeepLink` API and pass the deep linking URL, which is the fingerprinter URL that is generated in Adobe Mobile Services during configuration. 该 SDK 可对指纹执行 ping 操作以获取客户获取数据，并将其作为生命周期的一部分附加到安装/启动分析调用上下文数据中。此外，SDK还会附加取消链接URL参数中的链接数据。有关深层链接的更多信息，请参阅[跟踪深层链接](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md)。

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

广告创建者可在 Facebook 上创建一个广告作为深层链接。当用户点击 Facebook 上的广告时，将直接转到应用程序中他们感兴趣的信息。深层链接&#x200B;**不是**&#x200B;指纹 URL。但是，在广告配置期间，有一个选项可提供第三方深层链接 URL。使用 Experience Cloud Mobile SDK 和服务的应用程序开发人员应在此字段中输入 Mobile Service 配置的指纹 URL。如果一切设置正确，在安装或启动应用程序时，Facebook SDK 便会将此 URL 传递到应用程序。

## 设置 SDK {#section_834CD3109175432B8173ECB6EA7DE315}

1. 设置Facebook SDK。

   有关更多信息，请参阅以下内容：

   * [适用于 iOS 的 Facebook SDK 快速入门](https://developers.facebook.com/docs/ios/getting-started)
   * [深层链接设置](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. 要设置SDK，请调用并 `trackAdobeDeepLink` 将URL传递到SDK：

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >Ensure that the deep link URL has a key with the name `a.deeplink.id`. 如果 URL 缺少 `a.deeplink.id` 参数，则不会将 URL 参数附加到上下文数据中。

如果按以上所述设置了应用程序，当前的 AMSDK 版本将可正常运行，并向安装/启动分析调用正确附加深层链接数据。

## 在示例应用程序中启用该功能 {#section_64C15E269E89424B8E3D029F88094620}

1. 注册 URL 方案。

   确保您注册了与深层链接 URL 相同的 URL 方案。

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. 关联 Facebook SDK。

   ![Facebook资产](assets/link-fb-sdk.jpg)

1. 编辑 `AppDelegate`.

   1. 导入标头。

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. 添加用于推迟深层链接的句柄。

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. 调用 `trackAdobeDeepLink` API并将深层链接URL传递给SDK。

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```

