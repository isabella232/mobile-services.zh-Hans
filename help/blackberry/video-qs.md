---
description: 在所有 AppMeasurement 平台中，测量视频的大概过程都非常相似。This section provides a basic overview of the developer tasks along with code samples.
seo-description: 在所有 AppMeasurement 平台中，测量视频的大概过程都非常相似。本节提供开发人员任务的基本概述以及代码示例。
seo-title: Video Analytics
title: Video Analytics
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Video Analytics {#video-analytics}

在所有 AppMeasurement 平台中，测量视频的大概过程都非常相似。本节提供开发人员任务的基本概述以及代码示例。

For more information about Video measurement, see the [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) guide.  下表列出了发送到 Analytics 的媒体数据。请使用处理规则将“上下文数据变量”列中的上下文数据映射到“变量类型”列中所述的 Analytics 变量。

## Map player events to Analytics variables

* **a.media.name**

   （必需）当访客以某种方式查看视频时，收集在实施中指定的视频名称。您可以为此变量添加分类。

   **（可选）** “自定义分析”变量提供视频路径信息。

   * Variable name: eVar
      * 默认过期：访问
      * 自定义分析（s.prop，用于视频路径）

* **a.media.name**

   （**可选**）提供视频路径信息。必须由 ClientCare 为此变量启用路径。

   * 事件类型：自定义分析 (s.prop)
   * 自定义分析 (s.prop)

* **a.media.segment**

   （**必需**）收集视频区段数据，包括区段名称以及区段在视频中出现的顺序。此变量在自动跟踪播放器事件时通过启用 `segmentByMilestones` 变量来填充，或在手动跟踪播放器事件时通过设置自定义区段名称来填充。

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. 默认的视频数据收集方法在视频开始（播放）、段开始和视频结束（停止）点收集数据。

   当访客开始观看时，Analytics 会在第一个区段开始时计数第一个区段查看次数。后续区段查看次数会在相应区段开始时进行计数。

   * Variable type: eVar
   * 默认过期：页面查看

* **a.contentType**

   收集由访客查看的内容类型相关数据。由视频测量发送的点击量将被分配内容类型“视频”。此变量不需要专门为视频跟踪而进行保留。通过使用此相同变量让其他内容报告内容类型，您可以分析访客在不同内容类型之间的分布。例如，您可以使用此变量通过“article”或“product page”之类的值标记其他内容类型。从视频测量的角度来看，内容类型允许您识别视频访客，从而计算视频转化率。

   * Variable type: eVar
   * 默认过期：页面查看

* **a.media.timePlayed**

   以秒为单位，计算自上次数据收集流程（图像请求）以来，观看视频所花费的时间。

   * Variable type: Event
   * 类型：计数器

* **a.media.view**

   表明访客已查看了视频的某些部分。但是它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

   * Variable type: Event
   * 类型：计数器

* **a.media.segmentView**

   表明访客已查看了视频区段的某些部分。但是它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

   * Variable type: Event
   * 类型：计数器

* **a .media.complete**

   表明用户已查看了完整的视频。默认情况下，完整的事件会在视频结束前 1 秒进行测量。在实施过程中，您可以指定希望在距离视频结束有多少秒时被视为查看结束。对于实时视频和其他未定义结尾的流，您可以指定一个自定义时间点来测量结束。例如，在查看了特定时间之后。

   * 变量类型：活动
   * 类型：计数器

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. 例如，暂停播放器时，调用 `mediaStop`。开始或继续播放时，调用 `mediaPlay`。

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   打开视频以进行跟踪。

   * 下面是这种方法对应的语法：

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * 以下是这种方法的代码示例：

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   打开 `MediaSettings` 对象以进行跟踪。

   * 下面是这种方法对应的语法：

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Closes the media item named *`name`*.

   * 下面是这种方法对应的语法：

      ```cpp
      void close(QString name);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * 下面是这种方法对应的语法：

      ```cpp
      void play(QString name, double offset);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **完成**

   在提供的“”*`offset`时间（以秒为单位）将媒体项目手动标记为完成。*

   * 下面是这种方法对应的语法：

      ```cpp
      void complete(QString name, double offset);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   通知媒体模块已在给定的“offset”**&#x200B;时间停止或暂停视频。

   * 下面是这种方法对应的语法：

      ```cpp
      stop(QString name, double offset);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   通知媒体模块已单击媒体项目。

   * 下面是这种方法对应的语法：

      ```cpp
      void click(QString name, double offset);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 下面是这种方法对应的语法：

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
