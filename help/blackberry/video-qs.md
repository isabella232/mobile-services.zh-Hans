---
description: 在所有AppMeasurement平台上，衡量视频的一般过程都非常相似。 本节提供开发人员任务的基本概述以及代码示例。
seo-description: 在所有AppMeasurement平台上，衡量视频的一般过程都非常相似。 本节提供开发人员任务的基本概述以及代码示例。
seo-title: Video Analytics
title: Video Analytics
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 63%

---


# Video Analytics {#video-analytics}

在所有AppMeasurement平台上，衡量视频的一般过程都非常相似。 本节提供开发人员任务的基本概述以及代码示例。

For more information about Video measurement, see the [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/zh-Hans/media-analytics/using/media-overview.html) guide.  下表列出了发送到 Analytics 的媒体数据。使用处理规则将上下文数据变量列中的上下文数据映射到分析变量，如变量类型列中所述。

## 将播放器事件映射到 Analytics 变量

* **a.media.name**

   （必需）当访客以某种方式视图视频时，收集视频的名称（如实施中指定）。您可以为此变量添加分类。

   **（可选）Custom Insight** 变量提供视频路径信息。

   * 变量名称：eVar
      * 默认过期：访问
      * Custom Insight（s.prop，用于视频寻路）

* **a.media.name**

   （**可选**）提供视频路径信息。必须由ClientCare为此变量启用路径。

   * 事件类型：自定义分析 (s.prop)
   * Custom Insight

* **a.media.segment**

   (**Required**) Collects video segment data, including the segment name and the order in which the segment occurs in the video. 此变量在自动跟踪播放器事件时通过启用 `segmentByMilestones` 变量来填充，或在手动跟踪播放器事件时通过设置自定义区段名称来填充。

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. 默认的视频数据收集方法在视频开始（播放）、段开始和视频结束（停止）点收集数据。

   Analytics会在视图开始观看时，在区段的访客计算第一个区段开始。 当分部开始时，后续分部视图。

   * 变量类型：eVar
   * 默认过期：页面查看

* **a.contentType**

   收集由访客查看的内容类型相关数据。由视频测量发送的点击将被分配“视频”的内容类型。 无需为视频跟踪专门保留此变量。 使用相同的变量让其他内容报告内容类型使您能够分析不同类型内容中的访客分布。 例如，您可以使用此变量通过“article”或“product page”之类的值标记其他内容类型。从视频测量的角度来看，“内容类型”允许您识别视频访客，从而计算视频转化率。

   * 变量类型：eVar
   * 默认过期：页面查看

* **a.media.timePlayed**

   以秒为单位，计算自上次数据收集流程（图像请求）以来，观看视频所花费的时间。

   * 变量类型：事件
   * 类型：计数器

* **a.media.view**

   表明访客已查看了视频的某些部分。但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

   * 变量类型：事件
   * 类型：计数器

* **a.media.segmentView**

   表明访客已查看了视频区段的某些部分。但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

   * 变量类型：事件
   * 类型：计数器

* **a .media.complete**

   表明用户已查看了完整的视频。默认情况下，完整的事件会在视频结束前 1 秒进行测量。在实施过程中，您可以指定希望在距离视频结束有多少秒时被视为查看完成。对于直播视频和其他没有定义结尾的流，您可以指定一个测量完成的自定义点。例如，在查看特定时间后。

   * 变量类型：事件
   * 类型：计数器

## 跟踪播放器事件 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

要测量视频播放，需要在适当时调用 `mediaPlay`、`mediaStop` 和 `mediaClose` 方法。例如，暂停播放器时，调用 `mediaStop`。开始或继续播放时，调用 `mediaPlay`。

## 媒体测量类和方法引用 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   打开要跟踪的视频。

   * 以下是此方法的语法：

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * 以下是此方法的代码示例：

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   打开 `MediaSettings` 对象以进行跟踪。

   * 以下是此方法的语法：

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   关闭名为“”*`name`*&#x200B;的媒体项目。

   * 以下是此方法的语法：

      ```cpp
      void close(QString name);
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   在给定的“”*`name`*&#x200B;时间（以秒为单位）播放名为“”*`offset`*&#x200B;的媒体项目。

   * 以下是此方法的语法：

      ```cpp
      void play(QString name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **complete**

   在提供的“”*`offset`*&#x200B;时间（以秒为单位）将媒体项目手动标记为完成。

   * 以下是此方法的语法：

      ```cpp
      void complete(QString name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   通知媒体模块已在给定的“offset”**&#x200B;时间停止或暂停视频。

   * 以下是此方法的语法：

      ```cpp
      stop(QString name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   通知媒体模块已单击媒体项目。

   * 以下是此方法的语法：

      ```cpp
      void click(QString name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 以下是此方法的语法：

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
