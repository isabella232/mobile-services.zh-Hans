---
description: 您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。
seo-description: 您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。
seo-title: 重写AdBMobile JSON配置路径
solution: Marketing Cloud，Analytics
title: 重写AdBMobile JSON配置路径
topic: 开发人员和实施
uuid: 0d1be674-c63-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

您可以在应用程序启动时加载其他 ADBMobile JSON 配置文件。

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. 必须在 `applicationDidFinishLaunchingWithOptions` 方法中调用此方法，而且必须在其他任何 Experience Cloud SDK 调用（例如 `collectLifecycleData`）之前进行此调用。

当您将此方法调用为不同的路径时，配置文件的一次性覆盖会在应用程序关闭之前发生。

例如：

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

