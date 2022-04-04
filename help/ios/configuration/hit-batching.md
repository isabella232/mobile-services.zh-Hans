---
description: 点击批量处理允许启用了离线跟踪的应用程序在队列中的点击量超过可配置限制后才发送点击。
solution: Experience Cloud Services,Analytics
title: 点击批量处理
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---

# 点击批量处理 {#hit-batching}

点击批量处理允许启用了离线跟踪的应用程序在队列中的点击量超过可配置限制后才发送点击。

>[!IMPORTANT]
>
>点击批量处理需要 SDK 版本 4.1 或更高版本。

要启用点击批量处理，请更新您的 `ADBMobileConfig.json` 文件，并为 `batchLimit` 指定一个值：

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

如果将该值设置为大于 0 的数值，SDK 会将数量等于 *`batchLimit`* 值的点击量排入队列。达到此阈值后，将发送队列中的所有点击。

采用以下方法进行点击批量处理：

* `trackingGetQueueSize()` 返回 `NSUInteger`，其中包含点击批量处理队列中的当前点击量。
* `trackingSendQueuedHits()` 强制库发送队列中的所有点击，而不考虑当前排队的点击量。
* `trackingClearQueue()` 清除队列中的所有点击，而不发送它们。

>[!CAUTION]
>
>必须启用离线跟踪才能使用点击批量处理。
