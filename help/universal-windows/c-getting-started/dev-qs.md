---
description: 'null'
seo-description: 'null'
seo-title: 开发人员快速入门
solution: Marketing Cloud,Analytics
title: 开发人员快速入门
topic: 开发人员和实施
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Here is some information about how to implement the Universal Windows Platform library.

>[!IMPORTANT]
>
>要实施SDK，您需要Visual Studio 2013或更高版本。

## 获取 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. 您还会有一个 `ADBMobileConfig.json` 文件。 有关此文件的详细信息，请参 [阅ADBMobileConfig.json配置文件](/help/universal-windows/c-configuration/c.json.md)。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. 该文 `.winmd` 件仅包含元数据，并具有版本号， `255.255.255.255`根据Microsoft的规定，该版本号为可接受的行为。 有关详细信息，请 [参阅如何为WinRT C++ / CX组件dll添加组件信息？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## 语法差异 {#section_A02DE120B6D240F5AFFE7509755C4F14}

通用 Windows 平台库可用于多种编程语言。本指南中的示例在WinJS(JavaScript)中，如果您使用的是其他语言，则可能需要修改。 当您使用winJS中的winmd方法时，所有方法都会自动将其第一个字母小写。

不同实施之间的主要差别在于上下文数据所使用的数据结构。Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动 Visual Studio 并打开您的解决方案。
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Select the correct version  of the library and browse to the associated ADBMobile.winmd file.

   有关详细信息，请参 *阅在此页上选择正确的版* 本部分。

1. 单击&#x200B;**添加**。

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左侧的 **[!UICONTROL Windows]** 选项卡中，选择“扩展” ****，选择并添加 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**。

1. 将以下行添加到您的类中：

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 浏览至文件 `ADBMobileConfig.json` 并单击“添 **[!UICONTROL 加”]**。

1. 右键单击解决方 `ADBMobileConfig.json` 案中的文件，然后选择 **[!UICONTROL 属性]**。

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 启动 Visual Studio 并打开您的解决方案。
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. 选择库的正确版本，并添加对关联的ADBMobile.winmd文件的引用。

   有关详细信息，请参 *阅在此页上选择正确的版* 本部分。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. 将以下行添加到您的类中：

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 启动 Visual Studio 并打开您的解决方案。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated ADBMobile.winmd file.

1. Click **[!UICONTROL Add]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左侧的 **[!UICONTROL Windows]** 选项卡中，选择“扩展” **** ，然后选择并添加 **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 浏览至文件 `ADBMobileConfig.json` 并单击“添 **[!UICONTROL 加”]**。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. 选择“ **[!UICONTROL 文件属性]** ”后，确保将“ **[!UICONTROL 包操作]** ”设置为“ **[!UICONTROL 内容”]**。

   对于JavaScript项目，默认情况下将文件设置为“内容”。

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

以下是 `ADBMobileConfig.json` 文件的示例：

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

至少要更新您所使用的解决方案的以下值：

* **Adobe Analytics**: `rsids` 和 `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

有关详细信息，请参 [阅SDK方法](/help/universal-windows/c-configuration/methods.md)。

## 调试 {#section_3A10376A60394A15BEE483323E0CD4AA}

要启用SDK调试，请致电 `ADBMobile.Config.setDebugLogging(true);`。

对于C Sharp和JavaScript应用程序，您需要通过完成以下步骤启用本机代码调试（本机代码调试是C++应用程序的默认设置）:

### C锐化

1. 右键单击项目，单击“属性” **[!UICONTROL &gt;“调]** 试”选项卡 ****。

1. 将调试器类型下拉菜单更改为&#x200B;**仅本机**。

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Change the debugger type drop down to **[!UICONTROL Native Only]**.

就这么简单！您现在便可以在通用 Windows 平台应用程序中实施 Analytics、Target 和受众管理。

