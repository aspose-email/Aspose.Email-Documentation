---
title: "Отправка приглашений на собрание с помощью Exchange Server с помощью WebDAV"
url: /ru/java/sending-meeting-requests-with-exchange-server-using-webdav/
weight: 110
type: docs
---

{{% alert color="primary" %}}

В этой статье показано, как отправить приглашение на собрание нескольким получателям с помощью Microsoft Exchange Server и Aspose.Email. В ней также объясняется, как настроить код для работы с веб-службами Exchange.

{{% /alert %}}
## **Отправка приглашений на собрание с помощью Web Dav**
Чтобы отправить запрос на встречу, выполните следующие действия:

1. Создайте приглашение на собрание, используя [Appointment](https://apireference.aspose.com/java/email/com.aspose.email/appointment) класс и определите место, время и участников.
1. Создайте экземпляр [MailMessage](https://apireference.aspose.com/java/email/com.aspose.email/mailmessage) класс и назначьте встречу, используя [MailMessage.addAlternateView()](https://apireference.aspose.com/java/email/com.aspose.email/MailMessage#addAlternateView\(com.aspose.email.AlternateView\)) method.
1. Подключитесь к серверу Exchange и отправьте приглашение на собрание, используя [send(MailMessage)](https://apireference.aspose.com/java/email/com.aspose.email/ExchangeClient#send\(com.aspose.email.MailMessage\)) method.

В этом примере используется [ExchangeClient](https://apireference.aspose.com/java/email/com.aspose.email/exchangeclient) класс, в котором используется [WebDAV](http://en.wikipedia.org/wiki/WebDAV) протокол для подключения к серверу Exchange, который можно использовать с любой версией Exchange Server, на которой включен WebDAV, например Exchange 2000, 2003 или 2007.

Фрагменты кода, использованные для отправки приглашения на собрание, приведены ниже:

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendMeetingRequestsUsingExchangeServer-SendingMeetingRequestsUsingAnExchangeServerWebDav.java" >}}
