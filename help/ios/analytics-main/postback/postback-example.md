---
description: 回发功能的定义和源代码示例。
seo-description: 回发功能的定义和源代码示例。
seo-title: 回发示例
solution: Marketing Cloud，Analytics
title: 回发示例
topic: 开发人员和实施
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback example {#postback-example}

回发功能的定义和源代码示例。

>[!CAUTION]
>
>此示例仅供参考。`ADBMobileConfig.json` 文件应在 Adobe Mobile 用户界面中配置，而不应手动修改。在启用了远程消息配置时，手动编辑的配置文件可能会很危险。

## ADBMobileConfig.json definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Code sample {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. URL会替换包含点击值的所有模板变量。假定用户的之前会话长为132秒，而该用户在iOS SDK版本4.6.0上，则下面是生成的URL的示例：

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
