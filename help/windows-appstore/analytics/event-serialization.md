---
description: 处理规则不支持事件序列化。在移动SDK中，必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。
seo-description: 处理规则不支持事件序列化。在移动SDK中，必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。
seo-title: 事件序列化
solution: Experience Cloud,Analytics
title: 事件序列化
topic-fix: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
exl-id: 42ea5e0f-a69e-44ab-aa4e-bbec27815cc8
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---

# 事件序列化{#event-serialization}

处理规则不支持事件序列化。在mobile SDK中，必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。

```js
cdata["&&events"] = "event1:12341234";
```

例如：

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```
