---
description: 帮助您从脚本调用插件的信息。
keywords: Xamarin
seo-description: 帮助您从脚本调用插件的信息。
seo-title: 拨打图书馆
solution: Experience Cloud
title: 拨打图书馆
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# 拨打图书馆{#making-calls-to-the-library}

此信息可帮助您从脚本中调用插件。

如果要从脚本调用插件，则必须导入命名空间。

通过使用 `Com.Adobe.Mobile`:

* **iOS**:导入命名空间后，可通过类中的静态方法直接调用SDK `ADBMobile` 。

* **Android**:您可以通过类中的静态方法直接向SDK发 `Config/Analytics/Target/AudienceManager/Media`出调用。

