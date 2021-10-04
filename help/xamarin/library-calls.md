---
description: 此信息可帮助您从脚本中调用插件。
keywords: 沙马林
solution: Experience Cloud
title: 调用库
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# 调用库{#making-calls-to-the-library}

此信息可帮助您从脚本中调用插件。

如果要从脚本中调用插件，则必须导入命名空间。

使用`Com.Adobe.Mobile`:

* **iOS**:导入命名空间后，您可以通过类中的静态方法直接调用SDK `ADBMobile` 。

* **Android**:您可以通过类中的静态方法直接调用 `Config/Analytics/Target/AudienceManager/Media`SDK。
