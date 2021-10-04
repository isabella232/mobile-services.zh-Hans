---
description: 此信息可帮助您从 Android 应用程序中检索本地存储的 SDK 身份和处理 GDPR 数据访问请求。
title: 检索存储的标识符
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 64%

---

# 检索存储的标识符{#retrieving-stored-identifiers}

此信息可帮助您从 Android 应用程序中检索本地存储的 SDK 身份和处理 GDPR 数据访问请求。

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` 方法可检索存储在 SDK 中的身份信息。必须在用户选择禁用之前&#x200B;**调用此方法。**

SDK标识（如果适用）存储在本地，并在JSON字符串中返回，该字符串可能包含：

* 公司上下文 - IMS 组织 ID
* 用户 ID
* Experience CloudiD(MID)，以前称为Marketing CloudID
* 集成代码（ADID、推送ID）
* 数据源 ID (DPID、DPUUID)
* Analytics ID（AVID、AID、VID 和相关 RSID）
* 目标旧版ID(TNTID、TNT3rdpartyID)
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
