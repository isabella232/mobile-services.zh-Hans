---
description: 点击批量处理允许应用程序在队列中的点击量超过可配置限制后才发送点击。
keywords: Android;库;移动;SDK
seo-description: 点击批量处理允许应用程序在队列中的点击量超过可配置限制后才发送点击。
seo-title: 点击批量处理
solution: Experience Cloud,Analytics
title: 点击批量处理
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 100%

---

# 点击批量处理 {#hit-batching}

点击批量处理允许应用程序在队列中的点击量超过可配置限制后才发送点击。

>[!IMPORTANT]
>
>要使用点击批量处理，您&#x200B;**必须**&#x200B;启用离线跟踪，并具有 SDK 版本 4.1 或更高版本

要启用点击批量处理，请更新您的 `ADBMobileConfig.json` 文件，并为 `batchLimit` 指定一个值：

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

如果将该值设置为大于 0 的数值，SDK 会将数量等于 *`batchLimit`* 值的点击量排入队列。达到此阈值后，将发送队列中的所有点击。

采用以下方法进行点击批量处理：

* `Analytics.getQueueSize` 返回 `long`，其中包含点击批量处理队列中的当前点击量。

* `Analytics.sendQueuedHits` 强制库发送队列中的所有点击，而不考虑当前排队的点击量。
* `Analytics.clearQueue` 清除队列中的所有点击，而不发送它们。
