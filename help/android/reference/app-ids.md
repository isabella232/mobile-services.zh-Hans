---
description: 下表介绍了可供 Android SDK 和 Adobe Mobile Services 使用的不同应用程序标识符。
seo-description: 下表介绍了可供 Android SDK 和 Adobe Mobile Services 使用的不同应用程序标识符。
seo-title: 应用程序 ID
solution: Marketing Cloud，Analytics
title: 应用程序 ID
topic: 开发人员和实施
uuid: ac99489-6269-439e-a814-24102ef220 b1
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# 应用程序 ID{#app-ids}

下表介绍了可供 Android SDK 和 Adobe Mobile Services 使用的不同应用程序标识符。

| ID | 描述 |
|--- |--- |
| 随生命周期量度发送的 ID | 这是提交到应用商店的应用程序名称和包版本的组合。此值用于 Adobe Mobile Services 中的版本报表，您可以使用此值过滤，以按应用程序的特定发行版本进行分段。 |
| 应用商店 ID | 此ID由App Store分配给您的应用程序，并在您创建客户赢取链接时在Adobe Mobile服务中提供。 |
| ADBMobile JSON 配置中的应用程序 ID | 这是由 Adobe Mobile Services 分配给应用程序实例的唯一 ID，用于系统中的所有关联元数据。此 ID 用于创建客户获取跟踪或跟踪链接的唯一 URL。在从用户界面下载 ADBMobile JSON 配置文件时，此 ID 会自动添加到该文件中，可在应用程序客户获取设置下方的“管理应用程序设置”中找到此 ID。 |