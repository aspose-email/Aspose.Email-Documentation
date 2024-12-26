---
title: Sending Meeting Requests with Exchange Server using WebDav
ArticleTitle: Sending Meeting Requests with Exchange Server using WebDav
type: docs
weight: 110
url: /java/sending-meeting-requests-with-exchange-server-using-webdav/
---

{{% alert color="primary" %}} 

This article shows how to send a meeting request to multiple recipients using Microsoft Exchange Server and Aspose.Email. It also explains how to adjust the code to work with Exchange Web Services.

{{% /alert %}} 
## **Send Meeting Requests using Web Dav**
To send a meeting request:

1. Create a meeting request using the [Appointment](https://apireference.aspose.com/java/email/com.aspose.email/appointment) class and set the location, time and attendees.
1. Create an instance of the [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) class and set the appointment using the [MailMessage.addAlternateView()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#addAlternateView\(com.aspose.email.AlternateView\)) method.
1. Connect to the Exchange Server and send the meeting request using the [send(MailMessage)](https://apireference.aspose.com/java/email/com.aspose.email/ExchangeClient#send\(com.aspose.email.MailMessage\)) method.

This example uses the [ExchangeClient](https://apireference.aspose.com/java/email/com.aspose.email/exchangeclient) class, which uses the [WebDAV](http://en.wikipedia.org/wiki/WebDAV) protocol to connect to the Exchange Server and can be used with any version of Exchange Server on which WebDAV is enabled, for example, Exchange 2000, 2003 or 2007.

The code snippets used to send the meeting request are given below:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendMeetingRequestsUsingExchangeServer-SendingMeetingRequestsUsingAnExchangeServerWebDav.java" >}}
