---
description: 处理规则不支持事件序列化。在Mobile SDK中，必须在上下文数据参数中使用特殊语法来直接设置服务器调用中的序列化事件。
solution: Experience Cloud,Analytics
title: 事件序列化
topic-fix: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
exl-id: 9cb8d739-8b77-4fe7-8592-22e8cff172d4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 31%

---

# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。在Mobile SDK中，必须在上下文数据参数中使用特殊语法来直接设置服务器调用中的序列化事件。

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
