---
description: 以下是 Android 库提供的 Experience Cloud ID 方法。
keywords: Android;库;移动;SDK
seo-description: 以下是 Android 库提供的 Experience Cloud ID 方法。
seo-title: Adobe Experience Platform Identity Service 方法
solution: Experience Cloud,Analytics
title: Adobe Experience Platform Identity Service 方法
topic-fix: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
exl-id: 8eb98c3f-c6ef-4593-ad3a-f566f4d4b6a2
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 100%

---

# Adobe Experience Platform Identity Service 方法 {#experience-cloud-id-service-methods}

以下是 Android 库提供的 Experience Cloud ID 方法。

SDK 当前支持多个 Adobe Experience Cloud 解决方案，包括 Analytics、Target、Audience Manager 和 Adobe Experience Platform Identity Service。

方法将根据解决方案来添加前缀。例如，Experience Cloud ID 方法的前缀为 `visitor`。有关更多信息，请参阅 [Experience Cloud ID 配置](/help/android/c-marketing-cloud/mcvid.md)。

* **public static String appendToURL(final String URL)**

   将 Adobe 访客数据附加到 URL 字符串以用于 Adobe JavaScript 库。您必须拥有 Mobile SDK 4.12 及更高版本才能使用此方法。有关更多信息，请参阅[附加访客 ID 辅助函数](https://docs.adobe.com/content/help/zh-Hans/id-service/using/id-service-api/methods/appendvisitorid.html)。

   >[!IMPORTANT]
   >
   >此方法可能导致网络调用受阻。请不要在时间敏感的线程中调用此方法。

   * 以下是此方法的语法：

      ```java
      public static String appendToURL(final String URL) 
      ```

      将在其中附加访客信息的必需 URL 字符串。

   * 以下是此方法的代码示例：

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   从访客 ID 服务中检索 Experience Cloud ID。

   * 以下是此方法的语法：

      ```java
      public static String getMarketingCloudId(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >此方法可能导致网络调用受阻，因此&#x200B;**不应**&#x200B;从用户界面线程中对其进行调用。

* **syncIdentifiers**

   使用该 Experience Cloud ID，您可以设置其他可与每个访客关联的客户 ID。访客 API 接受同一访客具有多个客户 ID，并且使用客户类型标识符区分不同客户 ID 的适用范围。此方法对应于 JavaScript 库中的 `setCustomerIDs`。

   * 以下是此方法的语法：

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * 以下是此方法的代码示例：

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   将提供的标识符类型和值同步到访客 ID 服务。

   传入 `authenticationState` 以作为下列值之一：

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 以下是此方法的语法：

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 以下是此方法的代码示例：

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   将提供的标识符同步到 ID 服务。

   传入 `authenticationState` 以作为下列值之一：
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * 以下是此方法的语法：

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * 以下是此方法的代码示例：

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   检索只读 `ADBVisitorID` 对象的列表。

   * 以下是此方法的语法：

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * 以下是此方法的代码示例：

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   在版本 4.16.0 中引入，此方法会返回一个格式正确的字符串，其中包含访客 ID 服务 URL 变量。有关如何使用此方法的更多信息，请参阅 [Adobe Experience Platform Identity Service 方法](/help/android/reference/hybrid-app.md)。

   * 以下是此方法的语法：

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * 以下是此方法的代码示例：

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

## 公共方法 {#section_8AC744B431A3438C9B45629CA3EA0F51}

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
