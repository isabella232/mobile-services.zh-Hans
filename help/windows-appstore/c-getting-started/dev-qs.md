---
description: 'null'
seo-description: 'null'
seo-title: 开发人员快速入门
solution: Experience Cloud,Analytics
title: 开发人员快速入门
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 2%

---

# 开发人员快速入门 {#developer-quick-start}

您需要Visual Studio 2013或更高版本才能实施SDK。

## 获取SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

解压缩[SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)后，您将为每个受支持的架构和平台组合提供一个单独的文件夹。 您还将有一个`ADBMobileConfig.json`文件，本指南后面将说明。

## 选择正确的版本{#section_E53C5AA7D5474824A89BB32C003865A1}

为每个目标平台(Windows 8.1、Windows Phone 8.1)和支持的架构(x86、x64、ARM)提供不同的`.dll`/ `.winmd`文件。 根据以下规定，这些文件将分为文件夹结构：

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>`ADBMobile.winmd`的版本不反映库的版本。 `.winmd`文件仅包含元数据，因此将包含一个版本号`255.255.255.255`，该版本号根据Microsoft被接受的行为(请参阅[如何添加WinRT C++ / CX组件dll的程序集信息？](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode))。要检查所使用的库版本，请检查基础`ADBMobile.dll`文件的版本。

## 语法差异{#section_A02DE120B6D240F5AFFE7509755C4F14}

Windows 8.1通用应用程序商店库可以用于多种编程语言。 本指南中的示例位于WinJS(JavaScript)中，如果您使用的是其他语言，则可能需要修改。 请注意，当您从winJS(JavaScript)中使用winmd方法时，所有方法都会自动将其第一个字母小写。

实现之间的主要区别是用于上下文数据的数据结构。

此外，在WinJS项目中使用SDK时，对空字符串值使用空字符串（`""`或`''`）而不是`null`。

## 将库和配置文件添加到项目 — C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. 启动Visual Studio并打开您的解决方案。
1. 在&#x200B;**解决方案资源管理器**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

1. 选择库的正确版本并浏览至关联的`ADBMobile.winmd`文件。

   有关详细信息，请参阅下面的&#x200B;*选择正确的版本*&#x200B;部分。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证是否在&#x200B;**[!UICONTROL 引用管理器]**&#x200B;窗口中选择了`ADBMobile.winmd`，然后单击&#x200B;**[!UICONTROL 确定]**。

   >[!NOTE]
   >
   >添加对Windows Phone应用程序的引用时，要选择`ADBMobile.winmd`，请将默认文件过滤器从&#x200B;**[!UICONTROL 组件文件]**&#x200B;更改为&#x200B;**所有文件**。

1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左侧的&#x200B;**Windows**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL 扩展]**，然后选择并添加&#x200B;**[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**。

1. 在类中添加以下行：

   ```
   using ADBMobile;
   ```

1. 右键单击您的项目，然后选择&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**。

1. 浏览至您的`ADBMobileConfig.json`文件，然后单击&#x200B;**[!UICONTROL 添加]**。

1. 右键单击解决方案中的`ADBMobileConfig.json`文件，然后选择&#x200B;**[!UICONTROL 属性]**。

1. 将&#x200B;**[!UICONTROL 构建操作]**&#x200B;更改为&#x200B;**[!UICONTROL 内容]**。

## 将库和配置文件添加到项目 — C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. 启动Visual Studio并打开您的解决方案。
1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击项目并选择&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 引用]**。

1. 选择库的正确版本，然后添加对关联的`ADBMobile.winmd`文件的引用。

   有关详细信息，请参阅下面的&#x200B;*选择正确版本*&#x200B;部分。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 在&#x200B;**[!UICONTROL 引用管理器]**&#x200B;窗口中，验证是否已选择`ADBMobile.winmd`，然后单击&#x200B;**[!UICONTROL 确定]**。

   >[!TIP]
   >
   >添加对Windows Phone应用程序的引用时，要选择`ADBMobile.winmd`，请将默认文件过滤器从&#x200B;**[!UICONTROL 组件文件]**&#x200B;更改为&#x200B;**所有文件**。

1. 在类中添加以下行：

   ```
   using namespace ADMS::Measurement;
   ```

1. 右键单击您的项目，然后选择&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**。

1. 浏览至`ADBMobileConfig.json`文件，然后单击&#x200B;**[!UICONTROL 添加]**。

1. 右键单击解决方案中的`ADBMobileConfig.json`文件，然后选择&#x200B;**[!UICONTROL 属性]**。

1. 在&#x200B;**[!UICONTROL 常规]**&#x200B;选项卡上，将&#x200B;**[!UICONTROL 内容]**&#x200B;更改为&#x200B;**[!UICONTROL 是]**，然后单击&#x200B;**[!UICONTROL 确定]**。

## 将库和配置文件添加到项目 — WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. 启动Visual Studio并打开您的解决方案。
1. 在&#x200B;**解决方案资源管理器**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

   有关详细信息，请参阅下面的&#x200B;*选择正确版本*&#x200B;部分。

1. 选择正确的库版本，然后浏览至关联的`ADBMobile.winmd`文件。

1. 单击&#x200B;**[!UICONTROL 添加]**。

1. 验证是否在&#x200B;**[!UICONTROL 引用管理器]**&#x200B;窗口中选中`ADBMobile.winmd`，然后单击&#x200B;**[!UICONTROL 确定]**。

   >[!TIP]
   >
   >添加对Windows Phone应用程序的引用时，要选择`ADBMobile.winmd`，请将默认文件过滤器从&#x200B;**[!UICONTROL 组件文件]**&#x200B;更改为&#x200B;**所有文件**。

1. 在&#x200B;**[!UICONTROL 解决方案资源管理器]**&#x200B;中，右键单击&#x200B;**[!UICONTROL 引用]**&#x200B;并选择&#x200B;**[!UICONTROL 添加引用]**。

   如果您的解决方案中还包含C++项目，请跳过此步骤。

1. 在左侧的&#x200B;**[!UICONTROL Windows]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL 扩展]**&#x200B;并选择和添加&#x200B;**[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**。

1. 右键单击您的项目，然后选择&#x200B;**[!UICONTROL 添加]** > **[!UICONTROL 现有项目]**。

1. 浏览至`ADBMobileConfig.json`文件，然后单击&#x200B;**[!UICONTROL 添加]**。

1. 右键单击解决方案中的`ADBMobileConfig.json]`文件，然后选择&#x200B;**[!UICONTROL 属性]**。

1. 选择&#x200B;**[!UICONTROL 文件属性]**&#x200B;后，确保将&#x200B;**[!UICONTROL 包操作]**&#x200B;设置为&#x200B;**[!UICONTROL 内容]**。

   对于JavaScript项目，默认情况下将文件设置为&#x200B;**[!UICONTROL Content]**。

## 更新ADBMobileConfig.json配置文件{#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

`ADBMobileConfig.json`文件包含全局SDK设置，在您完成&#x200B;*将库和配置文件添加到Project*&#x200B;部分中的步骤后，该文件位于您的项目根目录下。 如果您的`ADBMobileConfig.json`文件未由Adobe Mobile Services预配置，则需要更新一些值才能开始。

以下是`ADBMobileConfig.json`文件的示例：

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

* **分析**: `rsids` 和  `server`
* **Target**: `clientCode`
* **受众管理**:  `server`

有关详细信息，请参阅[ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md)。

## 调试 {#section_3A10376A60394A15BEE483323E0CD4AA}

当要启用SDK调试时，必须调用`ADBMobile.Config.setDebugLogging(true);`。

对于C Sharp和JS应用程序，您必须完成以下步骤（本机代码调试是C++应用程序的默认设置）以启用本机代码调试：

### C锐

右键单击项目，选择&#x200B;**[!UICONTROL 属性]** > **[!UICONTROL 调试选项卡]**。 在调试器下拉列表中，选择&#x200B;**[!UICONTROL 仅本机]**。

### JS

右键单击项目，选择&#x200B;**[!UICONTROL 属性]** > **[!UICONTROL 配置属性]** > **[!UICONTROL 调试选项卡]**。 将调试器类型下拉列表更改为&#x200B;**仅本机**。

操作完成！现在，您已准备好在Windows 8.1通用App Store应用程序中实施分析、目标和受众管理。
