---
description: "Automatically generated file. DO NOT MODIFY"
---

```objc

MSHTTPClient *httpClient = [MSClientFactory createHTTPClientWithAuthenticationProvider:authenticationProvider];

NSString *MSGraphBaseURL = @"https://graph.microsoft.com/v1.0/";
NSMutableURLRequest *urlRequest = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:[MSGraphBaseURL stringByAppendingString:@"/teams/57fb72d0-d811-46f4-8947-305e6072eaa5/channels/19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2/messages"]]];
[urlRequest setHTTPMethod:@"POST"];
[urlRequest setValue:@"application/json" forHTTPHeaderField:@"Content-Type"];

MSGraphChatMessage *chatMessage = [[MSGraphChatMessage alloc] init];
MSGraphItemBody *body = [[MSGraphItemBody alloc] init];
[body setContentType: [MSGraphBodyType html]];
[body setContent:@"Here's the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>"];
[chatMessage setBody:body];
NSMutableArray *attachmentsList = [[NSMutableArray alloc] init];
MSGraphChatMessageAttachment *attachments = [[MSGraphChatMessageAttachment alloc] init];
[attachments setId:@"153fa47d-18c9-4179-be08-9879815a9f90"];
[attachments setContentType:@"reference"];
[attachments setContentUrl:@"https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx"];
[attachments setName:@"Budget.docx"];
[attachmentsList addObject: attachments];
[chatMessage setAttachments:attachmentsList];

NSError *error;
NSData *chatMessageData = [chatMessage getSerializedDataWithError:&error];
[urlRequest setHTTPBody:chatMessageData];

MSURLSessionDataTask *meDataTask = [httpClient dataTaskWithRequest:urlRequest 
	completionHandler: ^(NSData *data, NSURLResponse *response, NSError *nserror) {

		//Request Completed

}];

[meDataTask execute];

```