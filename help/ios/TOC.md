---
product: 移动服务
audience: 最终用户
user-guide-title: Mobile Services iOS帮助
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOS帮助 {#ios}

+ [适用于 Experience Cloud 解决方案的 iOS SDK 4.x](overview.md)
+ [发行说明](rel-notes.md)
+ 入门指南 {#getting-started-ios}
   + [入门概述](getting-started/getting-started.md)
   + [开始之前](getting-started/requirements.md)
   + [核心实施和生命周期](getting-started/dev-qs.md)
   + [处理规则和上下文数据](getting-started/proc-rules.md)
   + [Swift集成](getting-started/swift-integration.md)
   + [迁移到4.x iOS库](getting-started/migration-v3.md)
+ 配置 {#config-ios}
   + [配置概述](configuration/configuration.md)
   + [AdBMobile JSON配置](configuration/json-config/json-config.md)
   + [重写AdBMobile JSON配置路径](configuration/json-config/json-config-remote.md)
   + [对点击量进行批处理](configuration/hit-batching.md)
   + [配置方法](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [生命周期指标](metrics.md)
+ Analytics {#analytics-ios}
   + [分析概述](analytics-main/analytics-main.md)
   + [跟踪应用程序状态](analytics-main/states.md)
   + [跟踪应用程序操作](analytics-main/actions.md)
   + [跟踪应用程序的崩溃情况](analytics-main/crashes.md)
   + [定时操作](analytics-main/timed-actions.md)
   + [访客终身价值](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [产品变量](analytics-main/products/products.md)
      + [产品变量与产品eVar和产品特定事件](analytics-main/products/products-variable-evars-events.md)
   + [事件序列化](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + 回发 {#postbacks}
      + [回溯概述](analytics-main/postback/postback.md)
      + [返回示例](analytics-main/postback/postback-example.md)
      + [PII回回](analytics-main/postback/c-pii-postbacks.md)
   + [分析方法](analytics-main/analytics-methods.md)
+ 客户获取 {#acquisition-ios}
   + [客户赢取概述](acquisition-main/acquisition-main.md)
   + [移动应用程序获取](acquisition-main/acquisition.md)
   + [客户赢取方法](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [跟踪深层链接](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [跟踪第三方延迟深层链接](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Testing Marketing Link获取](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [测试V赢取](acquisition-main/t-testing-version-3-acquisition.md)
   + [测试传统客户赢取率](acquisition-main/t-testing-acquisition.md)
   + [Apple 搜索广告](acquisition-main/c-apple-search-ads.md)
+ 消息传送 {#messaging-ios}
   + [消息传递概述](messaging-main/messaging-main.md)
   + 应用程序内消息传送 {#in-app-messaging}
      + [应用程序内消息传送](messaging-main/messaging/messaging.md)
      + [应用程序内消息传递疑难解答](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [推送消息](messaging-main/push-messaging/push-messaging.md)
      + [利用深层链接实施推送消息](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [接收丰富的推送通知](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [推送消息疑难解答](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ 位置 {#location-ios}
   + [位置概述](location/location.md)
   + [地理位置和兴趣点](location/geo-poi.md)
   + [iBeacon 跟踪](location/ibeacon.md)
+ Target {#target-ios}
   + [Target概述](target-main/target-main.md)
   + [Target方法](target-main/c-target-methods.md)
   + [在 iOS 中预取选件内容](target-main/c-mob-target-prefetch-ios.md)
   + [iOS 上的 Target 预览](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud概述](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service方法](marketing-cloud/mc-methods.md)
   + [Experience Cloud 设备协作](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager方法](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [带TvOS的Apple TV实现](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [适用于 TVML/TVJS 的 Adobe Target](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS 方法](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS扩展实施](ios-ext/ios-ext.md)
   + [独立的扩展实施](ios-ext/c-stand-alone-extension-implementation.md)
+ [带WatchOS的Apple Watch实施](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDK参考](reference/reference.md)
   + [应用程序 ID](reference/app-ids.md)
   + [应用程序与移动Web之间的访客跟踪](reference/hybrid-app.md)
   + [iOS设备版本](reference/device-versions.md)
+ 隐私和通用数据保护条例{#privacy-gdpr-ios}
   + [隐私和通用数据保护条例](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [检索存储的标识符](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [设置用户的选择状态](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap 插件 {#phonegap-ios}
   + [PhoneGap插件](phonegap/phonegap.md)
   + [PhoneGap插件方法](phonegap/phonegap-methods.md)
