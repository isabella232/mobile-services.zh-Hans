---
product: mobile-services
audience: end-user
user-guide-title: Mobile Services Android 指南
breadcrumb-title: Android指南
translation-type: tm+mt
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 99%

---


# Mobile Services Android 指南{#android}

+ [适用于 Experience Cloud 解决方案的 Android SDK 4.x](overview.md)
+ [发行说明](rel-notes.md)
+ 入门指南{#getting-started-android}
   + [入门指南](getting-started/getting-started.md)
   + [开始之前](getting-started/requirements.md)
   + [核心实施和生命周期](getting-started/dev-qs.md)
   + [处理规则和上下文数据](getting-started/proc-rules.md)
   + [迁移至 Android 4.x 库](getting-started/migration-v3.md)
+ 配置{#configuration-android}
   + [配置概述](configuration/configuration.md)
   + [ADBMobile JSON 配置文件](configuration/json-config/json-config.md)
   + [覆盖 ADBMobile JSON 配置路径](configuration/json-config/json-config-remote.md)
   + [点击批量处理](configuration/hit-batching.md)
   + [配置方法](configuration/methods.md)
+ [生命周期量度](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics 概述](analytics-main/analytics-main.md)
   + [跟踪应用程序状态](analytics-main/states.md)
   + [跟踪应用程序操作](analytics-main/actions.md)
   + [跟踪应用程序的崩溃情况](analytics-main/crashes.md)
   + [定时操作](analytics-main/timed-actions.md)
   + [访客生命周期值](analytics-main/lifetime-value.md)
   + Products 变量{#products-variable}
      + [Products 变量](analytics-main/products/products.md)
      + [具有促销 eVar 和产品特定事件的 Products 变量](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回发{#postbacks}
      + [回发概述](analytics-main/postbacks/postbacks.md)
      + [回发示例](analytics-main/postbacks/postback-example.md)
      + [PII 回发](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analytics 方法](analytics-main/analytics-methods.md)
+ 客户获取{#acquisition-android}
   + [客户获取概述](acquisition-main/acquisition-main-android.md)
   + [移动设备应用程序客户获取](acquisition-main/acquisition.md)
   + [客户获取方法](acquisition-main/acquisition-methods.md)
   + 跟踪深层链接{#tracking-deep-links}
      + [跟踪深层链接](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [跟踪第三方延期深层链接](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [测试营销链接客户获取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [测试 V3 客户获取](acquisition-main/t-testing-version-3-acquisition.md)
   + [测试旧版客户获取](acquisition-main/t-testing-acquisition.md)
   + [排查客户获取测试问题](acquisition-main/troubleshoot-acquisition-testing.md)
+ 消息传送{#messaging-android}
   + [消息传送概述](messaging-main/messaging-main-android.md)
   + 应用程序内消息传送{#inapp-messaging}
      + [应用程序内消息传送](messaging-main/messaging/messaging.md)
      + [排查应用程序内消息传送问题](messaging-main/messaging/in-apps-ts.md)
   + 推送消息{#push-messaging}
      + [推送消息](messaging-main/push-messaging/push-messaging.md)
      + [实施包含深层链接的推送消息](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [接收富推送通知](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [排查推送消息问题](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置{#location}
   + [位置概述](location/location.md)
   + [地理位置和目标点](location/geo-poi.md)
   + [信标跟踪](location/beacon.md)
+ Target{#target-android}
   + [Target 概述](target-main/target-main.md)
   + [Target 配置](target-main/target.md)
   + [Target 方法](target-main/c-target-methods.md)
   + [在 Android 中预取选件内容](target-main/c-mob-target-prefetch-android.md)
   + [Android 上的“Target 预览”功能](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience Cloud 概述](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID 配置](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service 方法](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud 设备协作](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience Manager 概述](audience-manager/audience-manager.md)
   + [Audience Manager 配置](audience-manager/audiencemgmt.md)
   + [Audience Manager 方法](audience-manager/c-audience-manager-methods.md)
+ 可穿戴应用程序{#wearables-android}
   + [可穿戴应用程序概述](wearables/wearables.md)
   + [Android 可穿戴应用程序：快速入门](wearables/android-wearable.md)
   + [Android 可穿戴应用程序：其他说明](wearables/c-android-wearables--additional-notes.md)
+ Android SDK 参考{#sdk-reference-android}
   + [Android SDK 参考概述](/help/android/reference/reference.md)
   + [应用程序 ID](/help/android/reference/app-ids.md)
   + [应用程序和移动 Web 之间的访客跟踪](/help/android/reference/hybrid-app.md)
   + [Android 小组件](/help/android/reference/widgets.md)
+ 隐私和《通用数据保护条例》{#gdpr-privacy-android}
   + [隐私和 GDPR 概述](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [检索存储的标识符](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [设置用户的选择状态](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap 插件{#phonegap-android}
   + [PhoneGap 插件概述](phonegap/phonegap.md)
   + [PhoneGap 插件方法](phonegap/phonegap-methods.md)
