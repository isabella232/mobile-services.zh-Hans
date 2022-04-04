---
description: 无法使用处理规则来设置产品变量。在 Mobile SDK 中，必须在上下文数据参数中使用特殊语法来设置服务器调用中的产品。
keywords: Android;库;移动;SDK
solution: Experience Cloud Services,Analytics
title: 产品变量
topic-fix: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
exl-id: 1d850ce1-6fd4-463e-8949-8b8cf40d8467
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 100%

---

# Products 变量 {#products-variable}

无法使用处理规则来设置产品变量。在 Mobile SDK 中，必须在上下文数据参数中使用特殊语法来设置服务器调用中的产品。

要设置“产品”**&#x200B;变量，请将上下文数据键设置为 `"&&products"`，然后使用为“产品”**&#x200B;变量定义的语法来设置值：

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

例如：

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

“产品”**&#x200B;变量在图像请求中设置，而其他变量则设置为上下文数据。必须使用处理规则来映射所有上下文数据变量：

![](assets/map-products.png)

您无需使用处理规则来映射&#x200B;*产品*&#x200B;变量，因为 SDK 会直接在图像请求中设置此变量。
