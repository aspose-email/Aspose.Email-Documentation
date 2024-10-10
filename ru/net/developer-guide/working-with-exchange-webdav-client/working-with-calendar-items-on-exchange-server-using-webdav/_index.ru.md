---
title: "Работа с элементами календаря на Exchange Server с использованием WebDav"
url: /ru/net/working-with-calendar-items-on-exchange-server-using-webdav/
weight: 40
type: docs
---


## **Отправка запросов на встречу**
В этой статье показано, как отправить запрос на встречу нескольким получателям с использованием Microsoft Exchange Server и Aspose.Email.

1. Создайте запрос на встречу с помощью класса [Appointment](https://apireference.aspose.com/email/net/aspose.email.calendar/appointment) и установите место, время и участников.
1. Создайте экземпляр класса [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) и установите встречу с помощью метода [MailMessage.AddAlternateView()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/addalternateview).
1. Подключитесь к Exchange Server и отправьте запрос на встречу с помощью метода Send(MailMessage).

В этом примере используется класс [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient), который использует протокол [WebDAV](https://en.wikipedia.org/wiki/WebDAV) для подключения к Exchange Server и может использоваться с любой версией Exchange Server, на которой включен WebDAV, например, Exchange 2000, 2003 или 2007. Следующий фрагмент кода показывает, как отправить запрос на встречу, приведенный ниже.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendMeetingRequestsUsingExchangeServer-SendMeetingRequestsUsingExchangeServer.cs" >}}