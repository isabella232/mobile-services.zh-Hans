---
description: 此信息可帮助您排查推送消息问题。
keywords: mobile
seo-description: 此信息可帮助您排查推送消息问题。
seo-title: 排查推送消息问题
solution: Marketing Cloud，Analytics
title: 排查推送消息问题
topic: 量度
uuid: c7be7ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

此信息可帮助您排查推送消息问题。

## 为什么发送推送消息有时会出现延迟？

以下延迟类型可能与 Mobile Services 的推送消息有关。

* **等待Analytics点击**

   每个报表包都有一个设置来确定何时处理传入的 Analytics 点击。默认每 1 小时处理一次点击。

   对 Analytics 点击的实际处理可能最多需要 30 分钟，但通常为 15 到 20 分钟。例如，一个报表包每小时处理一次点击。如果将所需的处理时间（最多为 30 分钟）考虑在内，则可能需要长达 90 分钟的时间才能使传入点击可用于推送消息。如果用户在上午 9:01 启动应用程序，则该点击将在上午 10:15 到 10:30 期间在 Mobile Services UI 中显示为新的独特用户。

* **等待推送服务**

   推送服务（APNS 或 GCM）可能不会立即发出消息。虽然不常见，但会出现等待时间长达 5-10 分钟的情况。您可以验证推送消息是否已发送到推送服务，方法是查看推送消息的&#x200B;**[!UICONTROL 报表]**&#x200B;视图，在&#x200B;**[!UICONTROL 消息历史记录]表中找到该消息，然后查看**&#x200B;已发布]计数。**[!UICONTROL **

   >[!TIP]
   >
   >此计数是成功发送到推送服务的次数。推送服务不保证消息将被发送。

   有关服务可靠性的更多信息，请参阅：

   * [服务质量](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [信息的生命周期](https://developers.google.com/cloud-messaging/concept-options#lifetime)。

## 我的 Android GCM API 密钥为何无效？

* **无效的 API 密钥**

   由于以下原因，您的 API 密钥可能会无效：

   * 您提供的 API 密钥不是具有正确 GCM API 密钥值的服务器密钥。
   * 服务器密钥已将 IP 列入白名单，并阻止 Adobe 的服务器发送推送消息。

* **确定 API 密钥的有效性**

   要确定 API 密钥的有效性，请运行以下命令：

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   返回的 401 HTTP 状态代码意味着您的 API 密钥是无效的。在其他情况下，您将看到类似于如下的内容：

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## 为何我的 APNS 证书无效？

由于以下原因，您的 API 证书可能会无效：

* 您可能使用的是沙盒证书而不是生产证书。
* 您使用的是不受支持的新生产/沙盒证书。
* You are using `.p8` file instead of a `.p12` file.

## 解决推送消息失败问题

**示例**

以下示例说明了如何解决使用 VRS 时出现推送失败的问题。

以下客户拥有两个 iOS 应用程序：

* 应用程序名称：PhotoShop_app_iOS
   * 父 RSID：AllAdobe PhotoShop_apps
   * VRSID：PhotoShop_iOS_app_SF
   * VRSID定义区段： `a.appid contains “PhotoShop_iOS_app_SF”`
* 应用程序名称：PhotoShop_app_iOS
   * 父 RSID：AllAdobe PhotoShop_apps
   * RSID：Photoshop_ iOS_ app_ LA
   * VRSID定义区段： `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

If passed with the *PhotoShop_IOS_app_LA* push certificate, the push identifiers for the *PhotoShop_iOS_app_SF* come back as `invalid`.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. 如果每个应用都&#x200B;**不**&#x200B;具有有效的证书，则您的受众区段可能会被无限期地列入黑名单，并且将来可能无法将推送消息发送给受影响的用户。有关受众细分的更多信息，请参阅 [受众：定义和配置推送消息的受众选项](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)。
