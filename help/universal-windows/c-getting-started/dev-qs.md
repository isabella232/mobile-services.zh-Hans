---
description: 有关如何实施通用Windows平台库的信息。
solution: Experience Cloud Services,Analytics
title: 开发人员快速入门
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# 开发人员快速入门{#developer-quick-start}

以下是有关如何实施通用Windows平台库的一些信息。

>[!IMPORTANT]
>
>要实施SDK，您需要Visual Studio 2013或更高版本。

## 获取SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

在解压缩 [SDK下载](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) 文件中，您将为每个受支持的架构和平台组合提供一个单独的文件夹。 您还将拥有 `ADBMobileConfig.json` 文件。 有关此文件的更多信息，请参阅 [ADBMobileConfig.json配置文件](/help/universal-windows/c-configuration/c.json.md).

## 选择正确的版本 {#section_E53C5AA7D5474824A89BB32C003865A1}

不同 `.dll/.winmd` 为每个支持的架构(x86、x64、ARM)提供文件。

>[!IMPORTANT]
>
>的版本 `ADBMobile.winmd` 不反映库的版本。 的 `.winmd` 文件仅包含元数据，且版本号为 `255.255.255.255`，根据Microsoft的接受行为。 有关更多信息，请参阅 [如何为WinRT C++ / CX组件dll添加程序集信息？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)的问题。要检查您所使用库的版本，请检查基础库的版本 `ADBMobile.dll` 文件。

## 语法差异 {#section_A02DE120B6D240F5AFFE7509755C4F14}

通用Windows平台库可用于多种编程语言。 本指南中的示例在WinJS(JavaScript)中，如果您使用的是其他语言，则可能需要进行修改。 当您使用winJS中的winmd方法时，所有方法都会自动将其第一个字母小写。

实施之间的主要区别在于用于上下文数据的数据结构。 此外，在WinJS项目中使用SDK时，请使用空字符串( `""` 或 `''`) `null` 的值。

## 将库和配置文件添加到您的项目 — C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动Visual Studio并打开您的解决方案。
1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

1. 选择正确的库版本并浏览到关联的ADBMobile.winmd文件。

   有关更多信息，请参阅 *选择正确的版本* 部分。

1. 单击&#x200B;**添加**。

1. 验证是否在 **[!UICONTROL 引用管理器]** 窗口，单击 **[!UICONTROL 确定]**.

1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在 **[!UICONTROL Windows]** ，选择 **[!UICONTROL 扩展]**，选择并添加 **[!UICONTROL 适用于通用Windows平台应用程序的Visual C++ 2015运行时]**.

1. 将以下行添加到您的类中：

   ```csharp
   using ADBMobile;
   ```

1. 右键单击您的项目，然后单击 **[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**.

1. 浏览到 `ADBMobileConfig.json` 文件，单击 **[!UICONTROL 添加]**.

1. 右键单击 `ADBMobileConfig.json` 文件，然后选择 **[!UICONTROL 属性]**.

1. 更改 **[!UICONTROL 生成操作]** to **[!UICONTROL 内容]**.

## 将库和配置文件添加到您的项目 — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 启动Visual Studio并打开您的解决方案。
1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击您的项目并选择 **[!UICONTROL 添加]** > **[!UICONTROL 引用]**.

1. 选择正确的库版本，并添加对关联的ADBMobile.winmd文件的引用。

   有关更多信息，请参阅 *选择正确的版本* 部分。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证 `ADBMobile.winmd` 已签入 **[!UICONTROL 引用管理器]** 窗口，单击 **[!UICONTROL 确定]**.

1. 将以下行添加到您的类中：

   ```c++
   using namespace ADBMobile;
   ```

1. 右键单击您的项目并选择 **[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**.

1. 浏览到 `ADBMobileConfig.json` 文件，单击 **[!UICONTROL 添加]**.

1. 右键单击 `ADBMobileConfig.json` 文件，然后选择 **[!UICONTROL 属性]**.

1. 在 **[!UICONTROL 常规]** 选项卡，更改 **[!UICONTROL 内容]** to **[!UICONTROL 是]** 单击 **[!UICONTROL 确定]**.

## 将库和配置文件添加到您的项目 — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 启动Visual Studio并打开您的解决方案。

1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

1. 选择正确的库版本并浏览到关联的ADBMobile.winmd文件。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证是否在 **[!UICONTROL 引用管理器]** 窗口，单击 **[!UICONTROL 确定]**.

1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在 **[!UICONTROL Windows]** ，选择 **[!UICONTROL 扩展]** 选择并添加 **[!UICONTROL 适用于通用Windows平台应用程序的Visual C++ 2015运行时]**.

1. 右键单击您的项目并选择 **[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**.

1. 浏览到 `ADBMobileConfig.json` 文件，单击 **[!UICONTROL 添加]**.

1. 右键单击 `ADBMobileConfig.json` 文件，然后选择 **[!UICONTROL 属性]**.

1. 使用 **[!UICONTROL 文件属性]** 已选择，确保 **[!UICONTROL 包操作]** 设置为 **[!UICONTROL 内容]**.

   对于JavaScript项目，文件默认设置为“内容”。

## 更新ADBMobileConfig.json配置文件 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

的 `ADBMobileConfig.json` 文件包含全局SDK设置，并且在您完成 *将库和配置文件添加到您的项目* 中。 如果 `ADBMobileConfig.json` 文件未由AdobeMobile服务预配置，您需要更新一些值才能开始使用。

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

请至少为您所使用的解决方案更新以下值：

* **Adobe Analytics**: `rsids` 和 `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

有关更多信息，请参阅 [SDK方法](/help/universal-windows/c-configuration/methods.md).

## 调试 {#section_3A10376A60394A15BEE483323E0CD4AA}

要为SDK启用调试，请调用 `ADBMobile.Config.setDebugLogging(true);`.

对于C Sharp和JavaScript应用程序，您需要通过完成以下步骤来启用本机代码调试(本机代码调试是C++应用程序的默认设置):

### C锐

1. 右键单击项目，单击  **[!UICONTROL 属性]** > **[!UICONTROL “调试”选项卡]**.

1. 将调试器类型下拉列表更改为 **仅限本机**.

### JavaScript

1. 右键单击项目，单击 **[!UICONTROL 属性]** > **[!UICONTROL 配置属性]** > **[!UICONTROL “调试”选项卡]**.

1. 将调试器类型下拉列表更改为 **[!UICONTROL 仅限本机]**.

操作完成！现在，您便可以在通用Windows平台应用程序中实施Analytics、Target和受众管理。
