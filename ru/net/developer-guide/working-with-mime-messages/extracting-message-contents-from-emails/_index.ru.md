---
title: "Извлечение содержимого сообщений из электронной почты"
url: /ru/net/extracting-message-contents-from-emails/
weight: 30
type: docs
---

# Извлечение содержимого сообщений из электронной почты

## **Отображение информации о электронной почте на экране**

[MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) представляет собой электронное сообщение и позволяет разработчикам получать доступ к свойствам электронных сообщений. Заголовочная информация (обсуждаемая в [Извлечение заголовков электронной почты](https://docs.aspose.com/email/ru/net/extracting-message-contents-from-emails/#extracting-email-headers)) может быть извлечена и обработана различными способами. В этой статье объясняется, как отобразить выбранную информацию о заголовках электронной почты и теле сообщения на экране. Чтобы отобразить информацию о электронной почте на экране, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Загрузите электронное сообщение в экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Отобразите содержимое электронной почты на экране.

Следующий фрагмент кода показывает, как отобразить информацию о электронной почте на экране.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Email();

// Create MailMessage instance by loading an Eml file
MailMessage message = MailMessage.Load(dataDir + "test.eml", new EmlLoadOptions());

// Gets the sender info, recipient info, Subject, htmlbody and textbody
Console.Write("From:");
Console.WriteLine(message.From);
Console.Write("To:");
Console.WriteLine(message.To);
Console.Write("Subject:");
Console.WriteLine(message.Subject);
Console.WriteLine("HtmlBody:");
Console.WriteLine(message.HtmlBody);
Console.WriteLine("TextBody");
Console.WriteLine(message.Body);
```

## **Извлечение заголовков электронной почты**

Заголовок электронной почты представляет собой стандартный набор полей заголовков, определенный в Internet и RFC, который включается в сообщения электронной почты. Заголовок электронной почты можно указать с помощью класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Общие типы заголовков определены в классе [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/). Это закрытый класс, который работает как обычная перечисляемая переменная. Чтобы извлечь заголовки из электронной почты, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
2. Загрузите электронное сообщение в экземпляр класса [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
3. После загрузки электронного сообщения мы получим его сырой контент.

Сам класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) содержит такие свойства, как From, To, Cc, Subject и так далее. Эти свойства можно извлечь из заголовков.

Следующий фрагмент кода показывает, как извлечь заголовки электронной почты.

## **Получение декодированных значений заголовка**

Следующий фрагмент кода показывает, как получить декодированные значения заголовка.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
MailMessage mailMessage = MailMessage.Load(dataDir + "emlWithHeaders.eml");
string decodedValue = mailMessage.Headers.GetDecodedValue("Thread-Topic");
Console.WriteLine(decodedValue);
```

## **Получение текста тела сообщения**

Свойство [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) возвращает текстовое представление тела сообщения.

```csharp
string plainTextBody = mailMessage.Body;
```

Примечание: Если в сообщении присутствует часть текста/plain MIME, свойство возвращает его текстовые данные. В противном случае оно возвращает отделенный текстовый контент из свойства [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) без HTML-разметки.

## **Получение HTML-тела как простого текста**

Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) предоставляет возможность извлечь HTML-тело сообщения как простой текст. Класс [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) предоставляет метод [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext), который возвращает HTML-тело в виде простого текста. Этот метод разбирает свойство [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) и возвращает отделенный контент простого текста, игнорируя HTML-разметку. Метод [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) принимает логический параметр, который указывает, должно ли тело содержать URL или нет. Передача параметра как true указывает, что HTML-тело должно содержать URL.

Следующий фрагмент кода демонстрирует использование метода [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) для извлечения HTML-тела электронной почты как простого текста.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Email();

MailMessage mail = MailMessage.Load(dataDir + "HtmlWithUrlSample.eml");

string body_with_url = mail.GetHtmlBodyText(true);// body will contain URL
string body_without_url = mail.GetHtmlBodyText(false);// body will not contain URL

Console.WriteLine("Body with URL: " + body_with_url);
Console.WriteLine("Body without URL: " + body_without_url);
```