---
description: 您可以使用生命周期值测量和定位每个 Android 用户的生命周期值。此值可用于存储生命周期内的购买次数、广告查看次数、视频完成次数、社交分享次数、照片上载次数等。
seo-description: 您可以使用生命周期值测量和定位每个 Android 用户的生命周期值。此值可用于存储生命周期内的购买次数、广告查看次数、视频完成次数、社交分享次数、照片上载次数等。
seo-title: 访客生命周期值
solution: Marketing Cloud,Analytics
title: 访客生命周期值
topic: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---


# 访客生命周期值 {#visitor-lifetime-value}

您可以使用生命周期值测量和定位每个 Android 用户的生命周期值。此值可用于存储生命周期内的购买次数、广告查看次数、视频完成次数、社交分享次数、照片上载次数等。

每当您通过 `trackLifetimeValueIncrease` 发送值时，该值都会添加到现有值。生命周期值存储在设备上，并可随时通过调用 `lifetimeValue` 进行检索。

## 跟踪访客生命周期值 {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/android/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目”**。
1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 通过值的增加量调用 `trackLifetimeValueIncrease`：

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## 发送其他数据 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了生命周期值之外，您还可以通过每个跟踪操作调用发送其他上下文数据：

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

上下文数据值必须映射到 Adobe Mobile Services 中的自定义变量：

![](assets/map-variable-context-ltv.png)

