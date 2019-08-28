---
description: 点击批量处理允许应用程序在队列中的点击量超过可配置限制后才发送点击。
keywords: android；库；移动；sdk
seo-description: 点击批量处理允许应用程序在队列中的点击量超过可配置限制后才发送点击。
seo-title: 点击批量处理
solution: Marketing Cloud，Analytics
title: 点击批量处理
topic: 开发人员和实施
uuid: ada35be3-242b-4b2b-a828-9bf998 dd58 b5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# 对点击量进行批处理 {#hit-batching}

点击批量处理允许应用程序在队列中的点击量超过可配置限制后才发送点击。

>[!IMPORTANT]
>
>要使用点击批处理，必须 **** 启用脱机跟踪，并具有SDK4.1或更高版本

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. 超过此阈值后，将会发送队列中的所有点击。

以下方法可与点击批量处理结合使用：

* `Analytics.getQueueSize` 返回 `long`，其中包含点击批量处理队列中的当前点击量。

* `Analytics.sendQueuedHits` 强制库发送队列中的所有点击，而不考虑当前排队的点击量。
* `Analytics.clearQueue` 清除队列中的所有点击，而不发送它们。
