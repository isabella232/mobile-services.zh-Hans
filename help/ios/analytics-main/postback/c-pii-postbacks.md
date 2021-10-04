---
description: 您可以使用 Adobe SDK 收集个人身份信息 (PII) 并将其发送至第三方端点。
title: PII 回发
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 86%

---

# PII 回发 {#pii-postbacks}

您可以使用 Adobe SDK 收集个人身份信息 (PII) 并将其发送至第三方端点。

如果要使用 Adobe SDK 收集 PII，应发送一个 PII 跟踪调用。尽管使用此调用可收集PII数据，但SDK不会自动将数据发送到任何Adobe端点。 需要对 PII 类型回发配置相应的端点。

>[!TIP]
>
>要使用 PII 回发类型，需要支持 HTTPS 的端点。

## 跟踪 PII 回发 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的项目”**。
1. 导入库：

   ```objective-c
   #import "ADBMobile.h"
   ```

1. 准备好捕获 PII 时，调用 `trackPII` 以便为此操作、事件或视图发送点击：

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```
