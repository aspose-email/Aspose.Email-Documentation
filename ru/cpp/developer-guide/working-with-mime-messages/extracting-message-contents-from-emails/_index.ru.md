---
title: "Извлечение Содержимого Сообщений из Электронных Писем на C++"
description: "Используя библиотеку парсера электронной почты на C++, вы можете получить доступ к свойствам сообщений электронной почты, информации заголовка и манипулировать ей различными способами программно."
url: /ru/cpp/extracting-message-contents-from-emails/
weight: 20
type: docs
linktitle: "Извлечение Содержимого Сообщений из Электронных Писем"
---

## **Отображение Информации о Электронной Почте на Экране**
[MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) представляет собой сообщение электронной почты и позволяет разработчикам получать доступ к свойствам сообщения электронной почты. Информация заголовка (обсуждаемая в разделе Извлечение Заголовков Электронной Почты) может быть извлечена и обработана различными способами. В этой статье объясняется, как отобразить выбранную информацию заголовков электронной почты и тело письма на экране. Чтобы отобразить информацию о электронной почте на экране, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
- Загрузите сообщение электронной почты в экземпляр [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
- Отобразите содержимое электронной почты на экране.

Следующий фрагмент кода на C++ показывает, как отобразить информацию о электронной почте на экране.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-DisplayEmailInformation-DisplayEmailInformation.cpp" >}}

## **Извлечение Заголовков Электронной Почты**
Заголовок электронной почты представляет собой стандартный набор заголовочных полей, определенных в Internet и RFC, которые включены в сообщения электронной почты. Заголовок электронной почты можно задать с помощью класса [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message). Общие типы заголовков определены в классе HeaderType. Это запечатанный класс, который работает как обычная перечислимое значение. Чтобы извлечь заголовки из электронной почты, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
1. Загрузите сообщение электронной почты в экземпляр класса [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message).
1. После загрузки сообщения электронной почты мы получим его необработанное содержимое.

Класс [`MailMessage`](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) сам по себе содержит такие свойства, как From, To, Cc, Subject и т.д. Эти свойства могут быть извлечены из заголовков.

1. Отобразите необработанное содержимое.

Следующий фрагмент кода на C++ показывает, как извлечь заголовки электронной почты.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-ExtractingEmailHeaders-ExtractingEmailHeaders.cpp" >}}

## **Получение Декодированных Значений Заголовков**
Следующий фрагмент кода показывает, как получить декодированные значения заголовков.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-GetDecodedHeaderValues-GetDecodedHeaderValue.cpp" >}}