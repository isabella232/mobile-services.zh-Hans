---
description: 'iOS库提供以下“获取”方法 '
seo-description: 'iOS库提供以下“获取”方法 '
seo-title: 客户获取方法
solution: Marketing Cloud,Analytics
title: 客户获取方法
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

iOS 库提供了以下客户获取方法：

支持以下方法：

* **acquisitionCampaignStartForApp:data:**

   允许开发人员像用户单击链接一样，发起应用程序客户获取促销活动。这有助于自行创建手动客户获取链接并处理应用商店重定向，例如使用 `SKStoreView`。

   * 下面是这种方法对应的语法：

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```


