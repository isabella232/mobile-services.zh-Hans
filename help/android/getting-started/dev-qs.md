---
description: 此信息可帮助您实施 Android 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。
keywords: android；库；移动；sdk
seo-description: 此信息可帮助您实施 Android 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。
seo-title: 核心实施和生命周期
solution: Marketing Cloud，Analytics
title: 核心实施和生命周期
topic: 开发人员和实施
uuid: af4d11ac-8245-46a0-9b3a-4a29cfbbbb2
translation-type: tm+mt
source-git-commit: c4da3599c858bfbccb7af954df75f94eb7d8e99a

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

此信息可帮助您实施 Android 库并收集生命周期量度，例如启动次数、升级次数、会话数、参与用户数等。

## 下载 SDK {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>要下载SDK，您必须使用Android2.2或更高版本。

1. 请完成以下部分中的步骤，以设置一个开发报表包并下载预填充版本的配置文件：

   * [创建报表包](/help/android/getting-started/requirements.md)
   * [下载 SDK](/help/android/getting-started/requirements.md)

1. 下载并解压缩文件 `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` 并验证存在以下软件组件：

   * `adobeMobileLibrary.jar`这是将与Android设备和模拟器一起使用的库。

   * `ADBMobileConfig.json`，为您的应用程序自定义的 SDK 配置文件。
   >[!IMPORTANT]
   >
   >If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, and you want to set up a development report suite and download a pre-populated version of the configuration file, see [Before You Start](/help/android/getting-started/requirements.md).

## Add the SDK and config file to your IntelliJ IDEA or Eclipse project {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA项目**

要将 SDK 和配置文件添加到您的项目，请执行以下操作：

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.

1. 在项目导航面板中，右键单击您的项目。
1. Select **[!UICONTROL Open Module Settings]**.
1. Under **[!UICONTROL Project Settings]**, select **[!UICONTROL Libraries]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. 选择 **[!UICONTROL Java]** 并导航至 `adobeMobileLibrary.jar` 文件。
1. 选择您计划在其中使用移动设备库的模块。
1. 单击&#x200B;**[!UICONTROL 应用]**，然后单击&#x200B;**[!UICONTROL 确定]以关闭模块设置窗口。**

**Eclipse项目**

要将 SDK 和配置文件添加到您的项目，请执行以下操作：

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.
1. In **[!UICONTROL Eclipse IDE]**, right-click the project name.
1. Click  **[!UICONTROL Build Path]** &gt; **[!UICONTROL Add External Archives]**.
1. 选择 `adobeMobileLibrary.jar`.
1. Click **[!UICONTROL Open]**.
1. Right-click the project again and select **[!UICONTROL Build Path]** &gt; **[!UICONTROL Configure Build Path]**.
1. 在&#x200B;**[!UICONTROL 顺序和导出]**&#x200B;选项卡中，确保已选中 **`adobeMobileLibrary.jar`。**

## Add app permissions {#section_2EAF73ABF6424647B219A63B33B02CD5}

AppMeasurement 库需要以下权限来发送数据和记录离线跟踪调用：

* `INTERNET`
* `ACCESS_NETWORK_STATE`

要添加这些权限，请将以下行添加到 `AndroidManifest.xml` 文件中，该文件位于应用程序项目目录内：

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Set the application context {#set-application-context}

应在主活动的 `onCreate` 方法中添加以下代码：

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
````

## Implement lifecycle metrics {#section_BA686C09021F474AADDE8690BBB910F7}

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
>您必须将这些调用添加到每个活动，以确保准确的崩溃报告。有关更多信息，请参阅 [跟踪应用程序崩溃](/help/android/analytics-main/crashes.md)。

## 包含具有生命周期调用的其他数据

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

