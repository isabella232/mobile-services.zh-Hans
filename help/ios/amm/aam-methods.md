---
description: 以下是 iOS 库提供的 Audience Manager 方法列表。
seo-description: 以下是 iOS 库提供的 Audience Manager 方法列表。
seo-title: Audience Manager 方法
solution: Marketing Cloud，Analytics
title: Audience Manager 方法
topic: 开发人员和实施
uuid: 96758bd6-4c4f-4875-ea9-36adad4 ec8 Bae
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods {#audience-manager-methods}

以下是 iOS 库提供的 Audience Manager 方法列表。

SDK目前支持多个Adobe Experience Cloud解决方案，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。方法将根据解决方案来添加前缀， Manager 方法的前缀为“`audience`audience”。

如果在 JSON 文件中配置了 Audience Manager，则会随 `application:didFinishLaunchingWithOptions:` : 发送一个包含生命周期量度的信号。

* **audienceVisitorProfile**

   返回最近获取的访客资料，如果没有提交任何信号，则返回 `null`。访客资料保存在 `NSUserDefaults` 中，以供在多次启动应用程序时轻松访问。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * 下面是此菜单的代码示例：

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   返回当前 DPID。

   * 下面是这种方法对应的语法：

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   返回当前 DPUUID。

   * 下面是这种方法对应的语法：

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   设置 DPID 和 DPUUID。设置后，二者会同时附加到每个信号。

   * **数据提供程序 ID (DPID)** 是指由 Audience Manager 分配的数据合作伙伴 ID。
   * **数据提供程序唯一用户 ID (DPUUID)** 是指数据提供程序的唯一用户 ID。

      >[!IMPORTANT]
      >
      >在4.13.x版本之前，DPUUID未自动编码。从版本 4.13.x 开始，SDK 将首先对传入的值进行解码，然后再对该值重新编码。此过程可确保 SDK 不会破坏向后兼容性。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * 以下是这种方法的代码示例：

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   重置 Audience Manager UUID 并清除当前访客资料。

   * 下面是这种方法对应的语法：

      ```objective-c
      +(void) audienceReset;
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   向受众管理发送一个具有特征的信号，并获取块回调中返回的匹配区段。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## 示例

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
