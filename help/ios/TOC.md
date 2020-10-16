---
product: mobile-services
audience: end-user
user-guide-title: Mobile Services iOS 指南
breadcrumb-title: iOS指南
translation-type: tm+mt
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 99%

---


# Mobile Services iOS 指南{#ios}

+ [适用于 Experience Cloud 解决方案的 iOS SDK 4.x](overview.md)
+ [发行说明](rel-notes.md)
+ 入门指南 {#getting-started-ios}
   + [入门指南概述](getting-started/getting-started.md)
   + [开始之前](getting-started/requirements.md)
   + [核心实施和生命周期](getting-started/dev-qs.md)
   + [处理规则和上下文数据](getting-started/proc-rules.md)
   + [Swift 集成](getting-started/swift-integration.md)
   + [迁移至 4.x iOS 库](getting-started/migration-v3.md)
+ 配置 {#config-ios}
   + [配置概述](configuration/configuration.md)
   + [ADBMobile JSON 配置](configuration/json-config/json-config.md)
   + [覆盖 ADBMobile JSON 配置路径](configuration/json-config/json-config-remote.md)
   + [点击批量处理](configuration/hit-batching.md)
   + [配置方法](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [生命周期量度](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics 概述](analytics-main/analytics-main.md)
   + [跟踪应用程序状态](analytics-main/states.md)
   + [跟踪应用程序操作](analytics-main/actions.md)
   + [跟踪应用程序的崩溃情况](analytics-main/crashes.md)
   + [定时操作](analytics-main/timed-actions.md)
   + [访客生命周期值](analytics-main/lifetime-value.md)
   + Products 变量 {#products-variable}
      + [Products 变量](analytics-main/products/products.md)
      + [具有促销 eVar 和产品特定事件的 Products 变量](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回发 {#postbacks}
      + [回发概述](analytics-main/postback/postback.md)
      + [回发示例](analytics-main/postback/postback-example.md)
      + [PII 回发](analytics-main/postback/c-pii-postbacks.md)
   + [Analytics 方法](analytics-main/analytics-methods.md)
+ 客户获取 {#acquisition-ios}
   + [客户获取概述](acquisition-main/acquisition-main.md)
   + [移动设备应用程序客户获取](acquisition-main/acquisition.md)
   + [客户获取方法](acquisition-main/c-acquisition-methods.md)
   + 跟踪深层链接 {#tracking-deep-links}
      + [跟踪深层链接](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [跟踪第三方延期深层链接](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [测试营销链接客户获取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [测试 V3 客户获取](acquisition-main/t-testing-version-3-acquisition.md)
   + [测试旧版客户获取](acquisition-main/t-testing-acquisition.md)
   + [Apple 搜索广告](acquisition-main/c-apple-search-ads.md)
+ 消息传送 {#messaging-ios}
   + [消息传送概述](messaging-main/messaging-main.md)
   + 应用程序内消息传送 {#in-app-messaging}
      + [应用程序内消息传送](messaging-main/messaging/messaging.md)
      + [排查应用程序内消息传送问题](messaging-main/messaging/in-apps-ts.md)
   + 推送消息 {#push-messaging}
      + [推送消息](messaging-main/push-messaging/push-messaging.md)
      + [实施包含深层链接的推送消息](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [接收富推送通知](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [排查推送消息问题](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置 {#location-ios}
   + [位置概述](location/location.md)
   + [地理位置和目标点](location/geo-poi.md)
   + [iBeacon 跟踪](location/ibeacon.md)
+ Target {#target-ios}
   + [Target 概述](target-main/target-main.md)
   + [Target 方法](target-main/c-target-methods.md)
   + [在 iOS 中预取选件内容](target-main/c-mob-target-prefetch-ios.md)
   + [iOS 上的 Target 预览](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud 概述](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service 方法](marketing-cloud/mc-methods.md)
   + [Experience Cloud 设备协作](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager 方法](amm/aam-methods.md)
+ 使用 tvOS 实施 Apple TV {#apple-tv-implementation-tvos-ios}
   + [使用 tvOS 实施 Apple TV](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [适用于 TVML/TVJS 的 Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS 方法](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS 扩展实施 {#ios-ext}
   + [iOS 扩展实施](ios-ext/ios-ext.md)
   + [独立扩展实施](ios-ext/c-stand-alone-extension-implementation.md)
+ [使用 WatchOS 2 实施 Apple Watch](apple-watch-implementation-watchkit.md)
+ iOS SDK 参考 {#sdk-reference-ios}
   + [iOS SDK 参考](reference/reference.md)
   + [应用程序 ID](reference/app-ids.md)
   + [应用程序和移动 Web 之间的访客跟踪](reference/hybrid-app.md)
   + [iOS 设备版本](reference/device-versions.md)
+ 隐私和《通用数据保护条例》{#privacy-gdpr-ios}
   + [隐私和《通用数据保护条例》](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [检索存储的标识符](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [设置用户的选择状态](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap 插件 {#phonegap-ios}
   + [PhoneGap 插件](phonegap/phonegap.md)
   + [PhoneGap 插件方法](phonegap/phonegap-methods.md)
