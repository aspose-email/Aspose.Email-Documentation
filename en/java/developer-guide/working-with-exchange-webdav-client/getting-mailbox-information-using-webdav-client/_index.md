---
title: Getting Mailbox Information using WebDav Client
ArticleTitle: Getting Mailbox Information using WebDav Client
type: docs
weight: 50
url: /java/getting-mailbox-information-using-webdav-client/
---

{{% alert color="primary" %}} 

The [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class has members that can be used to get mailbox information from an Exchange Server by calling the [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) method. It returns an instance of type [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo). Get mailbox information from properties such as [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getInboxUri\(\)) , and [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getDraftsUri\(\)).

This article shows how to access mailbox information directly from an Exchange Server.

{{% /alert %}} 
## **Get Mailbox Information from an Exchange Server**
To get the Exchange Mailbox information:

1. Create an instance of the [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) class.
1. Specify the Exchange Server, username, password and domain in the ExchangeClient constructor.
1. Call the [ExchangeClient.getMailboxSize()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxSize\(\)) method to get mailbox size.
1. Call the [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) method to get an instance of the [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) class.
1. Get the mailbox information using the [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo) class' different properties.

The sample codes below get Exchange mailbox information.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromAnExchangeServer.java" >}}
