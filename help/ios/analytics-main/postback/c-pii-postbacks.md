---
description: 您可以使用 Adobe SDK 收集个人识别信息 (PII) 并将其发送至第三方端点。
seo-description: 您可以使用 Adobe SDK 收集个人识别信息 (PII) 并将其发送至第三方端点。
seo-title: PII 回发
title: PII 回发
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

您可以使用 Adobe SDK 收集个人识别信息 (PII) 并将其发送至第三方端点。

如果要使用 Adobe SDK 收集 PII，您应当发送一个跟踪 PII 调用。尽管使用此调用能够收集 PII 数据，但 SDK 不会自动将该数据发送到任何 Adobe 端点。需要对 PII 类型回发配置相应的端点。

>[!TIP]
>
>使用PII回传类型需要支持HTTPS的端点。

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 将库添加到您的项目并实施生命周期。

   有关详细信息，请参 *阅在核心实施和生命周期中将SDK和配置文件添加*[到您的项目中](/help/ios/getting-started/dev-qs.md)。
1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 准备好捕获 PII 时，调用 `trackPII` 以便为此操作、事件或视图发送点击：

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

