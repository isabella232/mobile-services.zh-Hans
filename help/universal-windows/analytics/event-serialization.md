---
description: 处理规则不支持事件序列化。 在移动SDK中，必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。
seo-description: 处理规则不支持事件序列化。 在移动SDK中，必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。
seo-title: 事件序列化
solution: Experience Cloud,Analytics
title: 事件序列化
topic: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。 在移动SDK中，您必须在上下文数据参数中使用特殊语法，在服务器调用中直接设置序列化事件。

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

