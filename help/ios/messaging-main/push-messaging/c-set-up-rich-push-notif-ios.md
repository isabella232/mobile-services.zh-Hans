---
description: 您可以将图像文件附加到 Apple 通知。添加可视组件能够显著提高推送通知带来的用户参与度。
seo-description: 您可以将图像文件附加到 Apple 通知。添加可视组件能够显著提高推送通知带来的用户参与度。
seo-title: 接收富推送通知
title: 接收富推送通知
uuid: 0dbda409-cf49-4eb8-90ee-baf27911 dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

您可以将图像文件附加到 Apple 通知。添加可视组件能够显著提高推送通知带来的用户参与度。

要在 iOS 应用程序中接收富推送通知，请执行以下操作：

1. 完成 [推送消息](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. 确认您可以向应用程序发送文本推送消息。
1. 完成以下步骤来添加通知服务扩展：

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. Select **[!UICONTROL Notification Service Extension]**.
   1. 确认存在 `NotificationService.m` 文件。

1. 打开 `NotificationService.m` 文件，并确认存在以下委托方法：

   * 一个用于接收通知请求的方法。
   * 一个用于处理服务扩展过期的方法。

      要接收富推送通知，请使用第一个方法：

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      在此方法中，您可以通过使用 `userInfo``attachment-url` 密钥获取媒体URL。将文件下载到本地目录后，添加本地路径 `bestAttemptContent.attachments`。

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


有关 iOS 富推送通知的更多信息，请参阅 [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment)。
