---
description: 'null'
seo-description: 'null'
seo-title: 开发人员快速入门
solution: Experience Cloud,Analytics
title: 开发人员快速入门
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
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

解压缩[SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)文件后，将为每个受支持的架构和平台组合提供一个单独的文件夹。 您还将有一个`ADBMobileConfig.json`文件。 有关此文件的详细信息，请参阅[ADBMobileConfig.json配置文件](/help/universal-windows/c-configuration/c.json.md)。

## 选择正确的版本{#section_E53C5AA7D5474824A89BB32C003865A1}

为每个支持的架构(x86、x64、ARM)提供不同的`.dll/.winmd`文件。

>[!IMPORTANT]
>
>`ADBMobile.winmd`的版本不反映库的版本。 `.winmd`文件仅包含元数据，版本号为`255.255.255.255`，根据Microsoft的说明，可接受此行为。 有关详细信息，请参阅[如何添加WinRT C++ / CX组件dll的程序集信息？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)的问题。要检查所使用的库版本，请检查基础`ADBMobile.dll`文件的版本。

## 语法差异{#section_A02DE120B6D240F5AFFE7509755C4F14}

通用Windows平台库可以用于多种编程语言。 本指南中的示例在WinJS(JavaScript)中，如果您使用的是其他语言，则可能需要修改。 当您从winJS中使用winmd方法时，所有方法都会自动将其第一个字母小写。

实现之间的主要区别是用于上下文数据的数据结构。 此外，在WinJS项目中使用SDK时，对空字符串值使用空字符串（`""`或`''`）而不是`null`。

## 将库和配置文件添加到您的项目 — C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动Visual Studio并打开您的解决方案。
1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

1. 选择库的正确版本，并浏览至关联的ADBMobile.winmd文件。

   有关详细信息，请参阅本页上的&#x200B;*选择正确的版本*&#x200B;部分。

1. 单击&#x200B;**添加**。

1. 确认在&#x200B;**[!UICONTROL Reference Manager]**&#x200B;窗口中检查了ADBMobile.winmd文件，然后单击&#x200B;**[!UICONTROL OK]**。

1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左侧的&#x200B;**[!UICONTROL Windows]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL 扩展]**，选择并添加&#x200B;**[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**。

1. 在类中添加以下行：

   ```csharp
   using ADBMobile;
   ```

1. 右键单击您的项目，然后单击&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**。

1. 浏览至`ADBMobileConfig.json`文件，然后单击&#x200B;**[!UICONTROL 添加]**。

1. 右键单击解决方案中的`ADBMobileConfig.json`文件，然后选择&#x200B;**[!UICONTROL 属性]**。

1. 将&#x200B;**[!UICONTROL 构建操作]**&#x200B;更改为&#x200B;**[!UICONTROL 内容]**。

## 将库和配置文件添加到项目 — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 启动Visual Studio并打开您的解决方案。
1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击项目并选择&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 引用]**。

1. 选择库的正确版本，并添加对关联的ADBMobile.winmd文件的引用。

   有关详细信息，请参阅本页上的&#x200B;*选择正确的版本*&#x200B;部分。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证是否在&#x200B;**[!UICONTROL 引用管理器]**&#x200B;窗口中选中`ADBMobile.winmd`，然后单击&#x200B;**[!UICONTROL 确定]**。

1. 在类中添加以下行：

   ```c++
   using namespace ADBMobile;
   ```

1. 右键单击您的项目，然后选择&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**。

1. 浏览至`ADBMobileConfig.json`文件，然后单击&#x200B;**[!UICONTROL 添加]**。

1. 右键单击解决方案中的`ADBMobileConfig.json`文件，然后选择&#x200B;**[!UICONTROL 属性]**。

1. 在&#x200B;**[!UICONTROL 常规]**&#x200B;选项卡上，将&#x200B;**[!UICONTROL 内容]**&#x200B;更改为&#x200B;**[!UICONTROL 是]**，然后单击&#x200B;**[!UICONTROL 确定]**。

## 将库和配置文件添加到项目 — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 启动Visual Studio并打开您的解决方案。

1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

1. 选择库的正确版本，并浏览至关联的ADBMobile.winmd文件。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 确认在&#x200B;**[!UICONTROL Reference Manager]**&#x200B;窗口中检查了ADBMobile.winmd文件，然后单击&#x200B;**[!UICONTROL OK]**。

1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左侧的&#x200B;**[!UICONTROL Windows]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL 扩展]**，然后选择并添加&#x200B;**[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**。

1. 右键单击您的项目，然后选择&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**。

1. 浏览至`ADBMobileConfig.json`文件，然后单击&#x200B;**[!UICONTROL 添加]**。

1. 右键单击解决方案中的`ADBMobileConfig.json`文件，然后选择&#x200B;**[!UICONTROL 属性]**。

1. 选择&#x200B;**[!UICONTROL 文件属性]**&#x200B;后，确保将&#x200B;**[!UICONTROL 包操作]**&#x200B;设置为&#x200B;**[!UICONTROL 内容]**。

   对于JavaScript项目，默认情况下将文件设置为“内容”。

## 更新ADBMobileConfig.json配置文件{#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json`文件包含全局SDK设置，在您完成&#x200B;*将库和配置文件添加到项目*&#x200B;部分中的步骤后，该文件位于您的项目根目录下。 如果您的`ADBMobileConfig.json`文件未由Adobe Mobile Services预配置，则需要更新一些值才能开始。

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

至少为您所使用的解决方案更新以下值：

* **Adobe Analytics**: `rsids` 和  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

有关详细信息，请参阅[SDK方法](/help/universal-windows/c-configuration/methods.md)。

## 调试 {#section_3A10376A60394A15BEE483323E0CD4AA}

要启用SDK调试，请调用`ADBMobile.Config.setDebugLogging(true);`。

对于C Sharp和JavaScript应用程序，您需要通过完成以下步骤（本机代码调试是C++应用程序的默认设置）启用本机代码调试：

### C锐

1. 右键单击项目，单击&#x200B;**[!UICONTROL 属性]** > **[!UICONTROL 调试选项卡]**。

1. 将调试器类型下拉列表更改为&#x200B;**仅本机**。

### JavaScript

1. 右键单击项目，单击&#x200B;**[!UICONTROL 属性]** > **[!UICONTROL 配置属性]** > **[!UICONTROL 调试选项卡]**。

1. 将调试器类型下拉列表更改为&#x200B;**[!UICONTROL 仅本机]**。

操作完成！您现在已准备好在通用Windows平台应用程序中实施分析、目标和受众管理。
