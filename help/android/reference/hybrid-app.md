---
description: 如果您的应用程序打开移动 Web 内容，请确保访客在本机和移动 Web 之间切换时不会单独进行识别。
seo-description: 如果您的应用程序打开移动 Web 内容，请确保访客在本机和移动 Web 之间切换时不会单独进行识别。
seo-title: 应用程序与移动Web之间的访客跟踪
solution: Marketing Cloud,Analytics
title: 应用程序与移动Web之间的访客跟踪
topic: 开发人员和实施
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor tracking between an app and the mobile web {#visitor-tracking-between-an-app-and-mobile-web}

如果您的应用程序打开移动 Web 内容，请确保访客在本机和移动 Web 之间切换时不会单独进行识别。

## 应用程序中的访客ID

在安装应用程序时，Android SDK 会生成一个独特访客 ID。此 ID 将存储在移动设备上的永久内存中，并会随每次点击一起发送，且仅在用户卸载应用程序时才被删除。

>[!TIP]
>
>App visitor IDs persist through upgrades.

## 移动Web中的访客ID

典型的移动 Web 实施使用的标准 Analytics `s_code.js` 或 `AppMeasurement.js` 与桌面站点中所用的相同。JavaScript 库具有自身的独特访客 ID 生成方法，这会导致在从您的应用程序中打开移动 Web 内容时生成一个不同的访客 ID。

## Implementing visitor tracking between an app and the mobile web {#section_1755BCCFD42D456EB2319141030FDDFF}

要在应用程序和移动 Web 中使用相同的访客 ID，请执行以下操作：

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参 *阅将SDK和配置文件添加到IntelliJ IDEA或Eclipse Project* (在核心实施和生命 [周期中)中](/help/android/getting-started/dev-qs.md)。

1. 要将访客信息附加到用于打开 Web 视图的 URL，请调用 `visitorAppendToURL`：

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   或者，从 SDK 版本 4.16.0 开始，您可以调用 `Visitor.getUrlVariablesAsync` 并生成您自己的 URL：

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

目标域上的 ID 服务代码从 URL 提取 MID，而不是向 Adobe 发送获取新 ID 的请求。该代码使用传入的 MID 跟踪访客。

对于来自移动 Web 内容的点击，确认 `mid` 参数存在于每次点击中，并且该值匹配由应用程序代码发送的 `mid` 参数。

## Troubleshooting visitor tracking {#section_9B641F8569E34A089C52AA28EA4C891D}

### I do not see `Visitor.appendToURL`.

确认父应用程序中捆绑的是 Adobe SDK 版本 4.12.0 或更高版本。

**我在 URL 中没有看到 Adobe ID。**

* 确认以下内容：
   * 用于打开 Web 视图的 URL 字符串是由 `Visitor.appendToURL(urlString)` ) 生成的。
   * 对 Adobe ID 进行了编码。To ensure that the IDs that are appended to the URL that is being opened, verify that the `adobe_mc` query parameter appears in the URL.

### 我的应用程序中的 `mid` 与 Web 视图中的不相同。

* 确认以下内容：

   * 用于打开 Web 视图的 URL 字符串是由 `Visitor.appendToURL(urlString)` ) 生成的。
   * URL 字符串包含 Adobe 参数。

      The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.
   * `VisitorAPI.js` 的版本为 1.7.0 或更高。

如果这些疑难解答步骤不能解决您的问题，请联系 Adobe Experience Care 团队。

>[!IMPORTANT]
>
>To allow Adobe can validate the implementation, you need to share a sample application and the associated site.

