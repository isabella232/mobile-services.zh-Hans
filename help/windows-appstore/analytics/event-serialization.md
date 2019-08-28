---
description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置序列化事件。
seo-description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数内使用专门的语法，直接在服务器调用中设置序列化事件。
seo-title: 事件序列化
solution: Marketing Cloud，Analytics
title: 事件序列化
topic: 开发人员和实施
uuid: a5966d05-e218-446f-9f19-8664a84 b74 cd
translation-type: tm+mt
source-git-commit: 4faf66df50c8b65198fd139bb15927fc2c2849bc

---


# 事件序列化{#event-serialization}

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

