---
description: 具有促销eVar和产品特定事件的产品变量的示例。
solution: Experience Cloud,Analytics
title: 具有促销 eVar 和产品特定事件的产品变量
topic-fix: Developer and implementation
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
exl-id: 3a90f624-da13-4c26-9e4c-3a4af33bc5ee
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 24%

---

# 具有促销 eVar 和产品特定事件的 Products 变量{#products-variable-with-merchandising-evars-and-product-specific-events}

具有促销eVar和产品特定事件的产品变量的示例。

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
>如果使用&#x200B;*`&&products`*&#x200B;变量触发产品特定事件，则还必须在&#x200B;*`&&events`*&#x200B;变量中设置该事件，否则该事件会在处理过程中被过滤掉。
