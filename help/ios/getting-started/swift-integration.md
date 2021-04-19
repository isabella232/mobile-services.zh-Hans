---
description: 通过使用 iOS 开发人员库中的“混合和匹配”功能，可以将 iOS Adobe Mobile SDK 无缝集成到 Swift 项目中。
seo-description: 通过使用 iOS 开发人员库中的“混合和匹配”功能，可以将 iOS Adobe Mobile SDK 无缝集成到 Swift 项目中。
seo-title: Swift 集成
solution: Experience Cloud,Analytics
title: Swift 集成
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 100%

---

# Swift 集成 {#swift-integration}

通过使用 iOS 开发人员库中的“混合和匹配”功能，可以将 iOS Adobe Mobile SDK 无缝集成到 Swift 项目中。

有关更多信息，请参阅[语言互操作性](https://developer.apple.com/documentation/swift#2984801.html)。

例如，使用文档中所述的桥接头方法，可以导入 Adobe Mobile iOS SDK 头文件：

```
#import “ADBMobile.h”
```

要从 Swift 文件中的 SDK 访问方法，请使用以下格式：

```
ADBMobile.{methodname}
```
