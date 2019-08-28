---
description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置序列化事件。
keywords: android；库；移动；sdk
seo-description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置序列化事件。
seo-title: 事件序列化
solution: Marketing Cloud，Analytics
title: 事件序列化
topic: 开发人员和实施
uuid: acdeda16-ab83-4cfc-907d-33448b801 b31
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置序列化事件。

```java
cdata.put("&&events", "event1:12341234");
```

例如：

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```

