---
description: 回传允许您将SDK收集的数据发送到第三方服务器。 通过利用用于显示应用程序内消息的相同触发器和特征，您可以配置SDK以将自定义数据发送到第三方目标。
keywords: android;library;mobile;sdk
seo-description: 回传允许您将SDK收集的数据发送到第三方服务器。 通过利用用于显示应用程序内消息的相同触发器和特征，您可以配置SDK以将自定义数据发送到第三方目标。
seo-title: 回发
solution: Experience Cloud,Analytics
title: 回发概述
topic: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 35%

---


# 回发 {#postbacks}

回传允许您将SDK收集的数据发送到第三方服务器。 通过利用用于显示应用程序内消息的相同触发器和特征，您可以配置SDK以将自定义数据发送到第三方目标。

>[!IMPORTANT]
>
>此功能需要 SDK 版本 4.6.0 或更高版本。

回传消息将排队，并遵循控制分析数据收集的所有现有在线／离线规则。 当消息匹配时（如显示消息），回传消息不会取消其余消息。 这允许在同一分析点击中发生多个回传。 有关定义，请参阅 *ADBMobile* JSON配 [置中的回发行](/help/android/configuration/json-config/json-config.md)。

## 模板扩展 {#section_6758AD05A24C4E9E965F5253294C164A}

模板扩展可在 `templateurl` 和 `templatebody` 属性中使用。模板项目采用 `{key}` 形式，其中 `key` 是上下文数据键或传统数据键。可用于模板扩展的值仅限于[生命周期量度](/help/android/metrics.md)，以及在触发消息的点击中附加的任何自定义数据。目前没有基于历史或细分的数据可用。

还有特定的保留模板，SDK将自动替换为SDK已知的内部数据。

此列表包括：

| 令牌名称 | 令牌描述 |
|--- |--- |
| {%sdkver%} | 返回 SDK 版本。 |
| {%cachebust%} | 解析为 1 到 100000000 之间的随机数。 |
| {%adid%} | 返回 Android 的广告商 ID。请注意，此令牌仅在使用了 `submitAdvertisingIdentifierTask` 时才可用。 |
| {%pushid%} | 返回推送标识符令牌。请注意，此令牌仅在使用了 `setPushIdentifier` 时才可用。 |
| {%timestampu%} | 以新纪元时间返回当前时间戳。 |
| {%timestampz%} | 以 JavaScript (ISO 8601) 格式返回当前时间戳。 |