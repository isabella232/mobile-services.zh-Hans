---
description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置序列化事件。
seo-description: 处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置序列化事件。
seo-title: 事件序列化
solution: Marketing Cloud,Analytics
title: 事件序列化
topic: 开发人员和实施
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。在 Mobile SDK 中，您必须在上下文数据参数中使用专门的语法，以直接在服务器调用中设置序列化事件。

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

