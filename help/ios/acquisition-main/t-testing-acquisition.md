---
description: 以下信息可帮助您对基于设备指纹的旧版客户获取促销活动链接进行往返测试。
seo-description: 以下信息可帮助您对基于设备指纹的旧版客户获取促销活动链接进行往返测试。
seo-title: 测试旧版客户获取
solution: Marketing Cloud，Analytics
title: 测试旧版客户获取
uuid: e0591f4a-e26 b-4fe4-97c1-a6831 a926 fa5
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Testing legacy acquisition {#testing-legacy-acquisition}

以下信息可帮助您对基于设备指纹的旧版客户获取促销活动链接进行往返测试。

如果 Google Play 中尚未提供相应的移动设备应用程序，则在创建促销活动链接时，可以选择任何移动设备应用程序作为目标。这只会影响在您单击客户获取链接后客户获取服务器将您重定向到的应用程序，而不会影响测试客户获取链接的功能。

1. Navigate to **[!UICONTROL Use Legacy Acquisition Links]** in Adobe Mobile Services and generate an acquisition campaign URL.

   有关更多信息，请参阅[使用旧版客户获取链接](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)。

1. 在将要安装应用程序的移动设备上，单击生成的链接。

   Adobe 服务器 (`c00.adobe.com`) 将存储指纹并重定向到应用商店。无需下载应用程序进行测试。

1. 在步骤 2 中使用的相同移动设备上，首次启动应用程序。

   确保此操作成功的最简单方法是删除并重新安装应用程序。

请牢记以下信息：

* 客户获取服务器提供基于 IP 地址和用户代理信息的归因匹配，这些信息会在链接点击中（步骤 2）以及应用程序启动时（步骤 3）进行记录。
* 通过使用 HTTP 监控工具，可以监控从应用程序发送的点击，以提供客户获取归因验证。

>[!TIP]
>
>发送的用户代理中的变量可能会导致归因失败。
