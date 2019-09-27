---
product: mobile-services
audience: 最终用户
user-guide-title: Mobile Services iOS帮助
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOS Help {#ios}

+ [适用于 Experience Cloud 解决方案的 iOS SDK 4.x](overview.md)
+ [发行说明](rel-notes.md)
+ 入门指南 {#getting-started-ios}
   + [Getting started overview](getting-started/getting-started.md)
   + [开始之前](getting-started/requirements.md)
   + [核心实施和生命周期](getting-started/dev-qs.md)
   + [处理规则和上下文数据](getting-started/proc-rules.md)
   + [Swift集成](getting-started/swift-integration.md)
   + [迁移到4.x iOS库](getting-started/migration-v3.md)
+ 配置 {#config-ios}
   + [Configuration overview](configuration/configuration.md)
   + [ADBMobile JSON config](configuration/json-config/json-config.md)
   + [覆盖ADBMobile JSON配置路径](configuration/json-config/json-config-remote.md)
   + [对点击量进行批处理](configuration/hit-batching.md)
   + [配置方法](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [生命周期指标](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [跟踪应用程序状态](analytics-main/states.md)
   + [跟踪应用程序操作](analytics-main/actions.md)
   + [跟踪应用程序的崩溃情况](analytics-main/crashes.md)
   + [定时操作](analytics-main/timed-actions.md)
   + [访客终身价值](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [产品变量](analytics-main/products/products.md)
      + [具有销售eVar和产品特定事件的产品变量](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回发 {#postbacks}
      + [回发概述](analytics-main/postback/postback.md)
      + [回发示例](analytics-main/postback/postback-example.md)
      + [PII postbacks](analytics-main/postback/c-pii-postbacks.md)
   + [分析方法](analytics-main/analytics-methods.md)
+ 客户获取 {#acquisition-ios}
   + [Acquisition overview](acquisition-main/acquisition-main.md)
   + [Mobile app acquisition](acquisition-main/acquisition.md)
   + [Acquisition methods](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [跟踪深层链接](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Tracking third-party deferred deep links](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [测试Marketing Link赢取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [测试V3客户获取](acquisition-main/t-testing-version-3-acquisition.md)
   + [测试旧版客户获取](acquisition-main/t-testing-acquisition.md)
   + [Apple 搜索广告](acquisition-main/c-apple-search-ads.md)
+ 消息传送 {#messaging-ios}
   + [Messaging overview](messaging-main/messaging-main.md)
   + 应用程序内消息传送 {#in-app-messaging}
      + [应用程序内消息传送](messaging-main/messaging/messaging.md)
      + [应用程序内消息处理疑难解答](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [Push messaging](messaging-main/push-messaging/push-messaging.md)
      + [实现具有深层链接的推送消息](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Receive rich push notifications](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [推送消息疑难解答](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置 {#location-ios}
   + [位置概述](location/location.md)
   + [地理位置和目标点](location/geo-poi.md)
   + [iBeacon 跟踪](location/ibeacon.md)
+ Target {#target-ios}
   + [Target概述](target-main/target-main.md)
   + [目标方法](target-main/c-target-methods.md)
   + [在 iOS 中预取选件内容](target-main/c-mob-target-prefetch-ios.md)
   + [iOS 上的 Target 预览](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience cloud概述](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity service方法](marketing-cloud/mc-methods.md)
   + [Experience Cloud 设备协作](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager methods](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [带tvOS的Apple TV实现](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [适用于 TVML/TVJS 的 Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS 方法](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS扩展实现](ios-ext/ios-ext.md)
   + [独立扩展实施](ios-ext/c-stand-alone-extension-implementation.md)
+ [Apple Watch implementation with WatchOS 2](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDK参考](reference/reference.md)
   + [应用程序 ID](reference/app-ids.md)
   + [在应用程序和移动Web之间跟踪访客](reference/hybrid-app.md)
   + [iOS设备版本](reference/device-versions.md)
+ 隐私和通用数据保护条例{#privacy-gdpr-ios}
   + [隐私和通用数据保护条例](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [检索存储的标识符](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [设置用户的选择状态](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap 插件 {#phonegap-ios}
   + [PhoneGap插件](phonegap/phonegap.md)
   + [PhoneGap插件方法](phonegap/phonegap-methods.md)
