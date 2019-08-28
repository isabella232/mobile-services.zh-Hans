---
description: 点击批量处理允许启用了离线跟踪的应用程序在队列中的点击量超过可配置限制后才发送点击。
seo-description: 点击批量处理允许启用了离线跟踪的应用程序在队列中的点击量超过可配置限制后才发送点击。
seo-title: 对点击量进行批处理
solution: Marketing Cloud，Analytics
title: 对点击量进行批处理
topic: 开发人员和实施
uuid: 3dda7322-0695-4cb7-b 7799-abca2 d6 e0 d9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 对点击量进行批处理 {#hit-batching}

点击批量处理允许启用了离线跟踪的应用程序在队列中的点击量超过可配置限制后才发送点击。

>[!IMPORTANT]
>
>点击批处理需要SDK版本4.1或更高版本。

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

当设置为高于 0 的数值时，SDK 会将数量等于 *`batchLimit`*. 超过此阈值后，将会发送队列中的所有点击。

以下方法可与点击批量处理结合使用：

* `trackingGetQueueSize()` 返回 `NSUInteger` 点击批处理队列中当前点击次数。
* `trackingSendQueuedHits()` 强制库发送队列中的所有点击，无论当前排队的点击数如何。
* `trackingClearQueue()` 清除队列中的所有点击，而不发送它们。

>[!CAUTION]
>
>必须启用离线跟踪才能使用点击批处理。

