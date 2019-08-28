---
description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置序列化事件。
seo-description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置序列化事件。
seo-title: 事件序列化
solution: Marketing Cloud，Analytics
title: 事件序列化
topic: 开发人员和实施
uuid: 7220a001-1174-4013-91ff-e8603 d8 ab265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。在移动SDK中，您必须在context data参数中使用特殊语法，直接在服务器调用上设置序列化事件。

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

