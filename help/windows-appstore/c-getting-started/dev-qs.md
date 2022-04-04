---
description: 开发人员快速入门文章
solution: Experience Cloud Services,Analytics
title: 开发人员快速入门
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# 开发人员快速入门 {#developer-quick-start}

您需要Visual Studio 2013或更高版本才能实施SDK。

## 获取SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

在解压缩 [SDK下载](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)，则您将为每个受支持的架构和平台组合提供一个单独的文件夹。 您还将拥有 `ADBMobileConfig.json` 本指南后面介绍的文件。

## 选择正确的版本 {#section_E53C5AA7D5474824A89BB32C003865A1}

不同 `.dll`/ `.winmd` 为每个目标平台(Windows 8.1、Windows Phone 8.1)和支持的架构(x86、x64、ARM)提供文件。 这些文件按照以下规则分为文件夹结构：

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>的版本 `ADBMobile.winmd` 不反映库的版本。 的 `.winmd` 文件仅包含元数据，因此将具有版本号 `255.255.255.255` Microsoft接受的行为(请参阅 [如何为WinRT C++ / CX组件dll添加程序集信息？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode))。要检查您所使用库的版本，请检查基础库的版本 `ADBMobile.dll` 文件。

## 语法差异 {#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1通用App Store库可以用于多种编程语言。 本指南中的示例位于WinJS(JavaScript)中，如果您使用的是其他语言，则可能需要修改这些示例。 请注意，当您使用winJS(JavaScript)中的winmd方法时，所有方法都会自动将其第一个字母小写。

实施之间的主要区别在于用于上下文数据的数据结构。

此外，在WinJS项目中使用SDK时，请使用空字符串( `""` 或 `''`) `null` 的值。

## 将库和配置文件添加到您的项目 — C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动Visual Studio并打开您的解决方案。
1. 在 **解决方案浏览器**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

1. 选择正确的库版本并浏览到关联的 `ADBMobile.winmd` 文件。

   有关更多信息，请参阅 *选择正确的版本* 部分。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证 `ADBMobile.winmd` 的 **[!UICONTROL 引用管理器]** 窗口，单击 **[!UICONTROL 确定]**.

   >[!NOTE]
   >
   >添加对Windows Phone应用程序的引用时，选择 `ADBMobile.winmd`，请将默认文件筛选器从 **[!UICONTROL 组件文件]** to **所有文件**.

1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在 **Windows** ，选择 **[!UICONTROL 扩展]**，然后选择并添加 **[!UICONTROL Microsoft Visual C++ 2013 Windows运行时包]**.

1. 将以下行添加到您的类中：

   ```
   using ADBMobile;
   ```

1. 右键单击您的项目并选择 **[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**.

1. 浏览到 `ADBMobileConfig.json` 文件，单击 **[!UICONTROL 添加]**.

1. 右键单击 `ADBMobileConfig.json` 文件，然后选择 **[!UICONTROL 属性]**.

1. 更改 **[!UICONTROL 生成操作]** to **[!UICONTROL 内容]**.

## 将库和配置文件添加到您的项目 — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 启动Visual Studio并打开您的解决方案。
1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击您的项目并选择 **[!UICONTROL 添加]** > **[!UICONTROL 引用]**.

1. 选择正确的库版本，然后添加对关联的 `ADBMobile.winmd` 文件。

   有关更多信息，请参阅 *选择正确的版本* 部分。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 在 **[!UICONTROL 引用管理器]** 窗口，验证 `ADBMobile.winmd` 选中并单击 **[!UICONTROL 确定]**.

   >[!TIP]
   >
   >添加对Windows Phone应用程序的引用时，选择 `ADBMobile.winmd`，请将默认文件筛选器从 **[!UICONTROL 组件文件]** to **所有文件**.

1. 将以下行添加到您的类中：

   ```
   using namespace ADMS::Measurement;
   ```

1. 右键单击您的项目并选择 **[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**.

1. 浏览到 `ADBMobileConfig.json` 文件，单击 **[!UICONTROL 添加]**.

1. 右键单击 `ADBMobileConfig.json` 文件，然后选择 **[!UICONTROL 属性]**.

1. 在 **[!UICONTROL 常规]** 选项卡，更改 **[!UICONTROL 内容]** to **[!UICONTROL 是]**，然后单击 **[!UICONTROL 确定]**.

## 将库和配置文件添加到您的项目 — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 启动Visual Studio并打开您的解决方案。
1. 在 **解决方案浏览器**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

   有关更多信息，请参阅 *选择正确的版本* 部分。

1. 选择正确的库版本，然后浏览到关联的 `ADBMobile.winmd` 文件。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证 `ADBMobile.winmd` 已签入 **[!UICONTROL 引用管理器]** 窗口，单击 **[!UICONTROL 确定]**.

   >[!TIP]
   >
   >添加对Windows Phone应用程序的引用时，选择 `ADBMobile.winmd`，请将默认文件筛选器从 **[!UICONTROL 组件文件]** to **所有文件**.

1. 在 **[!UICONTROL 解决方案浏览器]**，右键单击 **[!UICONTROL 引用]** 选择 **[!UICONTROL 添加引用]**.

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在 **[!UICONTROL Windows]** ，选择 **[!UICONTROL 扩展]** 选择并添加 **[!UICONTROL Microsoft Visual C++ 2013 Windows运行时包]**.

1. 右键单击您的项目并选择 **[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**.

1. 浏览到 `ADBMobileConfig.json` 文件，单击 **[!UICONTROL 添加]**.

1. 右键单击 `ADBMobileConfig.json]` 文件，然后选择 **[!UICONTROL 属性]**.

1. 使用 **[!UICONTROL 文件属性]** 已选择，确保 **[!UICONTROL 包操作]** 设置为 **[!UICONTROL 内容]**.

   对于JavaScript项目，文件将设置为 **[!UICONTROL 内容]** 默认情况下。

## 更新ADBMobileConfig.json配置文件 {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

的 `ADBMobileConfig.json` 文件包含全局SDK设置，并且在您完成 *将库和配置文件添加到您的项目* 中。 如果 `ADBMobileConfig.json` 文件未由AdobeMobile服务预配置，您需要更新一些值才能开始使用。

以下是 `ADBMobileConfig.json` 文件：

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

* **Analytics**: `rsids` 和 `server`
* **Target**: `clientCode`
* **受众管理**: `server`

有关更多详细信息，请参阅 [ADBMobileConfig.json配置](/help/windows-appstore/c-configuration/methods.md).

## 调试 {#section_3A10376A60394A15BEE483323E0CD4AA}

当您想要为SDK启用调试时，必须调用 `ADBMobile.Config.setDebugLogging(true);`.

对于C Sharp和JS应用程序，您必须完成以下步骤来启用本机代码调试(本机代码调试是C++应用程序的默认设置):

### C锐

右键单击项目，选择 **[!UICONTROL 属性]** > **[!UICONTROL “调试”选项卡]**. 在Debugger下拉菜单中，选择 **[!UICONTROL 仅限本机]**.

### JS

右键单击项目，选择  **[!UICONTROL 属性]** > **[!UICONTROL 配置属性]** > **[!UICONTROL “调试”选项卡]**. 将调试器类型下拉列表更改为 **仅限本机**.

操作完成！现在，您已准备好在Windows 8.1通用App Store应用程序中实施Analytics、Target和受众管理。
