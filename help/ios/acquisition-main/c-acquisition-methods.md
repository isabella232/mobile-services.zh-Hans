---
description: 'iOS 库提供了以下客户获取方法 '
solution: Experience Cloud,Analytics
title: 客户获取方法
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# 客户获取方法 {#acquisition-methods}

iOS 库提供了以下客户获取方法：

支持以下方法：

* **acquisitionCampaignStartForApp:data:**

   允许开发人员像用户单击链接一样，发起应用程序客户获取促销活动。这有助于自行创建手动客户获取链接并处理应用商店重定向，例如使用 `SKStoreView`。

   * 以下是此方法的语法：

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * 以下是此方法的代码示例：

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```
