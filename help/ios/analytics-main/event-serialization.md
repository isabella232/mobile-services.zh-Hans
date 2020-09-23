---
description: 处理规则不支持事件序列化。 在Mobile SDK中，您必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。
seo-description: 处理规则不支持事件序列化。 在Mobile SDK中，您必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。
seo-title: 事件序列化
solution: Experience Cloud,Analytics
title: 事件序列化
topic: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。 在Mobile SDK中，您必须在上下文数据参数中使用特殊语法直接在服务器调用中设置序列化事件。

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

例如：

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

