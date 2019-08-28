---
description: 您可以通过回发将 SDK 收集的数据发送至第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 SDK 以将自定义数据发送至第三方目标。
seo-description: 您可以通过回发将 SDK 收集的数据发送至第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 SDK 以将自定义数据发送至第三方目标。
seo-title: 回发
solution: Marketing Cloud，Analytics
title: 回溯概述
uuid: 25e2a5fb-1203-40dd-96cd-b23 e0 f23376 d
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# 回溯概述 {#postbacks}

您可以通过回发将 SDK 收集的数据发送至第三方服务器。利用您用来显示应用程序内消息的相同触发器和特征，可以配置 SDK 以将自定义数据发送至第三方目标。

>[!IMPORTANT]
>
>此功能需要SDK4.6.0或更高版本。

回发消息会排入队列，并遵循控制 Analytics 数据收集的所有现有在线/离线规则。当某个消息匹配时（与显示的消息一样），回发消息不会取消其余的消息。这允许对同一次 Analytics 点击发生多个回发。有关定义，请参阅&#x200B;**[ADBMobile JSON 配置](/help/ios/configuration/json-config/json-config.md)。

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in both the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context-data key, or traditional data key. 可用于模板扩展的值仅限于[标准生命周期变量列表](/help/ios/metrics.md)，以及在触发消息的点击中附加的任何自定义数据。基于历史记录的数据或基于区段的数据当前不可用。

还有一些特定的保留模板，SDK 会自动将其替换为 SDK 已知的内部数据。

此列表包括：

| 令牌名称 | 令牌描述 |
|--- |--- |
| `{%sdkver%}` | 返回 SDK 版本。 |
| `{%cachebust%}` | 解析为 1 到 100000000 之间的随机数。 |
| `{%adid%}` | 返回 IDFA。此令牌仅在您使用 `setAdvertisingIdentifier`时才有效。 |
| `{%pushid%}` | 返回推送标识符令牌。此令牌仅在您使用 `setPushIdentifier`时才有效。 |
| `{%timestampu%}` | 以新纪元时间返回当前时间戳。 |
| `{%timestampz%}` | 以 JavaScript (ISO 8601) 格式返回当前时间戳。 |