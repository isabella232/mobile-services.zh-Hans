---
description: 您可以使用此信息通过 Adobe Mobile Android SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。
keywords: android;library;mobile;sdk
seo-description: 您可以使用此信息通过 Adobe Mobile Android SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。
seo-title: 在 Adobe Mobile Services 中跟踪深层链接
solution: Marketing Cloud,Analytics
title: 跟踪深层链接
topic: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 88%

---


# 跟踪深层链接 {#tracking-deep-links}

您可以使用此信息通过 Adobe Mobile Android SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。

## 跟踪深层链接

1. 将 SDK 添加到您的项目并实施生命周期量度。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

1. 注册应用程序以处理 URL。

   有关更多信息，请参阅 [URL](https://developer.android.com/training/basics/intents/filters.html)。
1. 通过 `collectLifecycleData` 将包含深层链接意图的活动传递到 Adobe SDK。

   以下是跟踪深层链接的一个示例：

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

The Adobe Mobile SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. 附加到链接的数据的所有键值对都将进行解析，附加到生命周期点击，然后发送到 Adobe Analytics，前提是该链接包含 `a.deeplink.id` 键和值。

此外，您还可以将以下一个或多个保留键（具有用户生成的值）附加到深层链接或通用链接：

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

这些键是用于在 Adobe Analytics 中进行报告的预映射变量。有关映射和处理规则的更多信息，请参阅[处理规则和上下文数据](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

## 跟踪延期深层链接（与营销链接一起使用）

借助延期深层链接，Adobe SDK 将会打开一个新的“意图”，且深层链接作为意图数据。使用上述代码，将此进程作为外部深层链接处理。

## 深层链接公用信息 {#section_1815396353614DA8A63D8D92112217E7}

### 常量

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

