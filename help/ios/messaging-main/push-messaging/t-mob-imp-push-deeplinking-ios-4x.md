---
description: 在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 adb_deeplink 键包含在推送有效负荷中。
seo-description: 在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 adb_deeplink 键包含在推送有效负荷中。
seo-title: 通过深层链接实现推送消息
title: 通过深层链接实现推送消息
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 93%

---


# 实施包含深层链接的推送消息 {#implement-push-messaging-with-deep-linking}

在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 `adb_deeplink` 键包含在推送有效负荷中。

1. 在 AppDelegate 中，您可以从以下位置获取并自行处理深层链接 URL：

   * 在 `application:didFinishLaunchingWithOptions`：

      如果在发生推送点进时应用程序未运行，则可以从 `launchOptions` 获取推送有效负荷，并且深层链接 URL 将通过 `adb_deeplink` 键位于有效负荷词典中。

   * 远程通知的委托方法

      在 `didReceiveRemoteNotification:` 应用程序或 `didReceiveRemoteNotification:fetchCompletionHandler:` 应用程序中，您可以通过访问包含 `adb_deeplink` 键的 `userInfo` 词典来获取该 URL。

   * `UNUserNotificationCenter` 的委托方法

      在 `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` 方法中，您可以从 `userInfo` 词典的 `adb_deeplink` 键中获取推送有效负荷。

例如：

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```

