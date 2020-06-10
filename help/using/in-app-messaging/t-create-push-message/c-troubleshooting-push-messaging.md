---
description: 此信息可帮助您排查推送消息问题。
keywords: mobile
seo-description: 此信息可帮助您排查推送消息问题。
seo-title: 排查推送消息问题
solution: Marketing Cloud,Analytics
title: 排查推送消息问题
topic: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: e6af295ddc5fea2a3e649b659894e6c6123a3457
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 59%

---


# 排查推送消息问题{#troubleshooting-push-messaging}

此信息可帮助您排查推送消息问题。

## 为什么发送推送消息有时会出现延迟？

以下延迟类型可能与 Mobile Services 的推送消息有关。

* **等待 Analytics 点击**

   每个报表包都有一个设置来确定何时处理传入的 Analytics 点击。默认每 1 小时处理一次点击。

   对 Analytics 点击的实际处理可能最多需要 30 分钟，但通常为 15 到 20 分钟。例如，报表包每小时处理一次点击。 如果将所需的处理时间（最大为30分钟）计算在内，则传入的点击最多可能需要90分钟才能用于推送消息。 如果用户在上午 9:01 启动应用程序，则该点击将在上午 10:15 到 10:30 期间在 Mobile Services UI 中显示为新的独特用户。

* **等待推送服务**

   推送服务（APNS或GCM）可能不会立即发出消息。 虽然不常见，但会出现等待时间长达 5-10 分钟的情况。您可以验证推送消息是否已发送到推送服务，方法是查看推送消息的&#x200B;**[!UICONTROL 报表]**&#x200B;视图，在&#x200B;**[!UICONTROL 消息历史记录]**&#x200B;表中找到该消息，然后查看&#x200B;**[!UICONTROL 已发布]**&#x200B;计数。

   >[!TIP]
   >
   >此计数是成功发送到推送服务的数量。推送服务不保证消息将被发送。

   有关服务可靠性的更多信息，请参阅：

   * [服务的质量](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [消息的生命周期](https://developers.google.com/cloud-messaging/concept-options#lifetime)。

## 为什么我的Android GCM API密钥无效？

* **API密钥无效**

   您的API密钥可能无效，原因如下：

   * 您提供的API密钥不是具有正确GCM API密钥值的服务器密钥。
   * 服务器密钥已允许IP，并阻止Adobe服务器发送推送消息。

* **确定API密钥的有效性**

   要确定API密钥的有效性，请运行以下命令：

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   返回的401 HTTP状态代码表示您的API密钥无效。 否则，您将看到类似的内容：

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   您还可以将 `"ABC"` 替换为一个注册令牌，以检查该令牌的有效性。

## 为何我的 APNS 证书无效？

您的APNS证书可能无效，原因如下：

* 您可能使用沙箱证书而不是生产证书。
* 您使用的是不受支持的新生产／沙箱证书。
* 您使用的是 `.p8` 文件而不是 `.p12` 文件。

## 解决推送消息失败问题

**示例**

以下示例说明了在使用VRS时如何解决推送故障。

以下客户有两个iOS应用程序：

* 应用程序名称： PhotoShop_app_iOS
   * 父RSID: 所有Adobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID 定义区段：`a.appid contains “PhotoShop_iOS_app_SF”`
* 应用程序名称： PhotoShop_app_iOS
   * 父RSID: 所有Adobe PhotoShop_apps
   * RSID：PhotoShop_iOS_app_LA
   * VRSID 定义区段：`a.os contains “iOS”`

在此示例中，如果 Photoshop 员工将推送消息发送到 *PhotoShop_iOS_app_SF* 应用程序，则所有 *PhotoShop_iOS_app_SF 应用程序*&#x200B;用户都将会按预期收到推送消息。但是，如果员工将消息发送到 *PhotoShop_iOS_app_LA* 应用程序，因为其 VRSID 定义区段有误（是 `iOS` 而不是 `a.os contains "PhotoShop_iOS_app_LA"`），则该消息会发送到 *AllAdobe PhotoShop_apps* 中的&#x200B;**所有** iOS 用户。Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also deny-lists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. 如果该区段被定义为 `a.os contains “PhotoShop_iOS_app_LA”`，则推送消息将仅被发送到 *PhotoShop_iOS_app_LA* 用户。

如果通过 *PhotoShop_IOS_app_LA* 推送证书传递消息，则 *PhotoShop_iOS_app_SF* 的推送标识符将会返回为 `invalid`。

>[!CAUTION]
>
>在为使用 VRS 的应用程序创建推送消息并单击&#x200B;**[!UICONTROL 保存并发送]**&#x200B;后，会出现一个警报，提醒您确保列出的每个应用程序都&#x200B;**必须**&#x200B;具有一个有效证书。If each app does **not** have a valid certificate, your audience segments might be indefinitely deny listed, and you might not be able to send future push messages to the affected users. 有关受众区段的更多信息，请参阅[受众：为推送消息定义和配置受众选项](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)。
