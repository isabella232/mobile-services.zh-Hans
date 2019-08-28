---
description: 处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。
seo-description: 处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。
seo-title: 处理规则和上下文数据
solution: Marketing Cloud，Analytics
title: 处理规则和上下文数据
topic: 开发人员和实施
uuid: 51338CCD-fa52-4d9 c-97c4-947a4100465 d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Processing rules and context data{#processing-rules-and-context-data}

处理规则用于将您在上下文数据变量中发送的数据复制到 eVar、prop 及其他变量以供报告。

有关更多信息，请参阅以下内容：

* 2013 年峰会上的[处理规则培训](https://tv.adobe.com/embed/1181/16506/)
* 获得使用处理规则的授权

   有关处理规则的更多信息，请参阅 [处理规则概述](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)。

在使用处理规则时，请牢记以下信息：

* 使用命名空间对上下文数据变量进行分组，因为这可以帮助您保持逻辑排序。

   例如，如果您要收集有关某个产品的信息，则可以定义以下变量：

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

   在处理规则中执行一次性映射时，这或许会&#x200B;*稍微*&#x200B;提供一些便利，但在调试以及日后的代码更新期间，您将会失去可读性，从而加大理解难度。因此，请改用描述性名称来命名键和值：

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
>Adobe保留命名空间“ `a.`”。除了该限制之外，为了避免发生冲突，还只需满足一个要求，即上下文数据变量在您的登录公司中是唯一的。

