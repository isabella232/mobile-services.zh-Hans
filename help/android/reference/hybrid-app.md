---
description: 如果您的应用程序打开移动 Web 内容，请确保访客在本机和移动 Web 之间切换时不会单独进行识别。
seo-description: 如果您的应用程序打开移动 Web 内容，请确保访客在本机和移动 Web 之间切换时不会单独进行识别。
seo-title: 应用程序和移动 Web 之间的访客跟踪
solution: Experience Cloud,Analytics
title: 应用程序和移动 Web 之间的访客跟踪
topic: Developer and implementation
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '508'
ht-degree: 100%

---


# 应用程序和移动 Web 之间的访客跟踪 {#visitor-tracking-between-an-app-and-mobile-web}

如果您的应用程序打开移动 Web 内容，请确保访客在本机和移动 Web 之间切换时不会单独进行识别。

## 应用程序中的访客 ID

安装应用程序后，Android SDK 会生成一个独特访客 ID。此 ID 会存储在移动设备上的永久内存中，随每次点击一起发送，并且仅在用户卸载应用程序时才会被删除。

>[!TIP]
>
>升级过程中将保留应用程序访客 ID。

## 移动 Web 中的访客 ID

典型的移动 Web 实施使用的标准 Analytics `s_code.js` 或 `AppMeasurement.js` 与桌面站点中所用的相同。JavaScript 库具有自身的独特访客 ID 生成方法，这会导致在从您的应用程序中打开移动 Web 内容时生成一个不同的访客 ID。

## 在应用程序和移动 Web 之间实施访客跟踪 {#section_1755BCCFD42D456EB2319141030FDDFF}

要在应用程序和移动 Web 中使用相同的访客 ID，请执行以下操作：

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

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

目标域上的 ID 服务代码会从 URL 中提取 MID，而不是向 Adobe 发送请求以获取一个新 ID。此代码会使用传入的 MID 来跟踪访客。

对于来自移动 Web 内容的点击，确认 `mid` 参数存在于每次点击中，并且该值匹配由应用程序代码发送的 `mid` 参数。

## 访客跟踪疑难解答 {#section_9B641F8569E34A089C52AA28EA4C891D}

### 我没有看到 `Visitor.appendToURL`。

确认父应用程序中捆绑的是 Adobe SDK 版本 4.12.0 或更高版本。

**我在 URL 中没有看到 Adobe ID。**

* 确认以下内容：
   * 用于打开 Web 视图的 URL 字符串是由 `Visitor.appendToURL(urlString)` 生成的。
   * 对 Adobe ID 进行了编码。要确保 ID 已附加到所打开的 URL 中，请确认该 URL 中显示了 `adobe_mc` 查询参数。

### 我的应用程序中的 `mid` 与 Web 视图中的不相同。

* 确认以下内容：

   * 用于打开 Web 视图的 URL 字符串是由 `Visitor.appendToURL(urlString)` 生成的。
   * URL 字符串包含 Adobe 参数。

      该字符串应当包含 `adobe_mc="SAMPLE_ID_DATA"`，其中 `"SAMPLE_ID_DATA"` 又包含 Adobe Mobile SDK 中生成的 ID。
   * `VisitorAPI.js` 的版本为 1.7.0 或更高。

如果这些疑难解答步骤不能解决您的问题，请联系 Adobe Experience Care 团队。

>[!IMPORTANT]
>
>要使 Adobe 能够验证实施，您需要共享示例应用程序和关联的站点。

