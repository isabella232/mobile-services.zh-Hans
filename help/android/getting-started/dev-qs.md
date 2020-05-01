---
description: 此信息可帮助您实施 Android 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。
keywords: android;library;mobile;sdk
seo-description: 此信息可帮助您实施 Android 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。
seo-title: 核心实施和生命周期
solution: Marketing Cloud,Analytics
title: 核心实施和生命周期
topic: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: tm+mt
source-git-commit: dae60a21286edc28c84b7638da214b824abf0cd3

---


# 核心实施和生命周期 {#core-implementation-and-lifecycle}

此信息可帮助您实施 Android 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。

## 下载 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>要下载 SDK，您必须使用 Android 2.2 或更高版本。

1. 完成以下各节中的步骤，以设置开发报告套件并下载配置文件的预填充版本：

   * [创建报表包](/help/android/getting-started/requirements.md)
   * [下载 SDK](/help/android/getting-started/requirements.md)

1. 下载并解压缩 `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` 文件，同时确认存在以下软件组件：

   * `adobeMobileLibrary.jar`，这是将用于 Android 设备和模拟器的库。

   * `ADBMobileConfig.json`，为您的应用程序自定义的 SDK 配置文件。
   >[!IMPORTANT]
   >
   >如果您在 Adobe Mobile Services 用户界面之外下载 SDK，则必须手动配置 `ADBMobileConfig.json` 文件。如果您是初次使用 Analytics 和 Mobile SDK，而且想要设置一个开发报表包并下载预填充版本的配置文件，请参阅[开始之前](/help/android/getting-started/requirements.md)。

## 将 SDK 和配置文件添加到您的 IntelliJ IDEA 或 Eclipse 项目 {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA 项目**

要将 SDK 和配置文件添加到您的项目，请执行以下操作：

1. 将 `ADBMobileConfig.json` 文件添加到您项目的 `assets` 文件夹中。

1. 在项目导航面板中，右键单击您的项目。
1. 选择&#x200B;**[!UICONTROL 打开模块设置]**。
1. 在&#x200B;**[!UICONTROL 项目设置]**&#x200B;下，选择&#x200B;**[!UICONTROL 库]**。
1. Click the **[!UICONTROL +]** icon to add a new library.
1. 选择 **[!UICONTROL Java]** 并导航至 `adobeMobileLibrary.jar` 文件。
1. 选择您计划在其中使用移动设备库的模块。
1. 单击&#x200B;**[!UICONTROL 应用]**，然后单击&#x200B;**[!UICONTROL 确定]**&#x200B;以关闭“模块设置”窗口。

**Eclipse 项目**

要将 SDK 和配置文件添加到您的项目，请执行以下操作：

1. 将 `ADBMobileConfig.json` 文件添加到您项目的 `assets` 文件夹中。
1. 在 **[!UICONTROL Eclipse IDE]** 中，右键单击项目名称。
1. Click  **[!UICONTROL Build Path]** > **[!UICONTROL Add External Archives]**.
1. 选择 `adobeMobileLibrary.jar`。
1. 单击&#x200B;**[!UICONTROL 打开]**。
1. Right-click the project again and select **[!UICONTROL Build Path]** > **[!UICONTROL Configure Build Path]**.
1. 在&#x200B;**[!UICONTROL 顺序和导出]**&#x200B;选项卡中，确保已选中 **`adobeMobileLibrary.jar`**。

## 添加应用程序权限 {#section_2EAF73ABF6424647B219A63B33B02CD5}

AppMeasurement 库需要以下权限来发送数据和记录离线跟踪调用：

* `INTERNET`
* `ACCESS_NETWORK_STATE`

要添加这些权限，请将以下行添加到 `AndroidManifest.xml` 文件中，该文件位于应用程序项目目录内：

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## 设置应用程序上下文 {#set-application-context}

应在主活动的 `onCreate` 方法中添加以下代码：

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
```

## 实施生命周期量度 {#section_BA686C09021F474AADDE8690BBB910F7}

启用生命周期后，每次启动您的应用程序时，系统都会发送一个点击来测量启动次数、升级次数、会话数、参与用户数等量度。有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

**在应用程序的每个活动中完成以下步骤：**

1. 导入库：

   ```java
   import com.adobe.mobile.*;
   ```

1. 在 `onResume` 函数中，启动生命周期数据收集：

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. 在 `onPause` 函数中，暂停生命周期数据收集：

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>您必须将这些调用添加到每个活动中，才能确保准确报告崩溃情况。有关更多信息，请参阅[跟踪应用程序的崩溃情况](/help/android/analytics-main/crashes.md)。

## 通过生命周期调用包含其他数据

要通过生命周期量度调用包含其他数据，请将一个额外的参数传递到包含上下文数据的 `collectLifecycleData`：

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

通过 `collectLifecycleData` 发送的其他上下文数据值必须映射到 Adobe Mobile Services 中的自定义变量：

![](assets/map-variable-lifecycle.png)

其他生命周期量度将会自动收集。有关更多信息，请参阅[生命周期量度](/help/android/metrics.md)。

## 后续操作 {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

完成以下任务：

* [跟踪应用程序状态](/help/android/analytics-main/states.md)
* [跟踪应用程序操作](/help/android/analytics-main/actions.md)

