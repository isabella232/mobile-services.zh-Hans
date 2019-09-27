---
description: 您可以通过回发将 SDK 收集的数据发送至第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 SDK 以将自定义数据发送至第三方目标。
keywords: android；库；移动；sdk
seo-description: 您可以通过回发将 SDK 收集的数据发送至第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 SDK 以将自定义数据发送至第三方目标。
seo-title: 回发
solution: Marketing Cloud,Analytics
title: 回发概述
topic: 开发人员和实施
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# 回发 {#postbacks}

您可以通过回发将 SDK 收集的数据发送至第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 SDK 以将自定义数据发送至第三方目标。

>[!IMPORTANT]
>
>This functionality requires SDK version 4.6.0 or later.

回发消息会排入队列，并遵循控制 Analytics 数据收集的所有现有在线/离线规则。当某个消息匹配时（与显示的消息一样），回发消息不会取消其余的消息。这允许对同一次 Analytics 点击发生多个回发。有关定义，请参阅&#x200B;**[ADBMobile JSON 配置](/help/android/configuration/json-config/json-config.md)。

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. 基于历史记录的数据或基于区段的数据当前不可用。

还有一些特定的保留模板，SDK 会自动将其替换为 SDK 已知的内部数据。

此列表包括：

| 令牌名称 | 令牌描述 |
|--- |--- |
| {%sdkver%} | 返回SDK版本。 |
| {%cachebust%} | 解析为 1 到 100000000 之间的随机数。 |
| {%adid%} | 返回 Android 的广告商 ID。请注意，此令牌仅在使用了 `submitAdvertisingIdentifierTask` 时才可用。 |
| {%pushid%} | 返回推送标识符令牌。请注意，此令牌仅在使用了 `setPushIdentifier` 时才可用。 |
| {%timestampu%} | 以新纪元时间返回当前时间戳。 |
| {%timestampz%} | 以 JavaScript (ISO 8601) 格式返回当前时间戳。 |