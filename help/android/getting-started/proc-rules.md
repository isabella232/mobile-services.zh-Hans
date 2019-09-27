---
description: 处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。
seo-description: 处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。
seo-title: 处理规则和上下文数据
solution: Marketing Cloud,Analytics
title: 处理规则和上下文数据
topic: 开发人员和实施
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Processing rules and context data {#processing-rules-and-context-data}

处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

在使用处理规则时，请牢记以下信息：

* 使用命名空间对上下文数据变量进行分组，因为这可以帮助您保持逻辑排序。例如，要收集有关某个产品的信息，您可以定义以下变量：

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* 上下文数据变量在处理规则界面中按字母顺序进行排序，从而使您能够快速查看哪些变量位于同一命名空间。

   避免使用 evar 或 prop 编号命名上下文数据键：

   ```js
   "eVar1":"jimbo"
   ```

   在处理规则中完成一次性映射时，这或许会&#x200B;*稍微*&#x200B;提供一些便利，但在调试以及日后的代码更新期间，您将会失去可读性，从而加大理解难度。我们强烈建议为键和值使用描述性名称：

   ```js
   "username":"jimbo"
   ```

* 定义计数器事件的上下文变量应当设置为 1：

   ```js
   "logon":"1"
   ```

* 定义增量器事件的上下文数据变量可以使用事件作为键，使用递增量作为值：

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe保留命名空间 `"a."`。 为了避免发生冲突，还仅要求上下文数据变量在您的登录公司中是唯一的。

