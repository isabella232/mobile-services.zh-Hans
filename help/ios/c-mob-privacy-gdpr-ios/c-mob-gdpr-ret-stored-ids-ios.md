---
description: 此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。
seo-description: 此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。
seo-title: 检索存储的标识符
title: 检索存储的标识符
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 64%

---


# 检索存储的标识符{#retrieving-stored-identifiers}

此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。

有关GDPR的更多信息，请参 [阅GDPR和您的业务](https://www.adobe.com/cn/privacy/general-data-protection-regulation.html)。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法可检索存储在 Experience Cloud SDK 中的身份信息。You must call this method **before** the user opts-out.

Experience CloudSDK标识（如果适用）在本地存储并返回JSON字符串，其中可能包含：

* 公司上下文 - IMS 组织 ID
* 用户 ID
* Experience CloudiD(MID)，以前称为Marketing CloudID
* 集成代码（ADID，推送ID）
* 数据源 ID (DPID、DPUUID)
* Analytics ID（AVID、AID、VID 和相关 RSID）
* 目标旧版ID(TNTID, TNT3rdpartyID)
* Audience Manager ID (UUID)

以下示例介绍了 iOS 中的 `ADBMobile getAllIdentifiersAsync` 方法：

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

