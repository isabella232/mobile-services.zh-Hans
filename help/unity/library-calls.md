---
description: 从脚本中调用库插件。
keywords: Unity
solution: Experience Cloud Services
title: 调用库
uuid: 74c30379-6cdf-4318-9db8-e14fb63aa18a
exl-id: de95edd5-3a5b-4b84-aeea-adff3362f544
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 18%

---

# 调用库{#making-calls-to-the-library}

当您要从脚本中调用插件时，请导入命名空间：

* **C#:** 使用 `com.adobe.mobile;`

导入命名空间后，您可以通过ADBMobile类的静态方法直接调用插件。
