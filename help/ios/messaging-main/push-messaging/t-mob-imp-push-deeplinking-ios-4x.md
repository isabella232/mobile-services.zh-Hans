---
description: 在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 adb_deeplink 键包含在推送有效负荷中。
seo-description: 在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 adb_deeplink 键包含在推送有效负荷中。
seo-title: 实施包含深层链接的推送消息
title: 实施包含深层链接的推送消息
uuid: ee9590fc -bd3-4111-921-921-9011d9edbd84
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Implement push messaging with deep linking {#implement-push-messaging-with-deep-linking}

在 Adobe Mobile Services 用户界面中配置深层链接 URL 后，该 URL 将通过 `adb_deeplink` 键包含在推送有效负荷中。

1. 在 AppDelegate 中，您可以从以下位置获取并自行处理深层链接 URL：

   * 在 `application:didFinishLaunchingWithOptions`:

      如果在发生推送点进时应用程序未运行，则可以从 `launchOptions` 获取推送有效负荷，并且深层链接 URL 将通过 `adb_deeplink` 键位于有效负荷词典中。

   * 远程通知的委托方法

      In the `didReceiveRemoteNotification:` application or in the `didReceiveRemoteNotification:fetchCompletionHandler:` application, you can get the URL by accessing the `userInfo` dictionary with the `adb_deeplink` key.

   * The delegate methods for `UNUserNotificationCenter`

      `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` 在该方法中，您可以从字典中获取 `userInfo` 字典的推送有效负荷 `adb_deeplink` 。

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

