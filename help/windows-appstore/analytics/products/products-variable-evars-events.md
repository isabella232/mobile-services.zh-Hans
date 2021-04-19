---
description: 产品变量与促销eVar和产品特定事件的示例。
seo-description: 产品变量与促销eVar和产品特定事件的示例。
seo-title: 具有促销 eVar 和产品特定事件的产品变量
solution: Experience Cloud,Analytics
title: 具有促销 eVar 和产品特定事件的产品变量
topic-fix: Developer and implementation
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
exl-id: 3a90f624-da13-4c26-9e4c-3a4af33bc5ee
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 27%

---

# 具有促销 eVar 和产品特定事件的产品变量{#products-variable-with-merchandising-evars-and-product-specific-events}

产品变量与促销eVar和产品特定事件的示例。

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>如果使用&#x200B;*`&&products`*&#x200B;变量触发特定于产品的事件，则还必须在&#x200B;*`&&events`*&#x200B;变量中设置该事件，否则在处理过程中会过滤掉事件。
