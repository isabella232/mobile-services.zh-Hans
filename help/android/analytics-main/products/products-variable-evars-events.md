---
description: 以下是一个具有促销 eVar 和产品特定事件的产品变量示例。
keywords: android;library;mobile;sdk
seo-description: 以下是一个具有促销 eVar 和产品特定事件的产品变量示例。
seo-title: 具有促销 eVar 和产品特定事件的产品变量
solution: Experience Cloud,Analytics
title: 具有促销 eVar 和产品特定事件的产品变量
topic: Developer and implementation
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '98'
ht-degree: 100%

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

