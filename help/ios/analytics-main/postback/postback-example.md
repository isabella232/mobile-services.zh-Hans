---
description: 回发功能的定义和源代码示例。
solution: Experience Cloud Services,Analytics
title: 回发示例
topic-fix: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
exl-id: 3ec5abf1-a406-48b6-91b1-fbcb0a9094ee
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 100%

---

# 回发示例 {#postback-example}

回发功能的定义和源代码示例。

>[!CAUTION]
>
>此示例仅供参考之用。`ADBMobileConfig.json` 文件应在 Adobe Mobile 用户界面中配置，而不应手动修改。在启用了远程消息配置时，手动编辑的配置文件可能会很危险。

## ADBMobileConfig.json 定义 {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## 代码示例 {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

由于其状态为 `"MainMenu"`，因此该跟踪调用会触发上述回发消息。URL 会将所有的模板变量替换为来自点击的值。假定用户上一个会话的时长为 132 秒，并且该用户使用的是 iOS SDK 版本 4.6.0，则生成的 URL 如下所示：

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
