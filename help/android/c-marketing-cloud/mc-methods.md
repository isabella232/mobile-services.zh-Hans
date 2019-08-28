---
description: 以下是 Android 库提供的 Experience Cloud ID 方法。
keywords: android；库；移动；sdk
seo-description: 以下是 Android 库提供的 Experience Cloud ID 方法。
seo-title: Adobe Experience Platform Identity Service方法
solution: Marketing Cloud，Analytics
title: Adobe Experience Platform Identity Service方法
topic: 开发人员和实施
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: a54a969bb6abedfeb0fc20276d260664b68c1d66

---


# Adobe Experience Platform Identity Service方法{#experience-cloud-id-service-methods}

以下是 Android 库提供的 Experience Cloud ID 方法。

SDK目前支持多个Adobe Experience Cloud解决方案]，包括Analytics、Target、Audience Manager和Adobe Experience Platform Identity Service。

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   将 Adobe 访客数据附加到 URL 字符串以用于 Adobe JavaScript 库。您必须具有 Mobile SDK 4.12 及更高版本才能使用此方法。有关更多信息，请参阅[附加访客 ID 辅助函数](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html)。

   >[！重要事项]
   >
   >此方法可能会导致阻止网络调用。请不要在时间敏感的线程中调用此方法。

   * 下面是这种方法对应的语法：

      ```java
      URL java.lang.String  
      ```

      将在其中附加访客信息的必需 URL 字符串。

   * 以下是这种方法的代码示例：

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   从访客 ID 服务中检索 Experience Cloud ID。

   * 下面是这种方法对应的语法：

      ```java
      public static String getMarketingCloudId(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   除了 Experience Cloud ID 之外，您还可以设置其他与每个访客关联的客户 ID。访客 API 接受同一访客具有多个客户 ID，并且使用客户类型标识符区分不同客户 ID 的适用范围。此方法对应于 JavaScript 库中的 `setCustomerIDs`。

   * 下面是这种方法对应的语法：

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **Syncidentifier**

   将提供的标识符类型和值同步到访客 ID 服务。

   传入 `authenticationState` 以作为下列值之一：

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 下面是这种方法对应的语法：

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 以下是这种方法的代码示例：

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   将提供的标识符同步到 ID 服务。

   传入 `authenticationState` 以作为下列值之一：
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 下面是这种方法对应的语法：

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 以下是这种方法的代码示例：

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   检索只读 `ADBVisitorID` 对象的列表。

   * 下面是这种方法对应的语法：

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getURLVariablesAsync**

   在版本4.16.0中引入的此方法返回一个适当的组成字符串，其中包含访问者ID服务URL变量。有关如何使用此方法的更多信息，请参阅 [Adobe Experience Platform Identity Service方法](/help/android/reference/hybrid-app.md)。

   * 下面是这种方法对应的语法：

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * 以下是这种方法的代码示例：

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
