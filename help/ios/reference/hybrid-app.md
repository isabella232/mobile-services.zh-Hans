---
description: 如果您的应用程序打开移动 Web 内容，您需要确保访客在本机和移动 Web 之间切换时不会单独进行识别。
seo-description: 如果您的应用程序打开移动 Web 内容，您需要确保访客在本机和移动 Web 之间切换时不会单独进行识别。
seo-title: 应用程序和移动 Web 之间的访客跟踪
solution: Experience Cloud,Analytics
title: 应用程序和移动 Web 之间的访客跟踪
topic: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '528'
ht-degree: 100%

---


# 应用程序和移动 Web 之间的访客跟踪 {#visitor-tracking-between-an-app-and-mobile-web}

如果您的应用程序打开移动 Web 内容，您需要确保访客在本机和移动 Web 之间切换时不会单独进行识别。

## 应用程序中的访客 ID

安装应用程序后，iOS SDK 会生成一个独特访客 ID。此 ID 存储在移动设备上的永久内存中，随每次点击一起发送。此 ID 仅在用户卸载应用程序时才被删除。

>[!TIP]
>
>升级过程中将保留应用程序访客 ID。

## 移动 Web 中的访客 ID

典型的移动 Web 实施使用的标准 Analytics `s_code.js` 或 `AppMeasurement.js` 与桌面站点中所用的相同。JavaScript 库具有自身的独特访客 ID 生成方法，这会导致在从您的应用程序中打开移动 Web 内容时生成一个不同的访客 ID。

要在应用程序和移动 Web 中使用相同的访客 ID，并将应用程序访客 ID 在 URL 中传递到移动 Web，请执行以下操作：

## 在应用程序和移动 Web 之间实施访客跟踪 {#section_EDC91D6C67AD43999227707C2769C65D}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的项目”**。
1. 要将访客信息附加到用于打开 Web 视图的 URL，请调用 `visitorAppendToURL`：

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   或者，从 SDK 版本 4.16.0 开始，您可以调用 `visitorGetUrlVariablesAsync:` 并生成您自己的 URL：

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

目标域上的 ID 服务代码会从 URL 中提取 MID，而不是向 Adobe 发送请求以获取一个新 ID。目标页面上的 ID 服务代码使用传入的 MID 跟踪访客。

对于来自移动 Web 内容的点击，确认 `mid` 参数存在于每次点击中，并且该值匹配由应用程序代码发送的 `mid`。

## 访客跟踪疑难解答 {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### 我没有看到 `[ADBMobile visitorAppendToURL:]`。

确认父应用程序中捆绑的是 Adobe SDK 版本 4.12.0 或更高版本。

### 我在 URL 中没有看到 Adobe ID。

确认以下内容：

* 用于打开 Web 视图的 URL 字符串是由 `[ADBMobile visitorAppendToURL:]` 生成的。

* 对 Adobe ID 进行了编码。

   要确认 ID 已附加到所打开的 URL 中，请查找 `adobe_mc` 查询参数。

### 我的应用程序中的“mid”与 Web 视图中的不相同。*

确认以下内容：

* 用于打开 Web 视图的 URL 字符串是由 `[ADBMobile visitorAppendToURL:]` 生成的。

   URL 字符串包含 Adobe 参数。

   该字符串应当包含 `adobe_mc="SAMPLE_ID_DATA"`，其中 `"SAMPLE_ID_DATA"` 又包含 Adobe Mobile SDK 中生成的 ID。

* `VisitorAPI.js` 的版本为 1.7.0 或更高。

如果这些疑难解答步骤不能解决您的问题，请与 Adobe 客户关怀团队联系；应准备好共享示例应用程序和关联的站点，以便 Adobe 能够验证实施。
