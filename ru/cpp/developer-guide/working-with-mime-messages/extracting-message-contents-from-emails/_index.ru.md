---
title: "Извлечение содержимого сообщений из писем на C++"
description: "Используя библиотеку C++ Email Parser Library, вы можете получить доступ к свойствам сообщений электронной почты, информации в заголовках и программно управлять ими различными способами."
url: /ru/cpp/extracting-message-contents-from-emails/
weight: 20
type: docs
linktitle: "Извлечение содержимого сообщений из электронных писем"
---

## **Отображение информации об электронной почте на экране**
The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) представляет собой сообщение электронной почты и предоставляет разработчикам доступ к свойствам сообщения электронной почты. Информацию заголовка (описанную в разделе «Извлечение заголовков электронной почты») можно извлекать и обрабатывать различными способами. В этой статье объясняется, как отображать выбранную информацию в заголовке электронного письма и текст письма на экране. Чтобы отобразить информацию об электронной почте на экране, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
- Загрузите сообщение электронной почты в [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) instance.
- Отобразите содержимое электронной почты на экране.

В следующем фрагменте кода на языке C++ показано, как отображать информацию об электронной почте на экране.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-DisplayEmailInformation-DisplayEmailInformation.cpp" >}}

## **Извлечение заголовков электронной почты**
Заголовок электронного письма представляет собой стандартный набор полей заголовков, определенных в Интернете и RFC, включенных в сообщения электронной почты Интернета. Заголовок электронного письма можно указать с помощью [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) класс. Общие типы заголовков определены в классе HeaderType. Это запечатанный класс, работающий как обычное перечисление. Чтобы извлечь заголовки из электронного письма, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
1. Загрузите сообщение электронной почты в экземпляре [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
1. После загрузки сообщения электронной почты мы получим его необработанное содержимое.

The [`MailMessage`](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) Сам класс содержит такие свойства, как From, To, Cc, Subject и т. д. Эти свойства можно извлечь из заголовков.

1. Отобразите необработанный контент.

В следующем фрагменте кода на C++ показано, как извлекать заголовки писем.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-ExtractingEmailHeaders-ExtractingEmailHeaders.cpp" >}}

## **Получите декодированные значения заголовков**
В следующем фрагменте кода показано, как получить декодированные значения заголовков.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-GetDecodedHeaderValues-GetDecodedHeaderValue.cpp" >}}
