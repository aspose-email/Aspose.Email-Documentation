---
title: "Отправка запросов на встречу с использованием Exchange Server через WebDav"
url: /ru/java/sending-meeting-requests-with-exchange-server-using-webdav/
weight: 110
type: docs
---

{{% alert color="primary" %}} 

В этой статье описывается, как отправить запрос на встречу нескольким получателям с помощью Microsoft Exchange Server и Aspose.Email. Также объясняется, как настроить код для работы с Exchange Web Services.

{{% /alert %}} 
## **Отправка запросов на встречу с использованием Web Dav**
Чтобы отправить запрос на встречу:

1. Создайте запрос на встречу, используя класс [Appointment](https://apireference.aspose.com/java/email/com.aspose.email/appointment), и установите местоположение, время и участников.
1. Создайте экземпляр класса [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) и установите встречу, используя метод [MailMessage.addAlternateView()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#addAlternateView\(com.aspose.email.AlternateView\)).
1. Подключитесь к Exchange Server и отправьте запрос на встречу, используя метод [send(MailMessage)](https://apireference.aspose.com/java/email/com.aspose.email/ExchangeClient#send\(com.aspose.email.MailMessage\)).

В этом примере используется класс [ExchangeClient](https://apireference.aspose.com/java/email/com.aspose.email/exchangeclient), который использует протокол [WebDAV](http://en.wikipedia.org/wiki/WebDAV) для подключения к Exchange Server и может быть использован с любой версией Exchange Server, на которой включен WebDAV, например, Exchange 2000, 2003 или 2007.

Приведены кодовые фрагменты, используемые для отправки запроса на встречу:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendMeetingRequestsUsingExchangeServer-SendingMeetingRequestsUsingAnExchangeServerWebDav.java" >}}