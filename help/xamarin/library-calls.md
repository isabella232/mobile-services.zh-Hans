---
description: 有关帮助您从脚本中调用插件的信息。
keywords: Xamarin
seo-description: 有关帮助您从脚本中调用插件的信息。
seo-title: 调用库
solution: Marketing Cloud，开发人员
title: 调用库
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

此信息可帮助您从脚本调用插件。

如果需要从脚本中调用插件，则必须导入命名空间。

`Com.Adobe.Mobile`通过：

* **iOS**：导入命名空间后，可以通过 `ADBMobile` 类中的静态方法直接调用SDK。

* **Android**：您可以通过 `Config/Analytics/Target/AudienceManager/Media`类中的静态方法直接调用SDK。

