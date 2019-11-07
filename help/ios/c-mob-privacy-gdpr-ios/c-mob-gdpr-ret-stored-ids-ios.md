---
description: 此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。
seo-description: 此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。
seo-title: 检索存储的标识符
title: 检索存储的标识符
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# 检索存储的标识符{#retrieving-stored-identifiers}

此信息可帮助您从 iOS 应用程序中检索本地存储的 Experience Cloud SDK 身份和处理 GDPR 数据访问请求。

有关 GDPR 的更多信息，请参阅 [GDPR 和您的企业](https://www.adobe.com/cn/privacy/general-data-protection-regulation.html)。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法可检索存储在 Experience Cloud SDK 中的身份信息。您必须在用户选择禁用&#x200B;**之前**&#x200B;调用此方法。

Experience Cloud SDK 身份（如适用）存储在本地，并在 JSON 字符串中返回，其中可能包含以下项：

* 公司上下文 - IMS 组织 ID
* 用户 ID
* Experience Cloud ID (MID)，以前称为 Marketing Cloud ID
* 集成代码（ADID、推送 ID）
* 数据源 ID（DPID、DPUUID）
* Analytics ID（AVID、AID、VID 和关联的 RSID）
* Target 旧版 ID（TNTID、TNT3rdpartyID）
* Audience Manager ID (UUID)

以下示例介绍了 iOS 中的 `ADBMobile getAllIdentifiersAsync` 方法：

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

