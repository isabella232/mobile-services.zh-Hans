---
description: 帮助您处理视频Analytics的信息。
seo-description: 帮助您处理视频Analytics的信息。
seo-title: Video Analytics
solution: Marketing Cloud,Analytics
title: Video Analytics
topic: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 65%

---


# Video Analytics {#video-analytics}

帮助您处理视频Analytics的信息。

视频测量在AdobeAnalytics指南的“测 [量音频和视频”中有详细介绍](https://docs.adobe.com/content/help/zh-Hans/media-analytics/using/media-overview.html/) 。 在所有AppMeasurement平台上，衡量视频的一般过程都非常相似。 此快速开始部分提供开发人员任务的基本概述以及代码示例。

下表列出了发送到 Analytics 的媒体数据。使用处理规则将上下文数据映射到 Analytics 变量。

* **a.media.name**

   （必需）当访客以某种方式视图视频时，收集视频的名称（如实施中指定）。您可以为此变量添加分类。

   (可&#x200B;**选**)Custom Insight变量提供视频路径信息。

   * 变量类型：eVar
   * 默认过期：访问
   * Custom Insight（s.prop，用于视频路径）

* **a.media.name**

   （可选）提供视频路径信息。必须由ClientCare为此变量启用路径。

   事件类型：自定义分析 (s.prop)

   * 变量类型：自定义分析 (s.prop)

* **a.media.segment**

   （必需）收集视频区段数据，包括区段名称以及区段在视频中出现的顺序。此变量在自动跟踪播放器事件时通过启用 `segmentByMilestones` 变量来填充，或在手动跟踪播放器事件时通过设置自定义区段名称来填充。For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segment eVar.

   默认的视频数据收集方法在以下点收集数据：

   * 视频开始（播放）
   * 段开始
   * 视频结束（停止）

   Analytics在视图观看时，将第一个开始的访客计入该区段。 当分部开始时，后续分部视图。

   * 变量类型：eVar
   * 默认过期：页面查看


* **a.contentType**

   收集由访客查看的内容类型相关数据。由视频测量发送的点击将被分配“视频”的内容类型。 无需为视频跟踪专门保留此变量。 使用相同的变量让其他内容报告内容类型使您能够分析不同类型内容中的访客分布。 例如，您可以使用此变量通过“article”或“product page”之类的值标记其他内容类型。从视频测量的角度，内容类型允许您识别视频访客并计算视频转化率。

   * 变量类型：eVar
   * 默认过期：页面查看

* **a.media.timePlayed**

   以秒为单位，计算自上次数据收集流程（图像请求）以来，观看视频所花费的时间。

   * 变量类型：事件
   * 类型：计数器

* **a.media.view**

   表明访客已查看了视频的某些部分。但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

   * 变量： 事件
   * 类型：计数器

* **a.media.segmentView**

   表明访客已查看了视频区段的某些部分。但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

   * 变量类型：事件
   * 类型：计数器

* **a .media.complete**

   表明用户已查看了完整的视频。默认情况下，完整的事件会在视频结束前 1 秒进行测量。在实施过程中，您可以指定希望在距离视频结束有多少秒时被视为查看完成。对于直播视频和其他没有定义结尾的流，您可以指定一个测量完成的自定义点。例如，在查看特定时间后。

   * 变量类型：事件
   * 类型：计数器


## 配置媒体设置 {#section_929945D4183C428AAF3B983EFD3E2500}

使用您要用于跟踪视频的设置配置 `MediaSettings` 对象：

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## 跟踪播放器事件 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

要测量视频播放，需要在适当时调用 `Play`、`Stop` 和 `Close` 方法。例如，暂停播放器时，调用 `Stop`。开始或继续播放时，调用 `Play`。

## 类 {#section_16838332727348F990305C0C6B0D795C}

### 类：MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## 媒体测量类和方法引用 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **设置使用(winJS: 设置（使用）**

   通过指定的参数返回 `MediaSetting` 对象。

   * 以下是此方法的语法：

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith(winJS: adSettingsWith**

   返回用于跟踪广告视频的 `MediaSettings` 对象。

   * 以下是此方法的语法：

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **打开(winJS: 打开)**

   使用中定义的设置跟踪打开的媒体 `settings`。

   * 以下是此方法的语法：

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.open(mySettings); 
      ```

* **关闭(winJS: 关闭)**

   跟踪名称的媒体项的媒体关 *闭*。

   * 以下是此方法的语法：

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.close("mediaName");
      ```

* **播放(winJS: 播放)**

   跟踪以给定偏移量命名的媒 *`name`* 体项的媒 *体播* 放（以秒为单位）。

   * 以下是此方法的语法：

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **完整计划(winJS: 完成)**

   在提供的“offset”**&#x200B;时间（以秒为单位）将媒体项目手动标记为完成。

   * 以下是此方法的语法：

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **停止(winJS: 停止)**

   通知媒体模块已在给定的“offset”**&#x200B;时间停止或暂停视频。

   * 以下是此方法的语法：

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **单击(winJS: 单击)**

   通知媒体模块已单击媒体项目。

   * 以下是此方法的语法：

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **跟踪(winJS: 跟踪)**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 以下是此方法的语法：

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.track("mediaName", null);
      ```

