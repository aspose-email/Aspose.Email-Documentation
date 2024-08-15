---
title: "Работа с элементами календаря на сервере Exchange с помощью WebDAV"
url: /ru/net/working-with-calendar-items-on-exchange-server-using-webdav/
weight: 40
type: docs
---


## **Отправка приглашений на собрание**
В этой статье показано, как отправить приглашение на собрание нескольким получателям с помощью Microsoft Exchange Server и Aspose.Email.

1. Создайте приглашение на собрание, используя [Appointment](https://apireference.aspose.com/email/net/aspose.email.calendar/appointment) класс и определите место, время и участников.
1. Создайте экземпляр [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) класс и назначьте встречу, используя [MailMessage.AddAlternateView()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/addalternateview) method.
1. Подключитесь к серверу Exchange и отправьте приглашение на собрание с помощью метода Send (MailMessage).

В этом примере используется [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) класс, в котором используется [WebDAV](https://en.wikipedia.org/wiki/WebDAV) протокол для подключения к серверу Exchange, который можно использовать с любой версией Exchange Server, на которой включен WebDAV, например Exchange 2000, 2003 или 2007. В следующем фрагменте кода показано, как отправить приглашение на собрание, приведено ниже.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendMeetingRequestsUsingExchangeServer-SendMeetingRequestsUsingExchangeServer.cs" >}}
