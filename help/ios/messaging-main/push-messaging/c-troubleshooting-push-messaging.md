---
description: 此信息可帮助您排查推送消息问题。
keywords: mobile
seo-description: 此信息可帮助您排查推送消息问题。
seo-title: 排查推送消息问题
solution: Experience Cloud,Analytics
title: 排查推送消息问题
topic: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '363'
ht-degree: 100%

---


# 排查推送消息问题 {#troubleshooting-push-messaging}

此信息可帮助您排查推送消息问题。

## 为什么发送推送消息有时会出现延迟？

以下延迟类型可能与 Mobile Services 的推送消息有关。

* **等待 Analytics 点击**

   每个报表包都有一个设置来确定何时处理传入的 Analytics 点击。默认为小时，即 1 小时。对 Analytics 点击的实际处理可能最多需要 30 分钟，但通常为 15 到 20 分钟。

   例如，报表包会每小时处理一次点击。如果把最长 30 分钟的处理时间计算在内，则传入点击最长可能需要 90 分钟才能用于推送消息。如果用户在上午 9:01 启动应用程序，则该点击将在上午 10:15 到 10:30 期间在 Mobile Services 用户界面中显示为新的独特用户。

* **等待推送服务**

   推送服务（APNS 或 GCM）可能不会立即发出消息。偶尔会有 5 到 10 分钟的延迟。在消息页面上，您可以单击消息的查看链接来验证推送消息是否已发送到推送服务。在报表中，成功发送到推送服务的消息数会列在已发布列中。

   >[!TIP]
   >
   >推送服务不保证消息将被发送。有关服务可靠性的更多信息，请参阅相应的文档：
   >
   >* **APNS**：[服务的质量](https://developer.apple.com/documentation/usernotifications)
   >
   >* **GCM**：[消息的生命周期](https://developers.google.com/cloud-messaging/concept-options)


## 如何续订 Apple 推送服务证书？

发送推送消息需要具备有效的推送服务证书。当您的证书将要到期或已过期时，Mobile Services 将会通知您。如果您收到此通知，请完成以下步骤来续订您的证书：

1. 单击&#x200B;**[!UICONTROL 管理应用程序设置]**。
2. 要删除当前证书，请滚动到&#x200B;**[!UICONTROL 推送服务]**，然后单击&#x200B;**[!UICONTROL 删除]**。
3. 配置并测试新证书。

   有关更多信息，请参阅[启用推送消息的先决条件](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. 单击&#x200B;**[!UICONTROL 保存]**。

## 为什么在 iOS 模拟器中看不到我的推送消息？

iOS 模拟器不支持推送消息传送。
