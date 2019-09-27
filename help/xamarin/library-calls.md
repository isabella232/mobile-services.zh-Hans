---
description: 有关帮助您从脚本中调用插件的信息。
keywords: Xamarin
seo-description: 有关帮助您从脚本中调用插件的信息。
seo-title: 拨叫图书馆
solution: Marketing Cloud，开发人员
title: 拨叫图书馆
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

This information to help you make calls to the plugin from your scripts.

如果需要从脚本中调用插件，则必须导入命名空间。

通过使用 `Com.Adobe.Mobile`:

* **iOS**:导入命名空间后，您可以通过类中的静态方法直接对SDK进行调 `ADBMobile` 用。

* **Android**:您可以通过类中的静态方法直接调用SDK `Config/Analytics/Target/AudienceManager/Media`。

