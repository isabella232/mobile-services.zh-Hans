---
description: 下表描述了 iOS SDK 与 Adobe Mobile Services 使用的不同应用程序标识符。
solution: Experience Cloud,Analytics
title: 应用程序 ID
topic-fix: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
exl-id: 82f0a097-b2eb-4313-8624-dd442e3da039
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 100%

---

# 应用程序 ID {#app-ids}

下表描述了 iOS SDK 与 Adobe Mobile Services 使用的不同应用程序标识符。

| ID | 描述 |
|--- |--- |
| 使用生命周期量度发送的 ID | 这是提交到应用商店的应用程序名称和包版本的组合。此值用于 Adobe Mobile Services 中的版本报表，您可以使用此值按应用程序的特定发行版本过滤结果。 |
| 应用商店 ID | 此 ID 由应用商店分配给您的应用程序，并在您创建客户获取链接时提供在 Adobe Mobile Services 中。 |
| ADBMobile JSON 配置中的应用程序 ID | 这是由 Adobe Mobile Services 分配给应用程序实例的唯一 ID，用于系统中的所有关联元数据。此 ID 用于创建客户获取跟踪或跟踪链接的唯一 URL；在从用户界面下载 ADBMobile JSON 配置文件时，此 ID 会自动添加到该文件中，可在应用程序的客户获取设置下方的“管理应用程序设置”中找到此 ID。 |
