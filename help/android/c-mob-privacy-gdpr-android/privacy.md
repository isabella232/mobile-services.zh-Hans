---
description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-description: 此信息可以帮助您处理 GDPR 数据删除请求。
seo-title: 设置用户的选择状态
solution: Marketing Cloud,Analytics
title: Setting the user's opt status
topic: 开发人员和实施
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

此信息可以帮助您处理 GDPR 数据删除请求。

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

您可以使用以下设置控制设备上是否允许 Analytics、Target 和 Audience Manager 活动：

* `privacyDefault` 在 [ADBMobile JSON配置中](/help/android/configuration/json-config/json-config.md)。

   此设置控制初始设置，除非在代码中进行更改，否则将一直保留初始设置。

* 方 `Config.setPrivacyStatus` 法。

   使用此方法更改隐私设置后，所做的更改会一直保持有效，直到再次更改隐私设置或者您卸载并重新安装应用程序为止。有关这些方法的更多信息，请参阅 [配置方法](/help/android/configuration/methods.md).

下表描述了每种隐私状态：

* **选择启用**

   * **Analytics**：发送点击。
   * **Target**：发送 Mbox 请求。
   * **Audience Manager**：发送信号和 ID 同步。
   * Value in the JSON Config file: `optedin`
   * 以下项中的 `setPrivacyStatus`值： `MOBILE_PRIVACY_STATUS_OPT_IN`

* **选择禁用**

   * **Analytics**：丢弃点击。
   * **Target**：不允许发送 Mbox 请求。
   * **Audience Manager**：不允许发送信号和 ID 同步。
   * Value in the JSON config file: `optedout`
   * 以下项中的 `setPrivacyStatus`值： `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Unknown**

   * **分析**:如果启用脱 **机跟踪**，则会保存点击，直到隐私状态更改为选择加入（发送点击）或选择退出（丢弃点击）。

      如果<b>未启用</b>离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。
   * **Target**：发送 Mbox 请求。
   * **Audience Manager**：发送信号和 ID 同步。
   * Value in the JSON config file: `optunknown`
   * 以下项中的 `setPrivacyStatus`值： `MOBILE_PRIVACY_STATUS_UNKNOWN`

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

