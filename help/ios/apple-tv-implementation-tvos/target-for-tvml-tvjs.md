---
description: 通过直接替换 .xml 文件，可以在 TVML/TVJS 应用程序中利用 Adobe Target。可使用自定义 ADBTarget XML 元素指定要被 Target 内容替换的页面区域。
seo-description: 通过直接替换 .xml 文件，可以在 TVML/TVJS 应用程序中利用 Adobe Target。可使用自定义 ADBTarget XML 元素指定要被 Target 内容替换的页面区域。
seo-title: 适用于 TVML/TVJS 的 Adobe Target
title: 适用于 TVML/TVJS 的 Adobe Target
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# 适用于 TVML/TVJS 的 Adobe Target{#adobe-target-for-tvml-tvjs}

通过直接替换 .xml 文件，可以在 TVML/TVJS 应用程序中利用 Adobe Target。可使用自定义 ADBTarget XML 元素指定要被 Target 内容替换的页面区域。

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. For more information, see Apple TV Implementation with tvOS.[](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)

## 入门指南 {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>您应该相应地计划要替换的内容。

您的用例可能不像在标签中替换字符串值一样简单，也不像替换整个页面一样复杂。

## Configure your ADBTarget element {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

在 `ADBTarget` 元素中，您必须在 `mbox` 属性中提供 Mbox 名称。You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Mbox 位置名称.

   * Property type: String
   * 此属性为必需属性。

* **`id`**

   The Order ID.

   * Property type: String
   * 此属性不 **是必需** 。

* **`total`**

   The order total.

   * 属性类型：字符串
   * 此属性不 **是必需** 。

* **`purchasedProductIds`**

   此订单的已购产品 ID 的逗号分隔列表。

   * 以下是此属性的代码示例：


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * 属性类型：字符串
   * This property is not required.****

* **`mboxParameters`**

   `mboxParameters` 的键值对列表。此字符串中的每个条目都以分号分隔，键值以冒号分隔。

   * 以下是此属性的代码示例：

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * 属性类型：字符串
   * 此属性不 **是必需** 。

* **`customParameterName`**

   此属性的值为 `customParameterValue`。

   * 属性类型：字符串
   * 此属性不 **是必需** 。


## 示例 {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### 示例 1

以下示例在 `ADBTarget` 页面中使用 `LandingPage.xml.js` 元素来替换警报的内容：

#### 配置 Target

假定您有一个名为 `landingPage` 的 Mbox 位置，并且选件内容的设置如下所示：

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### 配置 landingPage.xml.js

* 以下是 landingPage.xml.js 的配置：

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* 如果对 Target 的请求成功，并且返回了您的选件内容，则您的页面将最终为：

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* 如果 Target 服务器无法访问或请求超时，则您的页面将最终为：

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
