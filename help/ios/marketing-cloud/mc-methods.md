---
description: 以下是 iOS 库提供的 Adobe Experience Platform Identity Service 方法。
seo-description: 以下是 iOS 库提供的 Adobe Experience Platform Identity Service 方法。
seo-title: Adobe Experience Platform Identity Service 方法
solution: Experience Cloud,Analytics
title: Adobe Experience Platform Identity Service 方法
topic: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 100%

---


# Adobe Experience Platform Identity Service 方法 {#experience-cloud-id-service-methods}

以下是 iOS 库提供的 Adobe Experience Platform Identity Service 方法。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Experience Cloud 访客 ID 服务。

方法将根据解决方案来添加前缀，Experience Cloud ID 方法的前缀为 `visitor`。有关更多信息，请参阅[启用 Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)。

* **`+`(nullable NSURL`*`)visitorAppendToURL:(nullable NSURL`*`)url;**

   将 Adobe 访客数据附加到 URL 字符串以用于 Adobe JavaScript 库。要使用此方法，您必须具有 Mobile SDK 版本 4.12 或更高版本。有关更多信息，请参阅[附加访客 ID 辅助函数](https://docs.adobe.com/content/help/zh-Hans/id-service/using/id-service-api/methods/appendvisitorid.html)。

   >[!IMPORTANT]
   >
   >此方法可能导致网络调用受阻。请不要在时间敏感的线程中调用此方法。

   * 输入：`URL<NSURL>`
将附加访客信息的必需 URL 字符串。
   * `URL<NSURL>`
附加了访客信息的字符串。

   * 以下是此方法的代码示例：

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   从 ID 服务中检索 Experience Cloud ID。

   * 以下是此方法的语法：

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >此方法可能导致网络调用受阻，因此&#x200B;**不应**&#x200B;从用户界面线程中对其进行调用。

* **visitorSyncIdentifiers:**

   使用该 Experience Cloud ID，您可以设置其他可与每个访客关联的客户 ID。访客 API 接受同一访客具有多个客户 ID，并且使用客户类型标识符区分不同客户 ID 的适用范围。此方法对应于 JavaScript 库中的 `setCustomerIDs`。

   * 以下是此方法的语法：

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   将提供的标识符同步到 ID 服务。传入 `authState` 以作为下列值之一：

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 以下是此方法的语法：

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   将提供的标识符类型和值同步到 ID 服务。传入 `authState` 以作为下列值之一：

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 以下是此方法的语法：

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 以下是此方法的语法：

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   检索只读 `ADBVisitorID` 对象的数组。

   * 以下是此方法的语法：

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **visitorgetUrlVariablesAsync**

   在版本 4.16.0 中引入，此方法会返回一个格式正确的字符串，其中包含访客 ID 服务 URL 变量。有关如何使用此方法的更多信息，请参阅 [Adobe Experience Platform Identity Service 方法](/help/ios/reference/hybrid-app.md)。

   * 以下是此方法的语法：

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * 以下是此方法的代码示例：

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID 接口 {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**公共方法：**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

