---
title: Send Email Message using Exchange Server with WebDav
ArticleTitle: Send Email Message using Exchange Server with WebDav
type: docs
weight: 100
url: /java/send-email-message-using-exchange-server-with-webdav/
---

You can send email messages using an Exchange Server with the help of the tools in com.aspose.email. The [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) method accepts a [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) instance as a parameter and sends the email. This article explains how to send email messages using an Exchange Client of the API.
## **Send Email Messages Using Exchange WebDav**
To send emails using an Exchange Server:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Specify server name, username, password, and domain.
1. Create an instance of the [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) class.
1. Specify the from, to, subject and other [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) properties.
1. Call the [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) method to send the email.

The sample code below sends email messages using Exchange Server.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendEmailMessageUsingExchangeServer-SendEmailMessageUsingExchangeServer.java" >}}
