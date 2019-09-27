---
description: BlackBerry库提供的类和方法。
seo-description: BlackBerry库提供的类和方法。
seo-title: Adobe Mobile类和方法参考
title: Adobe Mobile类和方法参考
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

BlackBerry库提供的类和方法。

SDK当前支持Adobe Analytics，并且方法基于该解决方案位于不同的类中。

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   返回当前用户隐私状态的枚举表示形式。

   * ADBMobilePrivacyStatusOptIn - 立即发送点击。
   * ADBMobilePrivacyStatusOptOut - 丢弃点击。
   * ADBMobilePrivacyStatusUnknown - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（随后将发送点击）或选择禁用（随后将丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      默认值在 `ADBMobileConfig.json` 文件中设置。

   * 下面是这种方法对应的语法：

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   将当前用户的隐私状态设置为 `status`。设置为以下值之一：

   * `ADBMobilePrivacyStatusOptIn` -立即发送点击。
   * `ADBMobilePrivacyStatusOptOut` -丢弃点击。
   * `ADBMobilePrivacyStatusUnknown` - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（随后将发送点击）或选择禁用（随后将丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

   * 下面是这种方法对应的语法：

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   如果设置了自定义标识符，则返回用户标识符。Returns `null` if a custom identifier is not set. 默认值为 `null`.

   * 下面是这种方法对应的语法：

      ```cpp
      static QString getUserIdentifier();
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   将用户标识符设置为 `identifier`。

   * 下面是这种方法对应的语法：

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   返回当前的调试日志记录首选项。默认值为 `false`.

   * 下面是这种方法对应的语法：

      ```cpp
      static bool getDebugLogging();
      ```

   * 以下是这种方法的代码示例：

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   将调试日志记录首选项设置为 `debugLogging`。

   * 下面是这种方法对应的语法：

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * 以下是这种方法的代码示例：

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/blackberry/metrics.md)。

   * 下面是这种方法对应的语法：

      ```cpp
      static void collectLifecycleData();
      ```

   * 以下是这种方法的代码示例：

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

下面每个方法均可用来将数据发送至 Adobe Analytics 报表包。

* **trackState**

   通过可选的上下文数据跟踪应用程序状态。状态是指您的应用程序中提供的各种视图，例如“主页功能板”、“应用程序设置”、“购物车”等。这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

   >[!TIP]
   >
   >This is the only tracking call that increments page views.

   * 下面是这种方法对应的语法：

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是这种方法的代码示例：

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   跟踪您的应用程序中的操作。操作是指您的应用程序中发生的要测量的事件，例如“登录”、“横幅点按”、“信息源订阅”及其他量度。

   * 下面是这种方法对应的语法：

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * 以下是这种方法的代码示例：

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   发送当前的 x y 坐标。将事件替换为从 BPS 的订阅者处收到的事件。

   * 下面是这种方法对应的语法：

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * 以下是这种方法的代码示例：

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` config file reference {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   （必需）一个或多个用于接收 Analytics 数据的报表包。多个报表包 ID 应当以逗号分隔，且彼此之间没有空格。

   以下是此变量的代码示例：

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (必需). Analytics 服务器。This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. 协议前缀将由库根据 `ssl` 变量自动处理。如果 `ssl` 为 `true`，则对此服务器进行安全连接。如果 `ssl` 为 `false`，则对此服务器进行非安全连接。

* **charset**

   定义将用于发送到 Analytics 的数据的字符集。charset 用于将传入的数据转换为 UTF-8 以便进行存储和报告。

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). 默认值为 `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 报表包必须启用时间戳才能使用离线跟踪。

   >[!TIP]
   >
   >如果报表包已启用时间戳，那么您的 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 `true`. 如果您的报表包未启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 false。如果配置不正确，数据将会丢失。如果您不确定报表包是否已启用时间戳， 联系 [企业支持](https://helpx.adobe.com/contact/enterprise-support.ec.html)。

   如果您当前向某个报表包报告 AppMeasurement 数据，而该报表包也从 JavaScript 收集数据，则您可能需要为移动设备数据设置一个单独的报表包，或使用 `s.timestamp` 变量在所有 JavaScript 点击中包含自定义时间戳。

   默认值为 `false`.

* **lifecycleTimeout**

   指定应用程序在后一次启动时，必须与前一次启动间隔多长时间，才能被视为新会话（以秒为单位）。此超时也适用于应用程序被发送到后台后又重新启用的情况。会话时间长度不包括应用程序在后台中运行的时间。

   默认值为 300 秒。

* **batchLimit**

   队列中存储的离线点击的最大数量。默认值为0（无限制）。

* **privacyDefault**

   * `optedin` -立即发送点击。
   * `optedout` -丢弃点击。
   * `optunknown` - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（随后将发送点击）或选择禁用（随后将丢弃点击）。

      如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。
   此变量仅设置初始值。 如果曾在代码中设置或更改此值，则之后会一直使用新值，直到它发生更改，或应用程序被卸载后又重新安装时为止。

   默认值为 `optedin`.

以下是 `ADBMobileConfig.json` 文件的示例：

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
