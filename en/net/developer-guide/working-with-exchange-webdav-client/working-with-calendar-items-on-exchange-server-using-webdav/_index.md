---
title: Working with Calendar Items on Exchange Server using WebDav
type: docs
weight: 40
url: /net/working-with-calendar-items-on-exchange-server-using-webdav/
---


## **Sending Meeting Requests**
This article shows how to send a meeting request to multiple recipients using Microsoft Exchange Server and Aspose.Email.

1. Create a meeting request using the [Appointment](https://apireference.aspose.com/email/net/aspose.email.calendar/appointment) class and set the location, time and attendees.
1. Create an instance of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class and set the appointment using the [MailMessage.AddAlternateView()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/addalternateview) method.
1. Connect to the Exchange Server and send the meeting request using the Send(MailMessage) method.

This example uses the [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) class, which uses the [WebDAV](https://en.wikipedia.org/wiki/WebDAV) protocol to connect to the Exchange Server and can be used with any version of Exchange Server on which WebDAV is enabled, for example Exchange 2000, 2003 or 2007. The following code snippet shows you how to send the meeting request are given below.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendMeetingRequestsUsingExchangeServer-SendMeetingRequestsUsingExchangeServer.cs" >}}
