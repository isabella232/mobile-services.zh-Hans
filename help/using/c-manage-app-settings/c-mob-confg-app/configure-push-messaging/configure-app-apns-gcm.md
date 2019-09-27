---
description: You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: 您可以将应用程序配置为使用Apple推送通知服务(APNS)或Firebase Cloud Messaging(FCM)。
seo-title: 将应用程序配置为使用APNS或FCM
solution: Marketing Cloud,Analytics
title: 将应用程序配置为使用APNS或FCM
topic: 量度
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# 将应用程序配置为使用APNS或FCM{#configure-app-to-use-apns-or-fcm}

您可以将应用程序配置为使用Apple推送通知服务(APNS)或Firebase Cloud Messaging(FCM)。

## Android 应用程序 {#section_41D304102CDF4586911EC1413AD35A10}

### 如果您的应用程序中未启用FCM

要在此场景中配置Android应用程序以使用FCM，请执行以下操作：

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 单击“ **[!UICONTROL 开始]** ”，然后选择 **[!UICONTROL “添加项目”]**。

1. 输入项目名称，如果选择使用Google Analytics获取Firebase数据，请单击接受控制器与控制器条款的复选框。

1. 单击 **[!UICONTROL 创建项目]** ，然后等待项目创建。

1. Click on the created project and the Project Overview page for the created project should be shown. ****&#x200B;单击带有Android图标的按钮，将Android应用程序添加到项目。

1. Enter the app package name, app nickname, and signing certificate if needed.

1. Follow the additional steps suggested by the setup wizard. After verifying the Firebase setup by testing communication with the Firebase servers, return to the Project Overview page.****

1. 单击“项目概述”按钮右侧的齿轮图 **[!UICONTROL 标]** ，然后单击“项 **[!UICONTROL 目设置”]**。

1. Click the Cloud Messaging tab.****

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   例如：

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 如果您的应用程序中启用了FCM

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 单击 **[!UICONTROL 开始]**。 This will open the project index page. 查找已启用Firebase的项目，该项目链接到您的Android应用程序，然后单击项目卡。

1. The Project Overview for the project should then be loaded. ****&#x200B;单击“项目概述”按钮右侧的齿轮图 **[!UICONTROL 标]** ，然后单击“项 **[!UICONTROL 目设置”]**。

1. Click the Cloud Messaging tab.****

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   例如：

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

要将您的 iOS 应用程序配置为使用 APNS，请执行以下操作：

1. 转到 [https://developer.apple.com/account](https://developer.apple.com/account) 并登录到您的 [Apple Developer 帐户](https://developer.apple.com/account)。
1. Under **[!UICONTROL iOS Apps]**, select **[!UICONTROL Identifiers]**.
1. 如果您为推送设置了应用程序ID，请转到步骤11。
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. 键入“应用程序 ID 描述”。
1. 键入“应用程序 ID 后缀”。

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. 在&#x200B;**[!UICONTROL 应用程序服务]**&#x200B;下，选中&#x200B;**[!UICONTROL 推送通知]**&#x200B;复选框。
1. Click **[!UICONTROL Continue]**.
1. Click **[!UICONTROL Submit]**.
1. 单击&#x200B;**[!UICONTROL 完成]**。
1. 从列表中选择设置为使用推送消息的应用程序 ID，然后单击&#x200B;**[!UICONTROL 编辑]**。
1. 如果已经创建推送证书，请跳转至步骤 15。
1. 向下滚动至&#x200B;**[!UICONTROL 推送通知]**，然后单击正确的&#x200B;**[!UICONTROL 创建证书…]**&#x200B;按钮。

   The button you click depends whether you are creating a certificate for Development or Production.
1. 按照以下步骤操作，在Apple网站上创建CSR、上传CSR并生成证书。
1. 向下滚动至&#x200B;**[!UICONTROL 推送通知]**&#x200B;部分，下载刚刚创建的 SSL 证书。
1. 双击下载的证书以将其添加到密钥链中。

### SSL证书和私钥

要获取SSL证书和私钥(APNS)，请执行以下操作：

1. 打开&#x200B;**[!UICONTROL 密钥链访问]**。
1. Click **[!UICONTROL My Certificates]** and find the appropriate **[!UICONTROL iOS Push Services Certificate]** for your app and environment.

   您可以通过匹配捆绑 ID 以及它是开发用证书还是生产用证书来识别正确的证书。

1. 展开证书，确认其中包含私钥。
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. Type the necessary information in the dialog box and save your new  file.`.p12`

   您不必键入密码。

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

