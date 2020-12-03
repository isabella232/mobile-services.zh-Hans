---
description: 可以将图像文件附加到Apple通知。 添加可视组件可以显着提高用户对推送通知的参与度。
seo-description: 可以将图像文件附加到Apple通知。 添加可视组件可以显着提高用户对推送通知的参与度。
seo-title: 接收富推送通知
title: 接收富推送通知
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 29%

---


# 接收富推送通知 {#receive-rich-push-notifications}

可以将图像文件附加到Apple通知。 添加可视组件可以显着提高用户对推送通知的参与度。

要在iOS应用程序中接收富推送通知，请执行以下操作：

1. 通过完成推送消息中的步骤，为应用程序实 [施推送消息](/help/ios/messaging-main/push-messaging/push-messaging.md)。
1. 验证是否可以向应用程序发送文本推送消息。
1. 通过完成以下步骤添加通知服务扩展：

   1. In your Xcode project, select  **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]**.
   1. 选择&#x200B;**[!UICONTROL 通知服务扩展]**。
   1. 确认存在 `NotificationService.m` 文件。

1. 打开 `NotificationService.m` 文件，并确认存在以下委托方法：

   * 一种接收通知请求的方法。
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


For more information about rich push notifications with iOS, see [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
