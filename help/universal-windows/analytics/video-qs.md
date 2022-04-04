---
description: 可帮助您使用Video Analytics的信息。
solution: Experience Cloud Services,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: f45dac3b-cd2e-4fba-a3b2-c243640ecfa4
exl-id: bf7a2936-4a90-4630-8a0c-df41baa1d6a8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 71%

---

# Video Analytics {#video-analytics}

可帮助您使用Video Analytics的信息。

视频测量在 [在Adobe Analytics中测量流媒体](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=zh-Hans) 的双曲余切值。 在所有AppMeasurement平台中，测量视频的一般过程都非常相似。 此快速入门部分提供了开发人员任务的基本概述以及代码示例。

下表列出了发送到 Analytics 的媒体数据。使用处理规则将上下文数据映射到 Analytics 变量。

* **a.media.name**

   (**必需**)在访客以某种方式查看视频时收集实施中指定的视频名称。您可以为此变量添加分类。

   （**可选**）自定义分析变量可提供视频路径信息。

   * 变量类型：eVar
   * 默认过期：访问
   * 自定义分析（s.prop，用于确定视频路径）

* **a.media.name**

   （**可选**）提供视频路径信息。必须由客户关怀代表为此变量启用路径。

   * 事件类型：自定义分析 (s.prop).
   * 变量类型：自定义分析 (s.prop)

* **a.media.segment**

   （**必需**）收集视频区段数据，包括区段名称以及区段在视频中出现的顺序。

   此变量在自动跟踪播放器事件时通过启用 `segmentByMilestones` 变量来填充，或在手动跟踪播放器事件时通过设置自定义区段名称来填充。例如，当访客查看视频中的第一个区段时，SiteCatalyst可能会在 `1:M:0-25` 区段eVar。

   默认的视频数据收集方法会在以下时间点收集数据：视频开始（播放）、区段开始和视频结束（停止）。 Analytics 会在访客开始观看时，将区段的开始计为第一个区段视图。在区段开始播放后，则计为后续区段视图。

   * 变量类型：eVar
   * 默认过期：页面查看

* **a.contentType**

   收集由访客查看的内容类型相关数据。由视频测量发送的点击量会被分配内容类型“video”。 无需专门为视频跟踪保留此变量。 通过使用此相同变量让其他内容报告内容类型，您可以分析访客在不同内容类型之间的分布。 例如，您可以使用此变量通过“article”或“product page”之类的值标记其他内容类型。

   从视频测量的角度来看，“内容类型”允许您识别视频访客，从而计算视频转化率。

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

### 媒体测量类和方法引用 {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith(winJS:settingsWith)**

   通过指定的参数返回 `MediaSettings` 对象。

   * 以下是此方法的语法：

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^playerID); 
      ```

   * 以下是此方法的代码示例：

      ```js
      var  mySettings  =  ADB.Media.settingsWith("name", 10,  "playerName", "playerId"); 
      ```

* **AdSettingsWith(winJS:adSettingsWith)**

   返回用于跟踪广告视频的 `MediaSettings` 对象。

   * 以下是此方法的语法：

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name,  double length, Platform::String ^playerName, Platform::String  ^parentName, Platform::String ^parentPod, double parentPosition,  Platform::String ^CPM);
      ```

   * 以下是此方法的代码示例：

      ```js
      var  myAdSettings = ADB.Media.adSettingsWith("name", 10,  "playerName", "parentName", "parentPod", 5, "myCPM");
      ```

* **打开(winJS:open)**

   使用 `settings`.

   * 以下是此方法的语法：

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.open(mySettings);
      ```

* **关闭(winJS:close)**

   跟踪名为的媒体项目的媒体关闭 *`name`*.

   * 以下是此方法的语法：

      ```csharp
      static  void  Close(Platform::String  ^name);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.close("mediaName"); 
      ```

* **播放(winJS:play)**

   跟踪名为的媒体项目的媒体播放 *`name`* 在给定 *偏移* （以秒为单位）。

   * 以下是此方法的语法：

      ```csharp
      static  void  Play(Platform::String ^name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.play("mediaName",  0);
      ```

* **完成(winJS:complete)**

   在提供的“offset”**&#x200B;时间（以秒为单位）将媒体项目手动标记为完成。

   * 以下是此方法的语法：

      ```csharp
      static  void  Complete(Platform::String ^name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.complete("mediaName", 8);
      ```

* **停止(winJS:stop)**

   通知媒体模块已在给定的“offset”**&#x200B;时间停止或暂停视频。

   * 以下是此方法的语法：

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.stop("mediaName",  4);
      ```

* **单击(winJS:单击)**

   通知媒体模块已单击媒体项目。

   * 以下是此方法的语法：

      ```csharp
      static void Click(Platform::String ^name, double  offset);
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.click("mediaName",  3); 
      ```

* **跟踪(winJS:track)**

   发送用于获取当前媒体状态的跟踪操作调用（无页面查看）。

   * 以下是此方法的语法：

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^,  Platform::Object> ^contextData); 
      ```

   * 以下是此方法的代码示例：

      ```js
      ADB.Media.track("mediaName",  null);
      ```
