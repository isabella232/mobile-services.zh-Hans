---
description: 'null'
seo-description: 'null'
seo-title: 开发人员快速入门
solution: Marketing Cloud，Analytics
title: 开发人员快速入门
topic: 开发人员和实施
uuid: b368959b-d985-436e-8b3 e-97e355 a97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

您将需要 Visual Studio 2013 或更高版本来实施 SDK。

## 获取 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

在解压缩[下载的 SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 之后，对于每种支持的架构和平台组合，您都会有一个对应的单独文件夹。您还将具有 `ADBMobileConfig.json` 文件，该文件在本指南的后面部分进行了介绍。

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). 这些文件按照以下条件划分到文件夹结构中：

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. `.winmd` 该文件仅包含元数据，并且由于此类版本的版本 `255.255.255.255` 号将根据Microsoft的要求而被接受(请参阅 [如何为WinRT C++/CX组件dll添加组合信息？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)）。To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1 通用应用商店库可用于多种编程语言。本指南中的示例采用的是 WinJS (JavaScript)，如果您使用其他语言，则可能需要进行修改。请注意，在使用 winJS (JavaScript) 中的 winmd 方法时，所有方法均自动将其第一个字母小写。

不同实施之间的主要差别在于上下文数据所使用的数据结构。

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动 Visual Studio 并打开您的解决方案。
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UIUCONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   有关更多信息，请参阅 *下面的选择正确版本* 部分。

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >在添加对Windows `ADBMobile.winmd`Phone应用程序的引用时，请将默认文件筛选器从 **[!UICONTROL 组件文件]** 更改为 **所有文件**。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您还在解决方案中有C++项目，请跳过此步骤。

1. 在左侧的 **Windows** 选项卡中，选择 **[!UICONTROL 扩展]**，然后选择并添加 **[!UICONTROL Microsoft Visual C++2013Runtime Package for Windows]**。

1. 将以下行添加到您的类中：

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 浏览到您的 `ADBMobileConfig.json` 文件，然后单击 **[!UICONTROL 添加]**。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 启动 Visual Studio 并打开您的解决方案。
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   有关更多信息，请参阅 *下面的选择正确版本* 部分。

1. Click **[!UICONTROL Add]**.

1. 在 **[!UICONTROL “引用管理器”]** 窗口中，验证是否已选中 `ADBMobile.winmd` ，然后单击 **[!UICONTROL “确定]**”。

   >[!TIP]
   >
   >在添加对Windows `ADBMobile.winmd`Phone应用程序的引用时，请将默认文件筛选器从 **[!UICONTROL 组件文件]** 更改为 **所有文件**。

1. 将以下行添加到您的类中：

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 浏览 `ADBMobileConfig.json` 到文件，然后单击 **[!UICONTROL 添加]**。

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 启动 Visual Studio 并打开您的解决方案。
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   有关更多信息，请参阅 *选择以下正确版本* 部分。

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Click **[!UICONTROL Add]**.

1. Verify that `ADBMobile.winmd` is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!TIP]
   >
   >在添加对Windows `ADBMobile.winmd`Phone应用程序的引用时，请将默认文件筛选器从 **[!UICONTROL 组件文件]** 更改为 **所有文件**。

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   如果您还在解决方案中有C++项目，请跳过此步骤。

1. 在左侧的 **[!UICONTROL Windows]** 选项卡中，选择 **[!UICONTROL 扩展]** ，然后选择并添加 **[!UICONTROL Microsoft Visual C++2013Runtime Package for Windows]**。

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. 浏览 `ADBMobileConfig.json` 到文件，然后单击 **[!UICONTROL 添加]**。

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. 选中 **[!UICONTROL “文件属性]** ”后，确保 **[!UICONTROL 将“包操作]** ”设置为 **[!UICONTROL “内容]**”。

   对于JavaScript项目，默认情况下将文件设置为 **[!UICONTROL “内容”]** 。

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json` 该文件包含全局SDK设置，并在完成 *“库”和“配置文件”到“项目* ”部分中的步骤后，位于项目根目录下。If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

至少应为您所使用的解决方案更新以下值：

* **分析**： `rsids` 并且 `server`
* **Target**: `clientCode`
* **受众管理**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## 调试 {#section_3A10376A60394A15BEE483323E0CD4AA}

如果您要对 SDK 启用调试，则必须调用 `ADBMobile.Config.setDebugLogging(true);`。

对于C Sharp和JS应用程序，您必须通过完成以下步骤来启用本机代码调试(本机代码调试是C++应用程序的默认设置)：

### C Sharp

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. 在调试器下拉列表中，选择 **[!UICONTROL “仅本机]**”。

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. 将调试器类型下拉菜单更改为&#x200B;**仅本机**。

就这么简单！您现在便可以在 Windows 8.1 通用应用商店应用程序中实施 Analytics、Target 和受众管理。
