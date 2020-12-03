---
description: 'null'
seo-description: 'null'
seo-title: 开发人员快速入门
solution: Experience Cloud,Analytics
title: 开发人员快速入门
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---


# 开发人员快速入门{#developer-quick-start}

以下是关于如何实施通用Windows平台库的一些信息。

>[!IMPORTANT]
>
>要实施SDK，您需要Visual Studio 2013或更高版本。

## 获取SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

解压缩SDK下 [载文件后](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) ，您将为每个受支持的架构和平台组合提供一个单独的文件夹。 您还将有一个 `ADBMobileConfig.json` 文件。 有关此文件的详细信息，请 [参阅ADBMobileConfig.json配置文件](/help/universal-windows/c-configuration/c.json.md)。

## 选择正确的版本 {#section_E53C5AA7D5474824A89BB32C003865A1}

为 `.dll/.winmd` 每个支持的体系结构(x86、x64、ARM)提供不同的文件。

>[!IMPORTANT]
>
>版本不 `ADBMobile.winmd` 反映库的版本。 文 `.winmd` 件仅包含元数据，版本号 `255.255.255.255`为，根据Microsoft，此版本为接受行为。 有关详细信息， [请参阅如何添加WinRT C++ / CX组件dll的程序集信息？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)的问题。要检查您所使用的库的版本，请检查基础文件的版 `ADBMobile.dll` 本。

## 语法差异 {#section_A02DE120B6D240F5AFFE7509755C4F14}

通用Windows平台库可用于多种编程语言。 本指南中的示例在WinJS(JavaScript)中，如果您使用的是其他语言，则可能需要修改。 使用winJS中的winmd方法时，所有方法都会自动将其第一个字母小写。

实现之间的主要区别是用于上下文数据的数据结构。 此外，在WinJS项目中使用SDK时，请使用空字符串( `""` 或 `''`)而不 `null` 是空字符串值。

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动Visual Studio并打开您的解决方案。
1. 在“解决 **[!UICONTROL 方案浏览器]**”中，右键单击“ **[!UICONTROL 引用]** ”，然后选 **[!UICONTROL 择“添加引用”]**。

1. 选择库的正确版本并浏览至关联的ADBMobile.winmd文件。

   有关详细信息，请 *参阅本页上的* “选择正确的版本”部分。

1. 单击&#x200B;**添加**。

1. 验证是否在“Reference Manager（引用管理器）”窗口中选中了ADBMobile. **[!UICONTROL winmd文件]** ，然后单 **[!UICONTROL 击“OK]**”。

1. 在“解决 **[!UICONTROL 方案浏览器]**”中，右键单击“ **[!UICONTROL 引用]** ”，然后选 **[!UICONTROL 择“添加引用”]**。

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左侧 **[!UICONTROL 的]** Windows选项卡中，选择“扩展 **[!UICONTROL ”]**，选择并添 **[!UICONTROL 加“Visual C++ 2015 Runtime for Universal Windows Platform Apps”]**。

1. 将以下代码行添加到您的类中：

   ```csharp
   using ADBMobile;
   ```

1. 右键单击您的项目，然后单击“添 **[!UICONTROL 加]** ”>“ **[!UICONTROL 现有项目]**”。

1. 浏览至文件 `ADBMobileConfig.json` 并单击“添 **[!UICONTROL 加”]**。

1. 右键单击解决方案 `ADBMobileConfig.json` 中的文件，然后选择 **[!UICONTROL 属性]**。

1. 将“ **[!UICONTROL 构建操作]** ”更 **[!UICONTROL 改为内容]**。

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 启动Visual Studio并打开您的解决方案。
1. 在“解决 **[!UICONTROL 方案浏览器]**”中，右键单击项目并选 **[!UICONTROL 择“添加]** ” **[!UICONTROL >“]**&#x200B;引用”。

1. 选择库的正确版本并添加对关联的ADBMobile.winmd文件的引用。

   有关详细信息，请 *参阅本页上的* “选择正确的版本”部分。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证是 `ADBMobile.winmd` 否在“Reference Manager(引用 **[!UICONTROL 管理器)”窗口中选中]** ，然后单 **[!UICONTROL 击“OK（确定）]**”。

1. 将以下代码行添加到您的类中：

   ```c++
   using namespace ADBMobile;
   ```

1. 右键单击您的项目，然后选择“ **[!UICONTROL 添加]** ”> **[!UICONTROL “现有项目]**”。

1. 浏览至文 `ADBMobileConfig.json` 件，然后单 **[!UICONTROL 击添加]**。

1. 右键单击解决方案 `ADBMobileConfig.json` 中的文件，然后选择“ **[!UICONTROL 属性”]**。

1. 在“常规 **[!UICONTROL ”]** 选项卡上，将“内 **[!UICONTROL 容]****[!UICONTROL ”更]** 改为“是 **[!UICONTROL ”，然]**&#x200B;后单击“确定”。

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 启动Visual Studio并打开您的解决方案。

1. 在“解决 **[!UICONTROL 方案浏览器]**”中，右键单击“ **[!UICONTROL 引用]** ”，然后选 **[!UICONTROL 择“添加引用”]**。

1. 选择库的正确版本并浏览至关联的ADBMobile.winmd文件。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证是否在“Reference Manager（引用管理器）”窗口中选中了ADBMobile. **[!UICONTROL winmd文件]** ，然后单 **[!UICONTROL 击“OK]**”。

1. 在“解决 **[!UICONTROL 方案浏览器]**”中，右键单击“ **[!UICONTROL 引用]** ”，然后选 **[!UICONTROL 择“添加引用”]**。

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左 **[!UICONTROL 侧的]** Windows选项卡中，选择“扩 **[!UICONTROL 展]** ”，然后选择并添 **[!UICONTROL 加“Visual C++ 2015 Runtime for Universal Windows Platform Apps”]**。

1. 右键单击您的项目，然后选择“ **[!UICONTROL 添加]** ”> **[!UICONTROL “现有项目]**”。

1. 浏览至文件 `ADBMobileConfig.json` 并单击“添 **[!UICONTROL 加”]**。

1. 右键单击解决方案 `ADBMobileConfig.json` 中的文件，然后选择“ **[!UICONTROL 属性”]**。

1. 选择 **[!UICONTROL “文件属性]** ”，确保将“ **[!UICONTROL 包操作]** ”设置为“ **[!UICONTROL 内容”]**。

   对于JavaScript项目，默认情况下将文件设置为“内容”。

## 更新ADBMobileConfig.json配置文件 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

文 `ADBMobileConfig.json` 件包含全局SDK设置，在您完成“将库和配置文件添加到项目”部 *分中的步骤后，该文件位于项目根目录* 。 如果 `ADBMobileConfig.json` AdobeMobile Services未预配置文件，您需要更新一些值才能开始。

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

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## 调试 {#section_3A10376A60394A15BEE483323E0CD4AA}

要启用SDK调试，请致电 `ADBMobile.Config.setDebugLogging(true);`。

对于C Sharp和JavaScript应用程序，您需要通过完成以下步骤（本机代码调试是C++应用程序的默认设置）启用本机代码调试：

### C Sharp

1. 右键单击项目，单击“属性 **[!UICONTROL ”]** >“调 **[!UICONTROL 试”选项卡]**。

1. 将调试器类型下拉框更改为“仅 **限本机**”。

### JavaScript

1. 右键单击项目，单击“属 **[!UICONTROL 性]** ”>“ **[!UICONTROL 配置属性]** ” **[!UICONTROL >“调]**&#x200B;试”选项卡。

1. 将调试器类型下拉框更改为“仅 **[!UICONTROL 限本机]**”。

操作完成！您现在已准备好在通用Windows平台应用程序中实施分析、目标和受众管理。

