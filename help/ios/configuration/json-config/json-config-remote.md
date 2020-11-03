---
description: 您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。
seo-description: 您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。
seo-title: 覆盖 ADBMobile JSON 配置路径
solution: Experience Cloud,Analytics
title: 覆盖 ADBMobile JSON 配置路径
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '120'
ht-degree: 100%

---


# 覆盖 ADBMobile JSON 配置路径 {#override-the-adbmobile-json-config-path}

您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。

通过 `ADBMobile overrideConfigPath:filePath` 方法，您能够指定在应用程序启动时加载的其他 `ADBMobile.json` 配置文件的路径。必须在 `applicationDidFinishLaunchingWithOptions` 方法中调用此方法，而且必须在其他任何 Experience Cloud SDK 调用（例如 `collectLifecycleData`）之前进行此调用。

通过其他路径调用此方法会导致一次性覆盖配置文件，直到应用程序关闭为止。

例如：

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

