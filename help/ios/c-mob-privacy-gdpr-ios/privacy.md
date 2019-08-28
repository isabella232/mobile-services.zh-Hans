---
description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-title: 设置用户的选择状态
solution: Marketing Cloud，Analytics
title: 设置用户的选择状态
topic: 开发人员和实施
uuid: 44a09a25-93c6-4e1a-b69 e-710018e8 b6 c3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

此信息可以帮助您处理 GDPR 数据删除请求。

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

您可以使用以下设置控制设备上是否允许 Analytics、Target 和 Audience Manager 活动：

* `privacyDefault` 在 [AdobeMobile JSON配置](/help/ios/configuration/json-config/json-config.md)中。

   此设置控制初始设置，除非在代码中进行更改，否则将一直保留初始设置。

* `setPrivacyStatus` 方法。

   使用此方法更改隐私设置后，所做的更改会一直保持有效，直到使用此方法再次进行更改或者您卸载并重新安装应用程序为止。

   有关这些方法的更多信息，请参阅 [配置方法](/help/ios/configuration/json-config/json-config.md).

以下是有关各个隐私状态的信息：

* **选择启用**

   * Analytics：发送点击。
   * Target：发送 Mbox 请求。
   * Audience Manager：发送信号和 ID 同步。
   * Value in the JSON config file: `optedin`
   * 值： `setPrivacyStatus``ADBMobilePrivacyStatusOptIn`

* **选择禁用**

   * Analytics：丢弃点击。
   * Target：不允许发送 Mbox 请求。
   * Audience Manager：不允许发送信号和 ID 同步。
   * Value in the JSON config file: `optedout`
   * 值： `setPrivacyStatus``ADBMobilePrivacyStatusOptOut`

* **未知**

   * Analytics：如果&#x200B;**启用了**&#x200B;离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。

      如果&#x200B;**未启用**&#x200B;离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   * Target：发送 Mbox 请求。
   * Audience Manager：发送信号和 ID 同步。
   * Value in the JSON config file: `optunknown`
   * 值： `setPrivacyStatus``ADBMobilePrivacyStatusUnknown`

## 示例 {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```

