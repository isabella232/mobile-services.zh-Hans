---
description: 处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。
seo-description: 处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。
seo-title: 处理规则和上下文数据
solution: Experience Cloud,Analytics
title: 处理规则和上下文数据
topic: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%

---


# 处理规则和上下文数据 {#processing-rules-and-context-data}

处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。有关更多信息，请参阅[处理规则](https://docs.adobe.com/content/help/zh-Hans/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

在使用处理规则时，请牢记以下信息：

* 使用命名空间对上下文数据变量进行分组，因为这有助于保持逻辑顺序。例如，要收集关于产品的信息，您可以定义以下变量：

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 上下文数据变量在处理规则界面中按字母顺序排序，这使您能够快速查看哪些变量处于同一命名空间。

   避免使用 evar 或 prop 编号来命名上下文数据键：

   ```js
   "eVar1":"jimbo"
   ```

   虽然在完成规则中执行一次性映射时，这可能会&#x200B;*略微*&#x200B;简化操作过程，但在调试和未来更新代码时会失去可读性，可能会使操作愈发困难。我们强烈建议您改用描述性名称来表示键和值：

   ```js
   "username":"jimbo"
   ```

* 定义计数器事件的上下文变量应设置为 1：

   ```js
   "logon":"1"
   ```

* 定义增量事件的上下文数据变量可以使用事件为键，使用增量为值：

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe 会保留命名空间 `"a."`。为了避免发生冲突，还仅要求上下文数据变量在您的登录公司中是唯一的。

