---
description: 以下是有关在 Android 上使用视频测量解决方案测量视频的一些信息。
keywords: android；库；移动；sdk
seo-description: 以下是有关在 Android 上使用视频测量解决方案测量视频的一些信息。
seo-title: Video Analytics
solution: Marketing Cloud，Analytics
title: Video Analytics
topic: 开发人员和实施
uuid: a137cc27-dc28-48c0-b08 e-2ca17 d2 c7 e1 d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Video Analytics {#video-analytics}

以下是有关在 Android 上使用视频测量解决方案测量视频的一些信息。

>[!TIP]
>
>在视频播放过程中，会向此服务发送频繁的“心率”调用，以测量播放的时间。这些心率调用每 10 秒发送一次，从而生成精细的视频参与量度和更准确的视频流失报表。有关Adobe视频测量解决方案的更多信息，请参阅 [在Adobe Analytics中测量音频和视频](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)。

在所有平台中，测量视频的常规过程都非常相似。本文中的内容提供了开发人员任务概述以及代码示例。下表列出了发送到 Analytics 的媒体数据。处理规则用于将上下文数据映射到Analytics变量。

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * 变量类型：eVar
      * 默认过期：访问
      * 自定义分析（s.prop，用于视频路径）
   * （**必需**）当访客以某种方式查看视频时，此上下文数据变量会收集在实施中指定的视频名称。您可以为此变量添加分类。
   * （**可选**）自定义分析变量提供视频路径信息。

* **a.media.name**
   * 变量类型：自定义分析(s. prop)
   * （**可选**）提供视频路径信息。

      >[!IMPORTANT]
      >
      >Excare必须启用此变量的路径。
   * 事件类型：自定义分析 (s.prop)

* **a.media.segment**
   * 变量类型：eVar
   * 默认过期：页面查看
   * （**必需**）收集视频区段数据，包括区段名称以及区段在视频中出现的顺序。

      此变量在自动跟踪播放器事件时通过启用 `segmentByMilestones` 变量来填充，或在手动跟踪播放器事件时通过设置自定义区段名称来填充。For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the Segments eVar: `1:M:0-25`.

      默认视频数据收集方法在以下时间点收集数据：

      * 视频开始（播放）
      * 区段开始
      * 视频结束（停止）
      当访客开始观看时，Analytics 会在第一个区段开始时计数第一个区段查看次数。后续区段查看次数会在相应区段开始时进行计数。


* **a.contentType**
   * 变量类型：eVar
   * 默认过期：页面查看
   * 收集访客查看的内容类型相关数据。

      由视频测量发送的点击量将被分配内容类型 `video`。从视频测量的角度来看，**内容类型**&#x200B;使您能够识别视频访客，并计算视频转化率。

* **a.media.timePlayed**
   * 变量类型：Event
   * 类型：计数器
   * 计算自上次数据收集流程（图像请求）以来，观看视频所花费的时间（以秒为单位）。

* **a.media.view**
   * 变量类型：Event
   * 类型：计数器
   * 表明访客已查看了视频的某些部分。

      但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

* **a.media.segmentView**
   * 变量类型：Event
   * 类型：计数器
   * 表明访客已查看了视频区段的某些部分。

      但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

* **a .media.complete**
   * 变量类型：Event
   * 类型：计数器
   * 表明用户已查看了完整的视频。

      默认情况下，完整的事件会在视频结束前 1 秒进行测量。在实施过程中，您可以指定希望在距离视频结束有多少秒时被视为查看完成。对于直播视频和没有定义结尾的其他视频流，您可以指定一个自定义时间点来测量完成（例如，查看了特定时间之后）。


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

使用您要用于跟踪视频的设置配置 `MediaSettings` 对象：

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, the `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. 例如，暂停播放器时，调用 `mediaStop`。开始或继续播放时，调用 `mediaPlay`。

## 类 {#section_16838332727348F990305C0C6B0D795C}

**类：MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**类：MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Media Measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

以下是Media Measurement类中的方法：

* **settingsWith**

   通过指定的参数返回 `MediaSettings` 对象。

   * 下面是这种方法对应的语法：

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * 以下是这种方法的代码示例：

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   返回用于跟踪广告视频的 `MediaSettings` 对象。
   * 下面是这种方法对应的语法：

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   打开 `MediaSettings` 对象以进行跟踪。

   * 下面是这种方法对应的语法：

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      关闭名为“name”**&#x200B;的媒体项目。

      * 下面是这种方法对应的语法：
      ```java
      public static void close(String name);
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.close("name"); 
      ```


* **play**
   * 在给定的“offset”**&#x200B;时间（以秒为单位）播放名为“name”**&#x200B;的媒体项目。
   * 下面是这种方法对应的语法：

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **完成**

   在提供的“offset”**&#x200B;时间（以秒为单位）将媒体项目手动标记为完成。

   * 下面是这种方法对应的语法：

      ```java
      public static void complete(String name, double offset); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   通知媒体模块已在给定的“offset”**&#x200B;时间停止或暂停视频。

   * 下面是这种方法对应的语法：

      ```java
      public static void stop(String name, double offset); 
      ```

   * 下面是代码示例或此方法：

      ```java
      Media.stop("name", 0);
      ```

* **click**

   通知媒体模块已单击媒体项目。

   * 下面是这种方法对应的语法：

      ```java
      public static void click(String name double offset); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.click("name", 0);
      ```

* **track**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 下面是这种方法对应的语法：

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Media.track("name", null); 
      ```
