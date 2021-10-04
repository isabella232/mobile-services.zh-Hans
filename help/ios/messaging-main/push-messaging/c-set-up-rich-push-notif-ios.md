---
description: 您可以将图像文件附加到Apple通知。 添加可视化组件可以显着提高推送通知用户的参与度。
title: 接收富推送通知
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
exl-id: 1167ae4b-04ad-4c0d-a9db-67d30693f697
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 33%

---

# 接收富推送通知 {#receive-rich-push-notifications}

您可以将图像文件附加到Apple通知。 添加可视化组件可以显着提高推送通知用户的参与度。

要在iOS应用程序中接收富推送通知，请执行以下操作：

1. 通过完成[推送消息](/help/ios/messaging-main/push-messaging/push-messaging.md)中的步骤，为应用程序实施推送消息。
1. 确认您可以向应用程序发送文本推送消息。
1. 通过完成以下步骤添加通知服务扩展：

   1. 在您的Xcode项目中，选择&#x200B;**[!UICONTROL 文件]** > **[!UICONTROL 新建]** > **[!UICONTROL 目标]**。
   1. 选择&#x200B;**[!UICONTROL 通知服务扩展]**。
   1. 确认存在 `NotificationService.m` 文件。

1. 打开 `NotificationService.m` 文件，并确认存在以下委托方法：

   * 接收通知请求的一种方法。
   * 一种处理服务扩展到期的方法。

      要接收富推送通知，请使用第一种方法：

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      在此方法中，您可以使用 `attachment-url` 键从 `userInfo` 获取媒体 URL。将文件下载到本地目录后，将本地路径添加到 `bestAttemptContent.attachments`。

      以下是此方法中的代码示例：

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


有关iOS富推送通知的更多信息，请参阅[UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment)。
