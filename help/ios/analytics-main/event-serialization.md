---
description: 处理规则不支持事件序列化。在 Mobile SDK 中，必须在上下文数据参数中使用特殊语法来直接设置服务器调用中的序列化事件。
solution: Experience Cloud,Analytics
title: 事件序列化
topic-fix: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
exl-id: c34331a4-bfe2-4955-807b-92a3303f8d81
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 100%

---

# 事件序列化 {#event-serialization}

处理规则不支持事件序列化。在 Mobile SDK 中，必须在上下文数据参数中使用特殊语法来直接设置服务器调用中的序列化事件。

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
