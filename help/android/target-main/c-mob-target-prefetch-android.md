---
description: Adobe Target 预取功能使用 Android Mobile SDK 获取选件内容，并通过缓存服务器响应来尽量减少获取次数。
seo-description: Adobe Target 预取功能使用 Android Mobile SDK 获取选件内容，并通过缓存服务器响应来尽量减少获取次数。
seo-title: 在 Android 中预取选件内容
title: 在 Android 中预取选件内容
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# 在 Android 中预取选件内容 {#prefetch-offer-content-in-android}

Adobe Target 预取功能使用 Android Mobile SDK 获取选件内容，并通过缓存服务器响应来尽量减少获取次数。

>[!IMPORTANT]
>
>Adobe Target中的“自动目标”、“自动分配”和“自动个性化”活动类型不支持Android版移动SDK中的预取功能。

此过程可缩短加载时间，阻止多个网络调用，并允许 Adobe Target 接收有关移动设备应用程序用户访问了哪个 mbox 的通知。在预取调用期间将检索和缓存所有内容，对于以后所有包含指定 mbox 名称的缓存内容的调用，都将从缓存中检索该内容。

在启动时，预取内容不会持久保留。The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

在 SDK 版本 4.14 或更高版本中，如果已指定 ，则在发起 v2 批量 mbox TNT 调用时，会从 文件中选取指定的 `environmentId``ADBMobileConfig.json`environmentId。如果未在此文件中指定 `environmentId`，则不会在 TNT 批量 mbox 调用中发送任何环境参数，将交付默认环境的选件。

例如：

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Pre-fetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

以下是可用于在 Android 中进行预取的方法：

* **prefetchContent**

   将包含位置数组的预取请求发送到配置的 Target 服务器，并在提供的回调中返回请求状态。

   * 下面是这种方法对应的语法：

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * 以下是此方法的参数：

      * **targetPrefetchArray**

         `TargetPrefetchObjects` 的数组，其中包含要预取的每个 Target 位置的名称和 mboxParameters。

      * **profileParameters**

         包含要在此请求中用于每个位置预取的配置文件参数的键和值。

      * **callback**

         在预取完成时被调用。Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **loadRequests**

   执行批量请求，以获取请求数组中指定的多个 mbox 位置。数组中的每个对象都包含一个回调函数，当其给定的 mbox 位置有相应的内容可用时，将会调用该函数。

   >[!IMPORTANT]
   >
   >如果所请求位置的内容已缓存，将立即在提供的回调中返回。 否则，SDK 将向 Target 服务器发送网络请求，以检索该内容。

   * 下面是这种方法对应的语法：

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * 以下是此方法的参数：

      * **requestArray**

         `TargetRequestObjects` 的数组，其中包含要检索的每个位置的名称、默认内容、参数和回调函数。

      * **profileParameters**

         包含要在此请求中用于每个位置预取的配置文件参数的键和值。

* **clearPrefetchCache**

   清除通过 Target 预取缓存的数据。

   * 下面是这种方法对应的语法：

      ```java
      public static void clearPrefetchCache();
      ```

   * 此方法没有参数。

* **createTargetRequestObject**

   使用提供的数据创建并返回 `TargetRequestObject` 的实例。

   * 下面是这种方法对应的语法：

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   使用提供的数据创建并返回 TargetPrefetchObject 的实例。

   * 下面是这种方法对应的语法：

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

以下是 Android 中支持预取的公共类：

### 类引用：TargetPrefetchObject

封装 mbox 名称以及用于 mbox 预取的参数。

* **`name`**

   将预取的位置的名称。
   * **类型**：字符串

* `mboxParameters`

   键值对的集合，将作为此 `mboxParameters` 请求的 `TargetPrefetchObject` 附加。
   * **类型**:地图`<String, Object>`

* **`orderParameters`**

   键值对的集合，将附加到当前位于 order 节点下方的 mbox。
   * **类型**:地图 `<String, Object>`

* **`productParameters`**

   键值对的集合，将附加到当前位于 product 节点下方的 mbox。

   * **类型**:地图 `<String, Object>`


### 类引用：TargetRequestObject

此类封装用于 Target 位置请求的 mbox 名称、默认内容、mbox 参数以及返回的回调。

* **`mboxName`**

   请求的位置的名称。

   * **类型**：字符串

* **`mboxParameters`**

   键值对的集合，将作为此 `mboxParameters` 的 `TargetRequestObject` 附加。

   * **类型：地图`<String, Object>`**

* **`orderParameters`**

   键值对的集合，将附加到当前位于 order 节点下方的 mbox。

   * **类型**:地图 `<String, Object>`

* **`productParameters`**

   键值对的集合，将附加到当前位于 product 节点下方的 mbox。

   * **类型**:地图 `<String, Object>`

* **`defaultContent`**

   SDK 无法从 Target 服务器中检索内容时在回调中返回的字符串值。

   * **类型**：字符串

* **`callback`**

   给定 `TargetRequestObject` 的内容可用时将调用的函数指针。

   * **类型**:Target.TargetCallback`<String>`


## Code sample {#section_BF7F49763D254371B4656E17953D520C}

以下是如何使用 Android SDK 预取内容的示例：

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
```

## 其他信息 {#section_A454BAD1CD49423E86C71BAEE06125FD}

以下是有关上述示例的其他一些信息：

* `ProductParameters` 仅允许使用以下键：

   * `id`
   * `categoryId`

* `OrderParameters` 仅允许使用以下键：

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` 接受字符串的数组列表。
