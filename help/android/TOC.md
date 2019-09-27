---
product: 移动服务
audience: 最终用户
user-guide-title: Mobile Services android帮助
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android Help{#android}

+ [适用于 Experience Cloud 解决方案的 Android SDK 4.x](overview.md)
+ [发行说明](rel-notes.md)
+ 入门指南{#getting-started-android}
   + [入门指南](getting-started/getting-started.md)
   + [开始之前](getting-started/requirements.md)
   + [核心实施和生命周期](getting-started/dev-qs.md)
   + [Processing rules and context data](getting-started/proc-rules.md)
   + [迁移至 Android 4.x 库](getting-started/migration-v3.md)
+ 配置{#configuration-android}
   + [Configuration overview](configuration/configuration.md)
   + [ADBMobile JSON config file](configuration/json-config/json-config.md)
   + [覆盖ADBMobile JSON配置路径](configuration/json-config/json-config-remote.md)
   + [对点击量进行批处理](configuration/hit-batching.md)
   + [配置方法](configuration/methods.md)
+ [生命周期指标](metrics.md)
+ Analytics{#analytics-android}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [跟踪应用程序状态](analytics-main/states.md)
   + [跟踪应用程序操作](analytics-main/actions.md)
   + [跟踪应用程序的崩溃情况](analytics-main/crashes.md)
   + [定时操作](analytics-main/timed-actions.md)
   + [访客终身价值](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [产品变量](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回发{#postbacks}
      + [Postbacks overview](analytics-main/postbacks/postbacks.md)
      + [回发示例](analytics-main/postbacks/postback-example.md)
      + [PII 回发](analytics-main/postbacks/c-pii-postbacks.md)
   + [分析方法](analytics-main/analytics-methods.md)
+ 客户获取{#acquisition-android}
   + [Acquisition overview](acquisition-main/acquisition-main-android.md)
   + [移动App客户获取](acquisition-main/acquisition.md)
   + [获取方法](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [跟踪深层链接](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracking third-party deferred deep links](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [测试Marketing Link赢取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [测试V3客户获取](acquisition-main/t-testing-version-3-acquisition.md)
   + [测试旧版客户获取](acquisition-main/t-testing-acquisition.md)
   + [客户获取测试疑难解答](acquisition-main/troubleshoot-acquisition-testing.md)
+ 消息传送{#messaging-android}
   + [消息传递概述](messaging-main/messaging-main-android.md)
   + 应用程序内消息传送{#inapp-messaging}
      + [应用程序内消息传送](messaging-main/messaging/messaging.md)
      + [应用程序内消息处理疑难解答](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [推送消息](messaging-main/push-messaging/push-messaging.md)
      + [Implement push messaging with deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Receive rich push notifications](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [推送消息疑难解答](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置{#location}
   + [位置概述](location/location.md)
   + [Geo-location and points of interest](location/geo-poi.md)
   + [信标跟踪](location/beacon.md)
+ Target{#target-android}
   + [Target概述](target-main/target-main.md)
   + [Target configuration](target-main/target.md)
   + [目标方法](target-main/c-target-methods.md)
   + [在 Android 中预取选件内容](target-main/c-mob-target-prefetch-android.md)
   + [Android 上的“Target 预览”功能](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Experience cloud概述](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID配置](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity service方法](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud 设备协作](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Audience manager概述](audience-manager/audience-manager.md)
   + [Audience manager配置](audience-manager/audiencemgmt.md)
   + [Audience Manager methods](audience-manager/c-audience-manager-methods.md)
+ 可穿戴应用程序{#wearables-android}
   + [可穿戴设备概述](wearables/wearables.md)
   + [Android可穿戴设备：入门](wearables/android-wearable.md)
   + [Android可穿戴设备：附加说明](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Android SDK参考概述](/help/android/reference/reference.md)
   + [应用程序 ID](/help/android/reference/app-ids.md)
   + [在应用程序和移动Web之间跟踪访客](/help/android/reference/hybrid-app.md)
   + [Android构件](/help/android/reference/widgets.md)
+ 隐私和通用数据保护条例{#gdpr-privacy-android}
   + [隐私和GDPR概述](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Retrieving stored identifiers](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [设置用户的选择状态](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap 插件{#phonegap-android}
   + [PhoneGap插件概述](phonegap/phonegap.md)
   + [PhoneGap插件方法](phonegap/phonegap-methods.md)
