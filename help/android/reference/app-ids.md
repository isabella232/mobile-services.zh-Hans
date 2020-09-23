---
description: 下表描述了Android SDK和Adobe移动服务使用的不同应用程序标识符。
seo-description: 下表描述了Android SDK和Adobe移动服务使用的不同应用程序标识符。
seo-title: 应用程序 ID
solution: Experience Cloud,Analytics
title: 应用程序 ID
topic: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 72%

---


# 应用程序 ID{#app-ids}

下表描述了Android SDK和Adobe移动服务使用的不同应用程序标识符。

| ID | 描述 |
|--- |--- |
| 使用生命周期指标发送的ID | 这是提交到应用商店的应用程序名称和包版本的组合。此值用于 Adobe Mobile Services 中的版本报表，您可以使用此值过滤，以按应用程序的特定发行版本进行分段。 |
| 应用商店 ID | 此 ID 由应用商店分配给您的应用程序，并在您创建客户获取链接时提供在 Adobe Mobile Services 中。 |
| ADBMobile JSON 配置中的应用程序 ID | 这是由 Adobe Mobile Services 分配给应用程序实例的唯一 ID，用于系统中的所有关联元数据。此 ID 用于创建客户获取跟踪或跟踪链接的唯一 URL。在从用户界面下载 ADBMobile JSON 配置文件时，此 ID 会自动添加到该文件中，可在应用程序客户获取设置下方的“管理应用程序设置”中找到此 ID。 |