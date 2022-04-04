---
description: 以下是有关在 Android 上使用视频测量解决方案测量视频的一些信息。
keywords: Android;库;移动;SDK
solution: Experience Cloud Services,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
exl-id: 1b7f5523-767a-45e8-b2e7-ecf9984849e4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 98%

---

# Video Analytics {#video-analytics}

以下是有关在 Android 上使用视频测量解决方案测量视频的一些信息。

>[!TIP]
>
>在视频播放过程中，会向此服务发送频繁的“心率”调用，以测量播放的时间。这些心率调用每 10 秒发送一次，从而生成精细的视频参与量度和更准确的视频流失报表。有关Adobe视频测量解决方案的更多信息，请参阅 [在Adobe Analytics中测量流媒体](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=zh-Hans).

在所有平台中，测量视频的常规过程都非常相似。本文中的内容提供了开发人员任务概述以及代码示例。下表列出了发送到 Analytics 的媒体数据。处理规则用于将上下文数据映射到 Analytics 变量。

## 将播放器事件映射到 Analytics 变量 {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * 变量类型：eVar
      * 默认过期：访问
      * 自定义分析（s.prop，用于确定视频路径）
   * （**必需**）当访客以某种方式查看视频时，此上下文数据变量将按照实施中指定的方式收集视频名称。您可以为此变量添加分类。
   * （**可选**）自定义分析变量可提供视频路径信息。

* **a.media.name**
   * 变量类型：自定义分析 (s.prop)
   * （**可选**）提供视频路径信息。

      >[!IMPORTANT]
      >
      >必须由 ExpCare 为此变量启用路径。
   * 事件类型：自定义分析 (s.prop)

* **a.media.segment**
   * 变量类型：eVar
   * 默认过期：页面查看
   * （**必需**）收集视频区段数据，包括区段名称以及区段在视频中出现的顺序。

      此变量在自动跟踪播放器事件时通过启用 `segmentByMilestones` 变量来填充，或在手动跟踪播放器事件时通过设置自定义区段名称来填充。例如，当访客查看视频中的第一个区段时，SiteCatalyst 可能会在区段 eVar 中收集以下信息：`1:M:0-25`。

      默认的视频数据收集方法会在以下节点收集数据：

      * 视频开始（播放）
      * 区段开始
      * 视频结束（停止）

      Analytics 会在访客开始观看时，将区段的开始计为第一个区段视图。在区段开始播放后，则计为后续区段视图。


* **a.contentType**
   * 变量类型：eVar
   * 默认过期：页面查看
   * 收集访客查看的内容类型相关数据。

      由视频测量发送的点击量将被分配内容类型 `video`。从视频测量的角度来看，**内容类型**&#x200B;使您能够识别视频访客，并计算视频转化率。

* **a.media.timePlayed**
   * 变量类型：事件
   * 类型：计数器
   * 以秒为单位，计算自上次数据收集流程（图像请求）以来观看视频所花费的时间。

* **a.media.view**
   * 变量类型：事件
   * 类型：计数器
   * 表明访客已查看了视频的某些部分。

      但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

* **a.media.segmentView**
   * 变量类型：事件
   * 类型：计数器
   * 表明访客已查看了视频区段的某些部分。

      但是，它并不提供有关访客查看了视频中的多少内容或哪一部分的信息。

* **a .media.complete**
   * 变量类型：事件
   * 类型：计数器
   * 表明用户已查看了完整的视频。

      默认情况下，完整的事件会在视频结束前 1 秒进行测量。在实施过程中，您可以指定希望在距离视频结束还剩多少秒时被视为已完成观看。对于直播视频和其他没有明确定义结束时间的流，您可以指定一个自定义的点来测量完成情况（例如，当观看了指定时间后即可认为已看完视频）。


## 配置媒体设置 {#section_929945D4183C428AAF3B983EFD3E2500}

使用您要用于跟踪视频的设置配置 `MediaSettings` 对象：

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## 跟踪播放器事件 {#section_C7F43AECBC0D425390F7FCDF3035B65D}

要测量视频播放，需要在适当时调用 `mediaPlay`、`mediaStop` 和 `mediaClose` 方法。例如，暂停播放器时，调用 `mediaStop`。开始或继续播放时，调用 `mediaPlay`。

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

## 媒体测量类和方法引用 {#section_50DF9359A7B14DF092634C8E913C77FE}

以下是媒体测量类中的方法：

* **settingsWith**

   通过指定的参数返回 `MediaSettings` 对象。

   * 以下是此方法的语法：

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * 以下是此方法的代码示例：

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   返回用于跟踪广告视频的 `MediaSettings` 对象。
   * 以下是此方法的语法：

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   打开 `MediaSettings` 对象以进行跟踪。

   * 以下是此方法的语法：

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      关闭名为“name”**&#x200B;的媒体项目。

      * 以下是此方法的语法：

      ```java
      public static void close(String name);
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.close("name"); 
      ```


* **play**
   * 在给定的“offset”**&#x200B;时间（以秒为单位）播放名为“name”**&#x200B;的媒体项目。
   * 以下是此方法的语法：

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **complete**

   在提供的“offset”**&#x200B;时间（以秒为单位）将媒体项目手动标记为完成。

   * 以下是此方法的语法：

      ```java
      public static void complete(String name, double offset); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   通知媒体模块已在给定的“offset”**&#x200B;时间停止或暂停视频。

   * 以下是此方法的语法：

      ```java
      public static void stop(String name, double offset); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.stop("name", 0);
      ```

* **click**

   通知媒体模块已单击媒体项目。

   * 以下是此方法的语法：

      ```java
      public static void click(String name double offset); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.click("name", 0);
      ```

* **track**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 以下是此方法的语法：

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Media.track("name", null); 
      ```
