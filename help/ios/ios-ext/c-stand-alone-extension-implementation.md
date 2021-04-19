---
description: 从 iOS 10 开始，Apple 允许您创建称为独立扩展的扩展，此类扩展无需容器应用程序即可分发。使用此扩展，您无需应用程序组，因为没有要与之共享数据的容器应用程序。
seo-description: 从 iOS 10 开始，Apple 允许您创建称为独立扩展的扩展，此类扩展无需容器应用程序即可分发。使用此扩展，您无需应用程序组，因为没有要与之共享数据的容器应用程序。
seo-title: 独立扩展实施
solution: Experience Cloud,Analytics
title: 独立扩展实施
topic-fix: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
exl-id: b51247b6-c4ba-4a00-9ba0-1824450ac067
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 100%

---

# 独立扩展实施 {#stand-alone-extension-implementation}

从 iOS 10 开始，Apple 允许您创建称为独立扩展的扩展，此类扩展无需容器应用程序即可分发。使用此扩展，您无需应用程序组，因为没有要与之共享数据的容器应用程序。

>[!IMPORTANT]
>
>要使用独立扩展，您必须具有 Mobile SDK 版本 4.13.0 或更高版本。

## 配置独立扩展以便与 SDK 结合使用 {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

要配置您的独立扩展，请执行以下操作：

1. 确保 `ADBMobileConfig.json` 文件是扩展目标的成员。
1. 关联以下库和框架：

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. 在您的扩展的主视图控制器中，先在 SDK 中将扩展类型设置为 `ADBMobileAppExtensionTypeStandAlone`，然后再完成任何与 SDK 相关的活动。

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. 确认您的应用程序在生成时没有出现意外错误。

## 其他说明 {#section_1C9A55E2309A44BF842310F735702B3D}

以下是一些附加信息：

* 添加了一个额外的上下文数据值 `a.RunMode`，以指示数据是来自容器应用程序还是扩展：

   * `a.RunMode = Application`

      此值表示点击来自容器应用程序。
   * `a.RunMode = Extension`

      此值表示点击来自扩展。

* 在 iOS 扩展应用程序中不会触发生命周期调用。
