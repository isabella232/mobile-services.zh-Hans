---
description: 您可以将应用程序配置为使用 Apple 推送通知服务 (APNS) 或 Firebase Cloud Messaging (FCM)。
keywords: mobile
seo-description: 您可以将应用程序配置为使用 Apple 推送通知服务 (APNS) 或 Firebase Cloud Messaging (FCM)。
seo-title: 配置应用程序以使用 APNS 或 FCM
solution: Experience Cloud,Analytics
title: 配置应用程序以使用 APNS 或 FCM
topic: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '652'
ht-degree: 100%

---


# 配置应用程序以使用 APNS 或 FCM{#configure-app-to-use-apns-or-fcm}

您可以将应用程序配置为使用 Apple 推送通知服务 (APNS) 或 Firebase Cloud Messaging (FCM)。

## Android 应用程序 {#section_41D304102CDF4586911EC1413AD35A10}

### 如果您的应用程序未启用 FCM

要在这种情形下将您的 Android 应用程序配置为使用 FCM，请执行以下操作：

1. 请转到 [https://firebase.google.com/](https://firebase.google.com/)，然后使用您的 Google Dev 凭据登录。

1. 单击&#x200B;**[!UICONTROL 开始]**，然后选择&#x200B;**[!UICONTROL 添加项目]**。

1. 输入项目名称，如果选择启用 Google Analytics for Firebase 数据，请单击相应的复选框以接受控制方-控制方条款。

1. 单击&#x200B;**[!UICONTROL 创建项目]**，然后等待项目创建完毕。

1. 单击已创建的项目，此时应会显示该已创建项目的&#x200B;**[!UICONTROL 项目概述]**&#x200B;页面。单击带有 Android 图标的按钮，以将 Android 应用程序添加到项目。

1. 根据需要，输入应用程序包名称、应用程序昵称和签名证书。

1. 执行安装向导建议的其他步骤。通过测试与 Firebase 服务器的通信来验证 Firebase 设置后，返回到&#x200B;**[!UICONTROL 项目概述]**&#x200B;页面。

1. 单击&#x200B;**[!UICONTROL 项目概述]**&#x200B;按钮右侧的齿轮图标，然后单击&#x200B;**[!UICONTROL 项目设置]**。

1. 单击 **[!UICONTROL Cloud Messaging]** 选项卡。

1. 复制&#x200B;**[!UICONTROL 旧版服务器密钥]**&#x200B;和&#x200B;**[!UICONTROL 发送者 ID]** 以供将来使用。

   例如：

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### 如果您的应用程序已启用 FCM

要在这种情形下将您的 Android 应用程序配置为使用 FCM，请执行以下操作：

1. 请转到 [https://firebase.google.com/](https://firebase.google.com/)，然后使用您的 Google Dev 凭据登录。

1. 单击&#x200B;**[!UICONTROL 开始]**。这将打开项目索引页面。查找已启用 Firebase 且已链接到您的 Android 应用程序的项目，然后单击该项目信息卡。

1. 随后应会加载该项目的&#x200B;**[!UICONTROL 项目概述]**。单击&#x200B;**[!UICONTROL 项目概述]**&#x200B;按钮右侧的齿轮图标，然后单击&#x200B;**[!UICONTROL 项目设置]**。

1. 单击 **[!UICONTROL Cloud Messaging]** 选项卡。

1. 复制&#x200B;**[!UICONTROL 旧版服务器密钥]**&#x200B;和&#x200B;**[!UICONTROL 发送者 ID]** 以供将来使用。

   例如：

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS 应用程序 {#section_2031DAB485FC4D2B9027E42AD90B294D}

要将您的 iOS 应用程序配置为使用 APNS，请执行以下操作：

1. 转到 [https://developer.apple.com/account](https://developer.apple.com/account)，然后登录到您的 [Apple Developer 帐户](https://developer.apple.com/account)。
1. 在 **[!UICONTROL iOS 应用程序]**&#x200B;下，选择&#x200B;**[!UICONTROL 标识符]**。
1. 如果已设置用于推送的应用程序 ID，请转到步骤 11。
1. 按 **[!UICONTROL +]** 按钮以创建新的应用程序 ID。
1. 键入应用程序 ID 说明。
1. 键入应用程序 ID 后缀。

   >[!IMPORTANT]
   >
   >要支持推送，您必须使用&#x200B;**未**&#x200B;使用通配符的显式应用程序 ID（例如，`- com.tester.pushSample`）。

1. 在&#x200B;**[!UICONTROL 应用程序服务]**&#x200B;下，选中&#x200B;**[!UICONTROL 推送通知]**&#x200B;复选框。
1. 单击&#x200B;**[!UICONTROL 继续]**。
1. 单击&#x200B;**[!UICONTROL 提交]**。
1. 单击&#x200B;**[!UICONTROL 完成]**。
1. 从列表中选择设置为使用推送消息的应用程序 ID，然后单击&#x200B;**[!UICONTROL 编辑]**。
1. 如果已经创建推送证书，请跳转至步骤 15。
1. 向下滚动至&#x200B;**[!UICONTROL 推送通知]**，然后单击正确的&#x200B;**[!UICONTROL 创建证书...]** 按钮。

   单击的按钮取决于您是创建用于开发还是用于生产的证书。
1. 按照有关如何在 Apple 网站上创建 CSR、上传 CSR 并生成证书的步骤执行操作。
1. 向下滚动至&#x200B;**[!UICONTROL 推送通知]**&#x200B;部分，下载刚刚创建的 SSL 证书。
1. 双击下载的证书，将其添加到您的密钥链。

### SSL 证书和私钥

要获取您的 SSL 证书和私钥 (APNS)，请执行以下操作：

1. 打开&#x200B;**[!UICONTROL 密钥链访问]**。
1. 单击&#x200B;**[!UICONTROL 我的证书]**，找到适用于您的应用程序和环境的 **[!UICONTROL iOS 推送服务证书]**。

   您可以通过匹配捆绑 ID 来识别正确的证书，并确定它是处于“开发”还是“生产”状态。

1. 展开证书并验证其是否包含私钥。
1. 右键单击私钥并选择&#x200B;**[!UICONTROL 导出&#x200B;*`<name of key>`*]**。
1. 在对话框中键入必需的信息，然后保存新的 `.p12` 文件。

   您不必键入密码。

1. 在&#x200B;**[!UICONTROL 私钥]**&#x200B;中，键入 `.p12` 文件。

