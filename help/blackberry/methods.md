---
description: BlackBerry库提供的类和方法。
seo-description: BlackBerry库提供的类和方法。
seo-title: Adobe移动类和方法参考
title: Adobe移动类和方法参考
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 55%

---


# Adobe移动类和方法参考 {#adobe-mobile-class-and-method-reference}

BlackBerry库提供的类和方法。

SDK目前支持Adobe Analytics，方法基于该解决方案位于不同的类中。

## SDK设置 {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   返回当前用户隐私状态的枚举表示形式。

   * ADBMobilePrivacyStatusOptIn —— 立即发送点击。
   * ADBMobilePrivacyStatusOptOut —— 丢弃点击。
   * ADBMobilePrivacyStatusUnknown —— 如果报表包启用了时间戳，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。 如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      默认值在 `ADBMobileConfig.json` 文件中设置。

   * 以下是此方法的语法：

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   将当前用户的隐私状态设置为 `status`。设置为以下值之一：

   * `ADBMobilePrivacyStatusOptIn` - 立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` - 丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` -如果报表包启用时间戳，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。 如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

   * 以下是此方法的语法：

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   如果设置了自定义标识符，则返回用户标识符。Returns `null` if a custom identifier is not set. 默认值为 `null`。

   * 以下是此方法的语法：

      ```cpp
      static QString getUserIdentifier();
      ```

   * 以下是此方法的代码示例：

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   将用户标识符设置为 `identifier`。

   * 以下是此方法的语法：

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   返回当前的调试日志记录首选项。默认值为 `false`。

   * 以下是此方法的语法：

      ```cpp
      static bool getDebugLogging();
      ```

   * 以下是此方法的代码示例：

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   将调试日志记录首选项设置为 `debugLogging`。

   * 以下是此方法的语法：

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * 以下是此方法的代码示例：

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/blackberry/metrics.md)。

   * 以下是此方法的语法：

      ```cpp
      static void collectLifecycleData();
      ```

   * 以下是此方法的代码示例：

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics 方法 {#section_91F4AD0A045D4E4E8F9A93450503E49E}

下面每个方法均可用来将数据发送至 Adobe Analytics 报表包。

* **trackState**

   通过可选的上下文数据跟踪应用程序状态。状态是您的应用程序中可用的视图，如“主仪表板”、“应用程序设置”、“购物车”等。 这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

   >[!TIP]
   >
   >只有此跟踪调用会递增页面查看次数。

   * 以下是此方法的语法：

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的代码示例：

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   跟踪您的应用程序中的操作。操作是您要衡量的应用程序中发生的事情，如“登录”、“横幅点击”、“源订阅”和其他指标。

   * 以下是此方法的语法：

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是此方法的代码示例：

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   发送当前的 x y 坐标。将事件替换为从BPS订户接收的事件。

   * 以下是此方法的语法：

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * 以下是此方法的代码示例：

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` 配置文件引用 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   （必需）一个或多个报表包以接收Analytics数据。 多个报表包 ID 应以逗号分隔，且中间不应有空格。

   以下是此变量的代码示例：

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (必需). 分析服务器。 应当使用不含 `https://` 或 `https://` 协议前缀的服务器域填充此变量。协议前缀由库根据变量自动处 `ssl` 理。 如果 `ssl` 为 `true`，则对此服务器进行安全连接。如果 `ssl` 为 `false`，则对此服务器进行非安全连接。

* **charset**

   定义您用于发送到Analytics的数据的字符集。 charset 用于将传入的数据转换为 UTF-8 以便进行存储和报告。

* **ssl**

   启用(`true`)或禁用(`false`)通过SSL(HTTPS)发送测量数据。 默认值为 `false`。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 报表包必须启用时间戳才能使用离线跟踪。

   >[!TIP]
   >
   >如果报表包已启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 `true`. 如果报表包未启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 false。如果未正确配置，数据将丢失。如果您不确定报表包是否启用时间戳，请与企业支 [持联系](https://helpx.adobe.com/cn/contact/enterprise-support.ec.html)。

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   默认值为 `false`。

* **lifecycleTimeout**

   指定在启动被视为新会话之前，应用程序启动之间必须经历的时长（以秒为单位）。 此超时也适用于应用程序被发送到后台后又重新启用的情况。应用程序在后台所用的时间不包括在会话时长中。

   默认值为300秒。

* **batchLimit**

   存储在队列中的脱机点击的最大数量。 默认值为0（无限制）。

* **privacyDefault**

   * `optedin` - 立即发送点击。
   * `optedout` - 丢弃点击。
   * `optunknown` -如果报表包启用时间戳，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。

      如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。
   此变量仅设置初始值。 如果在代码中设置或更改了此值，则新值将一直使用，直到其更改，或者卸载并重新安装应用程序。

   默认值为 `optedin`。

The following is an example of an `ADBMobileConfig.json` file:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
