---
description: 您可以将应用程序配置为使用Apple Push Notification Service(APNS)或Firebase Cloud Messaging(FCM)。
keywords: mobile
seo-description: 您可以将应用程序配置为使用Apple Push Notification Service(APNS)或Firebase Cloud Messaging(FCM)。
seo-title: 将应用程序配置为使用APNS或FCM
solution: Marketing Cloud，Analytics
title: 将应用程序配置为使用APNS或FCM
topic: 量度
uuid: fa411f2a-ba47-4499-bbe5-1aedef6 b49 ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# 将应用程序配置为使用APNS或FCM{#configure-app-to-use-apns-or-fcm}

您可以将应用程序配置为使用Apple Push Notification Service(APNS)或Firebase Cloud Messaging(FCM)。

## Android 应用程序 {#section_41D304102CDF4586911EC1413AD35A10}

### 如果应用程序中未启用FCM

要将Android应用程序配置为在此场景中使用FCM，请执行以下操作：

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 单击 **[!UICONTROL “快速入门]** ”，然后选择 **[!UICONTROL “添加项目]**”。

1. 输入项目名称，如果选择在Google Analytics中加入Firebase数据，请单击接受控制器控制器条款的复选框。

1. 单击 **[!UICONTROL 创建项目]** ，然后等待创建项目。

1. 单击创建的项目并显示创建项目的“ **[!UICONTROL 项目概述]** ”页面。单击带有Android图标的按钮可将Android应用程序添加到项目。

1. 根据需要输入应用程序包名称、应用程序别名和签名证书。

1. 按照设置向导建议的其他步骤操作。通过测试与Firebase服务器的通信验证Firebase设置后，返回 **[!UICONTROL 到“项目概述]** ”页面。

1. 单击 **[!UICONTROL “项目概述”]** 按钮右侧的齿轮图标，然后单击 **[!UICONTROL “项目设置]**”。

1. 单击 **[!UICONTROL 云消息]** 选项卡。

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   例如：

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 如果在应用程序中启用FCM

要将Android应用程序配置为在此场景中使用FCM，请执行以下操作：

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. 单击 **[!UICONTROL “开始”]**。这将打开项目索引页面。找到已启用Firebase的项目，该项目链接到您的Android应用程序并单击项目卡。

1. 随后应加载项目的 **** 项目概述。单击 **[!UICONTROL “项目概述”]** 按钮右侧的齿轮图标，然后单击 **[!UICONTROL “项目设置]**”。

1. 单击 **[!UICONTROL 云消息]** 选项卡。

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
1. 如果已设置要推送的App ID，请转到步骤11。
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

   单击的按钮取决于您正在创建“开发”或“生产”证书。
1. 按照以下步骤在Apple的网站上创建CSR，上传CSR并生成证书。
1. 向下滚动至&#x200B;**[!UICONTROL 推送通知]**&#x200B;部分，下载刚刚创建的 SSL 证书。
1. 双击下载的证书，将其添加到密钥链。

### SSL证书和私钥

获取SSL证书和私钥(APNS)：

1. 打开&#x200B;**[!UICONTROL 密钥链访问]**。
1. Click **[!UICONTROL My Certificates]** and find the appropriate **[!UICONTROL iOS Push Services Certificate]** for your app and environment.

   您可以通过匹配捆绑 ID 以及它是开发用证书还是生产用证书来识别正确的证书。

1. 展开证书，确认其中包含私钥。
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. 在对话框中键入必要信息并保存新 `.p12` 文件。

   您不必键入密码。

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

