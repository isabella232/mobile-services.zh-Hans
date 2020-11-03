---
description: 您可以使用生命周期值测量和定位每个用户的生命周期值。
seo-description: 您可以使用生命周期值测量和定位每个用户的生命周期值。
seo-title: 访客生命周期值
solution: Experience Cloud,Analytics
title: 访客生命周期值
topic: Developer and implementation
uuid: d830d18b-4313-43bb-8d75-3789869d0f1d
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '173'
ht-degree: 100%

---


# 访客生命周期值 {#visitor-lifetime-value}

您可以使用生命周期值测量和定位每个用户的生命周期值。

每当您通过 `trackLifetimeValueIncrease` 发送值时，该值都会添加到现有值。生命周期值存储在设备上，并可随时通过调用 `lifetimeValue` 进行检索。此值可用于存储生命周期购买、广告查看、视频完成、社交分享、照片上载等。

## 跟踪访客生命周期值 {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. 将库添加到您的项目并实施生命周期。

   有关更多信息，请参阅[核心实施和生命周期](/help/ios/getting-started/dev-qs.md)中的“将 SDK 和配置文件添加到您的项目”**。
1. 导入库：

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. 通过值的增加量调用 `trackLifetimeValueIncrease`：

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## 发送其他数据 {#section_3EBE813E54A24F6FB669B2478B5661F9}

除了生命周期值之外，您还可以通过每个跟踪操作调用发送其他上下文数据：

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

上下文数据值必须映射到以下自定义变量：

![](assets/map-variable-context-ltv.png)

