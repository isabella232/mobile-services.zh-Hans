---
description: 点击批量处理允许启用了离线跟踪的应用程序在队列中的点击量超过可配置限制后才发送点击。
seo-description: 点击批量处理允许启用了离线跟踪的应用程序在队列中的点击量超过可配置限制后才发送点击。
seo-title: 点击批量处理
solution: Marketing Cloud,Analytics
title: 点击批量处理
topic: 开发人员和实施
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

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

如果将该值设置为大于 0 的数值，SDK 会将数量等于 *`batchLimit`* 值的点击量排入队列。超过此阈值后，将会发送队列中的所有点击。

以下方法可与点击批量处理结合使用：

* `trackingGetQueueSize()` 返回 `NSUInteger`，其中包含点击批量处理队列中的当前点击量。
* `trackingSendQueuedHits()` 强制库发送队列中的所有点击，而不考虑当前排队的点击量。
* `trackingClearQueue()` 清除队列中的所有点击，而不发送它们。

>[!CAUTION]
>
>必须启用离线跟踪才能使用点击批量处理。

