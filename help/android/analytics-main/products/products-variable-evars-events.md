---
description: 以下是一个具有促销 eVar 和产品特定事件的产品变量示例。
keywords: Android;库;移动;SDK
seo-description: 以下是一个具有促销 eVar 和产品特定事件的产品变量示例。
seo-title: 具有促销 eVar 和产品特定事件的产品变量
solution: Marketing Cloud,Analytics
title: 具有促销 eVar 和产品特定事件的产品变量
topic: 开发人员和实施
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# 具有促销 eVar 和产品特定事件的产品变量 {#products-variable-with-merchandising-evars-and-product-specific-events}

以下是一个具有促销 eVar 和产品特定事件的产品变量示例。

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>如果通过使用 *`&&products`* 变量触发产品特定事件，则还必须在 *`&&events`* 变量中设置该事件。如果未设置该事件，则会在处理期间将其过滤掉。

