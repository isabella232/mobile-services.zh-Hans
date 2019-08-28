---
description: 您可以使用此信息帮助了解回发的含义及其工作方式。
keywords: android；库；移动；sdk
seo-description: 您可以使用此信息帮助了解回发的含义及其工作方式。
seo-title: 回发示例
solution: Marketing Cloud，Analytics
title: 回发示例
topic: 开发人员和实施
uuid: 8010cd00-d42 b-4e16-8403-692fab2550 f1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

您可以使用此信息帮助您了解回溯是什么以及他们如何工作。

>[!CAUTION]
>
>此示例仅供参考。`ADBMobileConfig.json` 文件应在 Adobe Mobile 用户界面中配置，而不应手动修改。在启用了远程消息配置时，手动编辑的配置文件可能会很危险。

## `ADBMobileConfig.json` definition {#section_8751E8176F3546C09420341A39758AFF}

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. URL 将把所有的模板变量替换为来自点击的值。假定用户的之前会话长为132秒，且该用户在Android SDK版本4.6.0上，因此生成的URL如下所示：

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
