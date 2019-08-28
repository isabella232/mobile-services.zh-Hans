---
description: 此信息可帮助您从 Android 应用程序中检索本地存储的 SDK 身份和处理 GDPR 数据访问请求。
seo-description: 此信息可帮助您从 Android 应用程序中检索本地存储的 SDK 身份和处理 GDPR 数据访问请求。
seo-title: 检索存储的标识符
title: 检索存储的标识符
uuid: 6fd3d202-b0 a1-4c80-96f4-369fc24 ac0 a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

此信息可帮助您从 Android 应用程序中检索本地存储的 SDK 身份和处理 GDPR 数据访问请求。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 该方法检索存储在SDK中的身份。您必须在用户选择禁用&#x200B;**之前**&#x200B;调用此方法。

SDK 身份（如适用）存储在本地，并在 JSON 字符串中返回，其中可能包含以下项：

* 公司上下文 - IMS 组织 ID
* 用户 ID
* Experience Cloud ID (MID)，以前称为 Marketing Cloud ID
* 集成代码（ADID、推送 ID）
* 数据源 ID（DPID、DPUUID）
* Analytics ID（AVID、AID、VID 和关联的 RSID）
* Target 旧版 ID（TNTID、TNT3rdpartyID）
* Audience Manager ID (UUID)

以下示例介绍了 Android 中的 `ADBMobile getAllIdentifiersAsync` 方法：

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
