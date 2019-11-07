---
description: 您可以使用 Adobe SDK 收集个人识别信息 (PII) 并将其发送至第三方端点。
seo-description: 您可以使用 Adobe SDK 收集个人识别信息 (PII) 并将其发送至第三方端点。
seo-title: PII 回发
title: PII 回发
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: ht
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII 回发 {#pii-postbacks}

您可以使用 Adobe SDK 收集个人识别信息 (PII) 并将其发送至第三方端点。

如果要使用 Adobe SDK 收集 PII，您应当发送一个跟踪 PII 调用。尽管使用此调用能够收集 PII 数据，但 SDK 不会自动将该数据发送到 Adobe 端点。需要对 PII 类型回发配置相应的端点。

>[!TIP]
>
>要使用 PII 回发类型，需要支持 HTTPS 的端点。

## 跟踪 PII 回发 {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。

1. 导入库：

   ```java
   #import "ADBMobile.h"
   ```

1. 准备好捕获 PII 时，调用 `trackPII` 以便为此操作、事件或视图发送点击：

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

