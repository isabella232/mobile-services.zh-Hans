---
description: 您可以使用此信息通过 Adobe Mobile Android SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。
keywords: android；库；移动；sdk
seo-description: 您可以使用此信息通过 Adobe Mobile Android SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。
seo-title: 跟踪Adobe Mobile services中的深层链接
solution: Marketing Cloud,Analytics
title: 跟踪深层链接
topic: 开发人员和实施
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

您可以使用此信息通过 Adobe Mobile Android SDK 在移动设备应用程序中跟踪深层链接和延期深层链接。

## Tracking deep links

1. 将 SDK 添加到您的项目并实施生命周期量度。

   有关详细信息，请参 *阅将SDK和配置文件添加到IntelliJ IDEA或Eclipse Project* (在核心实施和生命 [周期中)中](/help/android/getting-started/dev-qs.md)。

1. 注册应用程序以处理 URL。

   For more information, see [URLs](https://developer.android.com/training/basics/intents/filters.html).
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

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

此外，您还可以将以下一个或多个保留键（带有用户生成的值）附加到深层链接或通用链接：

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

这些键是用于在 Adobe Analytics 中进行报告的预映射变量。有关映射和处理规则的更多信息，请参阅[处理规则和上下文数据](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

## 跟踪延迟的深层链接（用于营销链接）

通过延期深层链接，Adobe SDK 将打开一个新意图并使用该深层链接作为意图数据。此过程将作为外部深层链接使用上述代码来处理。

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### 常量

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

