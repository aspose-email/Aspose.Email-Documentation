---
title: Setting Default Text Encoding in Email Message
ArticleTitle: Setting Default Text Encoding in Email Message
type: docs
weight: 120
url: /net/setting-default-text-encoding-in-email-message/
---


This article introduces the [MailMessage.PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) property and explains how it is used. Using this property, you can set the default text encoding for the following properties:

- From: Display name
- To: Display name
- Subject
- Body
## **Setting Default Text Encoding**
In previous versions of Aspose.Email, text encoding for the from, to, subject and body properties were set separately. To improve usability, we added the [PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) property which sets all at once. It's now easier to ensure that all the text in the above properties is encoded properly in the email message. The following code snippet shows you how to use a French word as the display name for email addresses, subject and body.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-SetDefaultTextEncoding-SetDefaultTextEncoding.cs" >}}
