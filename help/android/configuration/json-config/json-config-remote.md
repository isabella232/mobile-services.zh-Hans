---
description: 您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。
solution: Experience Cloud,Analytics
title: 覆盖 ADBMobile JSON 配置路径
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 100%

---

# 覆盖 ADBMobile JSON 配置路径 {#override-the-adbmobile-json-config-path}

您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。

通过 `Config.overrideConfigStream(configInput)` 方法，您能够指定在应用程序启动时加载的其他 `ADBMobile.json` 配置文件的路径。必须在任何其他 Experience Cloud SDK 调用之前（在 `Config.collectLifecycleData()` 之前）调用此方法，通常是在第一个加载活动的 `onCreate` 方法中进行此调用。

通过其他路径调用此方法会导致一次性覆盖配置文件，直到应用程序关闭为止。

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
