---
description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-title: 设置用户的选择状态
solution: Experience Cloud,Analytics
title: 设置用户的选择状态
topic: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 67%

---


# 设置用户的选择状态{#setting-the-user-s-opt-status}

此信息可以帮助您处理 GDPR 数据删除请求。

>[!IMPORTANT]
>
>从 Android SDK 4.15 开始，将隐私状态设置为 `unknown` 将会保留 Audience Manager 和 Experience Cloud ID 点击量。

您可以使用以下设置控制设备上是否允许 Analytics、Target 和 Audience Manager 活动：

* [ADBMobile JSON 配置](/help/android/configuration/json-config/json-config.md)中的 `privacyDefault`。

   此设置控制初始设置，除非在代码中进行更改，否则将一直保留初始设置。

* `Config.setPrivacyStatus` 方法。

   使用此方法更改隐私设置后，此更改将保持有效，直到您再次更改它或您卸载并再次安装应用程序时为止。 有关这些方法的详细信息，请参 [阅配置方法](/help/android/configuration/methods.md)。

下表描述了每种隐私状态：

* **选择启用**

   * **分析**:将发送点击。
   * **目标**:发送Mbox请求。
   * **Audience Manager**:将发送信号和ID同步。
   * JSON 配置文件中的值：`optedin`
   * `setPrivacyStatus` 中的值：`MOBILE_PRIVACY_STATUS_OPT_IN`

* **选择禁用**

   * **分析**:将丢弃点击。
   * **目标**:不允许Mbox请求。
   * **Audience Manager**:不允许信号和ID同步。
   * JSON 配置文件中的值：`optedout`
   * `setPrivacyStatus` 中的值：`MOBILE_PRIVACY_STATUS_OPT_OUT`

* **未知**

   * **Analytics**：如果&#x200B;**启用了**&#x200B;离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。

      如果<b>未启用</b>离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。
   * **目标**:发送Mbox请求。
   * **Audience Manager**:将发送信号和ID同步。
   * JSON 配置文件中的值：`optunknown`
   * `setPrivacyStatus` 中的值：`MOBILE_PRIVACY_STATUS_UNKNOWN`

## 示例 {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```

