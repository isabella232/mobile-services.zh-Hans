---
description: 您可以使用此信息帮助了解回发的含义及其工作方式。
keywords: Android;库;移动;SDK
seo-description: 您可以使用此信息帮助了解回发的含义及其工作方式。
seo-title: 回发示例
solution: Experience Cloud,Analytics
title: 回发示例
topic-fix: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
exl-id: 2ff41066-e2ee-425f-8aff-e5e3f3e5f0f5
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# 回发示例 {#postbacks-example}

您可以使用此信息帮助了解回发的含义及其工作方式。

>[!CAUTION]
>
>此示例仅供参考之用。`ADBMobileConfig.json` 文件应在 Adobe Mobile 用户界面中配置，而不应手动修改。在启用了远程消息配置时，手动编辑的配置文件可能会很危险。

## `ADBMobileConfig.json` 定义 {#section_8751E8176F3546C09420341A39758AFF}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## 代码示例 {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

由于其状态为 `“MainMenu”`，因此该跟踪调用会触发上述回发消息。URL 会将所有的模板变量替换为来自点击的值。假定用户上一个会话的时长为 132 秒，并且该用户使用的是 Android SDK 版本 4.6.0，则生成的 URL 如下所示：

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
