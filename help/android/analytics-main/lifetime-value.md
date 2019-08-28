---
description: 生命周期值允许您测量和定位每个 Android 用户的生命周期值。该值可用于存储生命周期购买、广告查看、视频完成、社交分享、照片上载等。
seo-description: 生命周期值允许您测量和定位每个 Android 用户的生命周期值。该值可用于存储生命周期购买、广告查看、视频完成、社交分享、照片上载等。
seo-title: 访客生命周期值
solution: Marketing Cloud，Analytics
title: 访客生命周期值
topic: 开发人员和实施
uuid: ba0308de-282e-46f9-a14 c-19fb6 d5 c363 e
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Visitor lifetime value {#visitor-lifetime-value}

生命周期值允许您测量和定位每个 Android 用户的生命周期值。该值可用于存储生命周期购买、广告查看、视频完成、社交分享、照片上载等。

每当您通过 `trackLifetimeValueIncrease` 发送值时，该值都会添加到现有值。生命周期值存储在设备上，并可随时通过调用 `lifetimeValue` 进行检索。

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 将[库到您的项目并实施生命周期。

   有关详细信息，请参阅 *在核心实施和生命周期* 中 [将SDK和Config文件添加到IntelliJ IDEA或Eclipse项目](/help/android/getting-started/dev-qs.md)。
1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 通过值的增加量调用 `trackLifetimeValueIncrease`：

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了生命周期值之外，您还可以通过每个跟踪操作调用发送其他上下文数据：

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

上下文数据值必须映射到 Adobe Mobile Services 中的自定义变量：

![](assets/map-variable-context-ltv.png)

