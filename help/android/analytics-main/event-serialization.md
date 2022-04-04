---
description: 处理规则不支持事件序列化。在 Mobile SDK 中，必须在上下文数据参数中使用特殊语法来直接设置服务器调用中的序列化事件。
keywords: Android;库;移动;SDK
solution: Experience Cloud Services,Analytics
title: 事件序列化
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 100%

---

# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。在 Mobile SDK 中，必须在上下文数据参数中使用特殊语法来直接设置服务器调用中的序列化事件。

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
