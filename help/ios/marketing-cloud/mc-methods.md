---
description: 以下是iOS库提供的Adobe Experience Platform Identity Service方法。
seo-description: 以下是iOS库提供的Adobe Experience Platform Identity Service方法。
seo-title: Adobe Experience Platform Identity Service方法
solution: Marketing Cloud，Analytics
title: Adobe Experience Platform Identity Service方法
topic: 开发人员和实施
uuid: cdd307bc-8b7d-47a8-b77 e-00902b9 e2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Adobe Experience Platform Identity Service方法 {#experience-cloud-id-service-methods}

以下是iOS库提供的Adobe Experience Platform Identity Service方法。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Experience Cloud 访客 ID 服务。

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. 有关更多信息，请参阅[启用 Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)。

* **`+`(nullable NSURL`*`) togortorAppendURL：(nullable NSURL`*`) url；**

   将 Adobe 访客数据附加到 URL 字符串以用于 Adobe JavaScript 库。要使用此方法，您必须具有Mobile SDK版本4.12或更高版本。有关更多信息，请参阅[附加访客 ID 辅助函数](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)。

   >[!IMPORTANT]
   >
   >此方法可能会导致阻止网络调用。请不要在时间敏感的线程中调用此方法。

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
   * `URL<NSURL>`附加了访客信息的字符串。

   * 以下是这种方法的代码示例：

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   从 ID 服务中检索 Experience Cloud ID。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   除了 Experience Cloud ID 之外，您还可以设置其他与每个访客关联的客户 ID。访客 API 接受同一访客具有多个客户 ID，并且使用客户类型标识符区分不同客户 ID 的适用范围。此方法对应于 JavaScript 库中的 `setCustomerIDs`。

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   将提供的标识符同步到 ID 服务。传入 `authState` 以作为下列值之一：

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   将提供的标识符类型和值同步到 ID 服务。Pass in the `authState` one of the following values:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * 下面是这种方法对应的语法：

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   检索只读 `ADBVisitorID` 对象的数组。

   * 下面是这种方法对应的语法：

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **togtorgOrlvariablesAsync**

   在版本4.16.0中引入的此方法返回一个适当的组成字符串，其中包含访问者ID服务URL变量。有关如何使用此方法的更多信息，请参阅 [Adobe Experience Platform Identity Service方法](/help/ios/reference/hybrid-app.md)。

   * 下面是这种方法对应的语法：

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * 以下是这种方法的代码示例：

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

## ADBMobileVisitorAuthenticationState 枚举 {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

