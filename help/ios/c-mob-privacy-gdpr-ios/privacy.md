---
description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-title: 设置用户的选择状态
solution: Experience Cloud,Analytics
title: 设置用户的选择状态
topic: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 84%

---


# 设置用户的选择状态 {#setting-the-user-s-opt-status}

此信息可以帮助您处理 GDPR 数据删除请求。

>[!IMPORTANT]
>
>从 Experience Cloud iOS SDK 4.15 开始，将隐私状态设置为 `unknown` 会保留 Audience Manager 和 Experience Cloud ID 点击量。

您可以使用以下设置控制设备上是否允许 Analytics、Target 和 Audience Manager 活动：

* [ADBMobile JSON 配置](/help/ios/configuration/json-config/json-config.md)中的 `privacyDefault`。

   此设置控制初始设置，除非在代码中进行更改，否则将一直保留初始设置。

* `setPrivacyStatus` 方法。

   使用此方法更改隐私设置后，更改将永久存在，直到再次使用此方法更改设置，或在您卸载并再次安装应用程序时更改。

   有关这些方法的详细信息，请参 [阅配置方法](/help/ios/configuration/json-config/json-config.md)。

以下是关于每种隐私状态的信息：

* **选择启用**

   * Analytics：发送点击。
   * Target：发送 Mbox 请求。
   * Audience Manager：发送信号和 ID 同步。
   * JSON 配置文件中的值：`optedin`
   * `setPrivacyStatus` 中的值：`ADBMobilePrivacyStatusOptIn`

* **选择禁用**

   * Analytics：丢弃点击。
   * Target：不允许发送 Mbox 请求。
   * Audience Manager：不允许发送信号和 ID 同步。
   * JSON 配置文件中的值：`optedout`
   * `setPrivacyStatus` 中的值：`ADBMobilePrivacyStatusOptOut`

* **未知**

   * Analytics：如果&#x200B;**启用了**&#x200B;离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。

      如果&#x200B;**未启用**&#x200B;离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   * Target：发送 Mbox 请求。
   * Audience Manager：发送信号和 ID 同步。
   * JSON 配置文件中的值：`optunknown`
   * `setPrivacyStatus` 中的值：`ADBMobilePrivacyStatusUnknown`

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

