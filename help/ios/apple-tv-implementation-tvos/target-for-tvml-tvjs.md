---
description: 您可以通过直接替换.xml文件，在TVML/TVJS应用程序中利用Adobe Target。 使用自定义ADBTarget XML元素指定要由Target内容替换的页面区域。
title: 适用于 TVML/TVJS 的 Adobe Target
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
exl-id: 9348d49c-2a5a-4ea0-b90d-99d446bd336a
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 75%

---

# 适用于 TVML/TVJS 的 Adobe Target{#adobe-target-for-tvml-tvjs}

您可以通过直接替换.xml文件，在TVML/TVJS应用程序中利用Adobe Target。 使用自定义ADBTarget XML元素指定要由Target内容替换的页面区域。

>[!IMPORTANT]
>
>在 TVML 页面中使用 `ADBTarget` 元素之前，必须将 TVML/TVJS 应用程序配置为使用 tvOS SDK。有关更多信息，请参阅[使用 tvOS 实施 Apple TV](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)。

## 快速入门 {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. 找到要使用 Target 位置的 `.xml` 文件。
1. 将 `ADBTarget` 元素作为 `<document>` 元素的子项添加到该文件中。
1. 如果 Target 找不到 Mbox 位置或发生超时，将使用 `<ADBTarget>` 和 `</ADBTarget>` 标记之间的值作为默认内容。

## 在 Target 中配置 Mbox {#section_F2DA140C34B0421D976046F825B23123}

从 Target 返回的内容将替换 `<ADBTarget>` 和 `</ADBTarget>` 之间的所有内容，其中包括两个 `ADBTarget` 标记。

>[!TIP]
>
>您应当相应地计划要替换的内容。

您的用例可能不像在标签中替换字符串值一样简单，也不像替换整个页面一样复杂。

## 配置 ADBTarget 元素 {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

在 `ADBTarget` 元素中，您必须在 `mbox` 属性中提供 Mbox 名称。您可以选择采用 `customParameterName="customParameterValue"` 格式将自定义属性添加到请求中。

* **`mbox`**

   Mbox 位置名称。

   * 属性类型：字符串
   * 此属性是必需的。

* **`id`**

   订单 ID。

   * 属性类型：字符串
   * 此属性&#x200B;**不是**&#x200B;必需的。

* **`total`**

   订单总计。

   * 属性类型：字符串
   * 此属性&#x200B;**不是**&#x200B;必需的。

* **`purchasedProductIds`**

   此订单的已购产品 ID 的逗号分隔列表。

   * 以下是此属性的代码示例：


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * 属性类型：字符串
   * 此属性&#x200B;**不是**&#x200B;必需的。

* **`mboxParameters`**

   `mboxParameters` 的键值对列表。此字符串中的各条目用分号分隔，键值用冒号分隔。

   * 以下是此属性的代码示例：

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * 属性类型：字符串
   * 此属性&#x200B;**不是**&#x200B;必需的。

* **`customParameterName`**

   此属性的值为 `customParameterValue`。

   * 属性类型：字符串
   * 此属性&#x200B;**不是**&#x200B;必需的。


## 示例 {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### 示例 1

以下示例在 `LandingPage.xml.js` 页面中使用 `ADBTarget` 元素来替换警报的内容：

#### 配置 Target

假定您有一个名为 `landingPage` 的 Mbox 位置，并且选件内容的设置如下所示：

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### 配置 landingPage.xml.js

* 以下是landingPage.xml.js的配置：

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* 如果对Target的请求成功，并且返回了选件内容，则您的页面将生成：

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* 如果无法访问Target服务器或请求超时，则页面将生成：

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### 示例 2

以下示例说明了如何将自定义数据添加到 `ADBTarget` 元素。您可以通过此方法在 Target 中为此 Mbox 位置创建条件式体验和选件内容：

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
