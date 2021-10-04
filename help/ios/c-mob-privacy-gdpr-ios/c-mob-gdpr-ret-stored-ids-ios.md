---
description: 此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。
title: 检索存储的标识符
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 60%

---

# 检索存储的标识符{#retrieving-stored-identifiers}

此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。

有关GDPR的更多信息，请参阅[GDPR与您的业务](https://www.adobe.com/cn/privacy/general-data-protection-regulation.html)。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法可检索存储在 Experience Cloud SDK 中的身份信息。必须在用户选择禁用之前&#x200B;**调用此方法。**

Experience CloudSDK标识（如果适用）存储在本地，并在JSON字符串中返回，该字符串可能包含：

* 公司上下文 - IMS 组织 ID
* 用户 ID
* Experience CloudiD(MID)，以前称为Marketing CloudID
* 集成代码（ADID、推送ID）
* 数据源 ID (DPID、DPUUID)
* Analytics ID（AVID、AID、VID 和相关 RSID）
* 目标旧版ID(TNTID、TNT3rdpartyID)
* Audience Manager ID (UUID)

以下示例介绍了 iOS 中的 `ADBMobile getAllIdentifiersAsync` 方法：

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
