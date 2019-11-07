---
description: 您可以使用 iOS PhoneGap 插件方法完成多种任务。
keywords: PhoneGap
seo-description: 您可以使用 iOS PhoneGap 插件方法完成多种任务。
seo-title: PhoneGap 插件方法
solution: Marketing Cloud,Analytics
title: PhoneGap 插件方法
topic: 开发人员和实施
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap 插件方法 {#phonegap-plug-in-methods}

您可以使用 iOS PhoneGap 插件方法完成多种任务。

在要使用跟踪的 `html` 文件中，将以下内容添加到 `<head>` 标记内：

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## 配置方法 {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   返回当前用户的隐私状态。以下是可用的状态：

   * `ADB.optedIn`，立即发送点击。
   * `ADB.optedOut`，丢弃点击。
   * `ADB.optUnknown`如果您的报表包&#x200B;**启用了**&#x200B;时间戳，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。如果您的报表包&#x200B;**未启用**&#x200B;时间戳，则将丢弃点击，直到隐私状态更改为选择启用。\
      默认值在 `ADBMobileConfig.json` 文件中设置。

      * 以下是此方法的代码示例：

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   将当前用户的隐私状态设置为 `status`。您可以设置以下状态之一：
   * `ADB.optedIn`，立即发送点击。
   * `ADB.optedOut`，丢弃点击。
   * `ADB.optUnknown` - 如果您的报表包&#x200B;**启用了**&#x200B;时间戳，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。

      如果您的报表包&#x200B;**未启用**&#x200B;时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

   * 以下是此方法的代码示例：

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   返回当前用户的生命周期值。默认值为 0。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   启用 (`true`) 或禁用 (`false`) 查看调试信息。默认情况下，此变量为 `false`。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   获取库版本。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   返回自动生成的访客标识符。这是特定于应用程序的独特访客 ID，该 ID 在首次启动应用程序时生成，之后会存储并使用该 ID。在应用程序升级期间，会保留该 ID，而在应用程序卸载时，则会将其删除。

   >[!TIP]
   >
   >如果您的应用程序从 Experience Cloud 3.x SDK 升级到 4.x SDK，则会检索之前的访客 ID（自定义或自动生成）并将其存储为自定义用户标识符（请参阅下面的 `getUserIdentifier`）。这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符为 `null`，并且将使用跟踪标识符。

   * 以下是此方法的代码示例：

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   如果设置了自定义标识符，则返回自定义用户标识符；如果未设置自定义标识符，则返回 `null`。默认值为 `null`。

   * 以下是此方法的代码示例：

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   将用户标识符设置为 `identifier`。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   设置推送通知的设备令牌。

   * 以下是此方法的语法：

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   设置使生命周期会话保持活动状态的首选项。

   >[!IMPORTANT]
   >
   >调用 `keepLifecycleSessionAlive` 会阻止您的应用程序在下次从后台恢复时启动新会话。仅当您的应用程序在后台注册通知时，才应使用此方法。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   无论当前使用何种批量处理选项，都强制库发送所有排队的点击。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   获取或设置离线队列中存储的跟踪调用的数量。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   删除离线队列中存储的所有跟踪调用。

   >[!CAUTION]
   >
   >手动清除队列时请务必谨慎，因为此操作无法还原。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   指示 SDK 无论配置文件中的生命周期会话超时值为多少，下次从后台恢复时都不应启动新会话。

   >[!IMPORTANT]
   >
   >重要信息：此方法专门用于在后台注册通知的应用程序，而且只应从应用程序处于后台时运行的代码中调用。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   指示 SDK 应收集生命周期数据以在 SDK 的所有解决方案中使用。有关更多信息，请参阅[生命周期量度](/help/ios/metrics.md)。

   * 以下是此方法的代码示例：

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII 方法 {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   提交 PII 收集请求。

   * 以下是此方法的语法：

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## 跟踪方法 {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   跟踪 Adobe 深层链接点进。

   >[!TIP]
   >
   >如果生命周期调用是启动事件，将附加 Adobe 链接数据，否则，将发送一个额外调用。

   * 以下是此方法的语法：

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickThrough**

   跟踪推送消息点进。

   * 以下是此方法的语法：

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   跟踪本地通知消息点进。

   * 以下是此方法的语法：

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   通过可选的上下文数据跟踪应用程序状态。状态是您的应用程序中可用的一些视图，例如 `home dashboard`、`app settings`、`cart` 等等。这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。cData 是在上下文数据中发送的具有键值对的 JSON 对象。

   * 以下是此方法的语法：

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   跟踪您的应用程序中的操作。操作是指您的应用程序中发生的要测量的事件，包括 `logins`、`banner taps`、`feed subscriptions` 及其他量度。

   * 以下是此方法的语法：

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   跟踪后台发生的操作。此方法在某些情况下会阻止生命周期事件的触发。

   * 以下是此方法的语法：

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   发送当前的 x 和 y 坐标。此方法还使用 `ADBMobileConfig.json` 文件中定义的目标点来确定作为参数提供的位置是否位于您的任何 POI 内。如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 以下是此方法的语法：

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * 以下是此方法的代码示例：

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   向用户的生命周期值中添加 `amount`。

   * 以下是此方法的语法：

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   启动名为 `action` 的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   传入 `cData`，以更新与给定 `action` 关联的上下文数据。传入的 `cData` 会附加到给定操作的现有数据中，如果已经为 `action` 定义了相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 以下是此方法的语法：

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'}); 
      ```

* **trackTimed&#x200B;ActionEnd**

   结束定时操作。

   * 以下是此方法的代码示例：

      ```java
      ADB.trackTimedActionEnd("cartToCheckout");
      ```

* **trackingTimedActionExists**

   返回定时操作是否正在进行中。

   * 以下是此方法的语法：

      ```java
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Target 方法 {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   向您配置的 `Target` 服务器发送请求，并返回选件的字符串值。

   * 以下是此方法的语法：

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   向您配置的 Target 服务器发送请求。

   * 以下是此方法的语法：

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   从共享的 Cookie 存储中清除 Target Cookie。

   * 以下是此方法的代码示例：

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   处理 Target 服务请求。

   * 以下是此方法的语法：

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   处理 Target 服务请求。

   * 以下是此方法的语法：

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   获取 Target 服务器为此访客返回的 `SessionID` Cookie 值。

   * 以下是此方法的语法：

      ```java
      ADB.targetSessionID(success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   获取 Target 服务器为此访客返回的 `PcID` Cookie 值。

   * 以下是此方法的语法：

      ```java
      ADB.targetPcID(success,fail);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   为 Target 设置自定义访客 ID。

   * 以下是此方法的语法：

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * 以下是此组的代码示例：

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   获取 Target 的自定义访客 ID。

   * 以下是此方法的语法：

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## 客户获取方法 {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   允许开发人员像用户单击链接一样，发起应用程序客户获取促销活动。这有助于自行创建手动客户获取链接并处理应用商店重定向（例如使用 `SKStoreView`）。

   * 以下是此方法的语法：

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## 广告标识符 {#section_194607D101B047A19C51B19E176E1500}

在 Cordova 生成的 `AppDelegate` 中，调用 `application:didFinishLaunchingWithOptions:` 委托方法中的 `[ADBMobile setAdvertisingIdentifier:]`。有关更多信息，请参阅[配置方法](/help/ios/configuration/sdk-methods.md)。

## Audience Manager 方法 {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   获取访客资料。

   * 以下是此方法的语法：

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   返回 DPUUID。

   * 以下是此方法的语法：

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * 以下是此方法的代码示例：

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   返回 DPID。

   * 以下是此方法的语法：

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   设置 DPID 和 DPUUID。

   * 以下是此方法的语法：

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   处理 Audience Manager 服务请求。

   * 以下是此方法的语法：

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   重置 Audience Manager UUID 并清除当前访客资料。

   * 以下是此方法的代码示例：

      ```java
      ADB.audienceReset(); 
      ```

## ID 服务方法 {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   从 ID 服务返回 Experience Cloud ID。

   * 以下是此方法的语法：

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   将提供的标识符与 ID 服务同步。

   * 以下是此方法的语法：

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   将提供的标识符同步到访客 ID 服务。

   * 以下是此方法的语法：

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   将提供的标识符同步到访客 ID 服务。

   * 以下是此方法的语法：

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   将访客标识符附加到给定 URL。

   * 以下是此方法的语法：

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   返回已同步的所有 `visitorIDs`。

   * 以下是此方法的语法：

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```

