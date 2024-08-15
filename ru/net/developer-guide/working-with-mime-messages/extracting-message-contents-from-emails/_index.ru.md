---
title: "Извлечение содержимого сообщений из электронных писем"
url: /ru/net/extracting-message-contents-from-emails/
weight: 30
type: docs
---

# Извлечение содержимого сообщений из электронных писем

## **Отображение информации об электронной почте на экране**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) представляет собой сообщение электронной почты и предоставляет разработчикам доступ к свойствам сообщения электронной почты. Информация в заголовке (обсуждается в [Извлечение заголовков электронной почты](https://docs.aspose.com/email/ru/net/extracting-message-contents-from-emails/#extracting-email-headers)) можно извлекать и манипулировать им по-разному. В этой статье объясняется, как отображать выбранную информацию в заголовке электронного письма и текст письма на экране. Чтобы отобразить информацию об электронной почте на экране, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Загрузите сообщение электронной почты в [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.
- Отобразите содержимое электронной почты на экране.

В следующем фрагменте кода показано, как отображать информацию об электронной почте на экране.

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

Заголовок электронного письма представляет собой стандартный набор полей заголовков, определенных в Интернете и RFC, включенных в сообщения электронной почты Интернета. Заголовок электронного письма можно указать с помощью [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс. Общие типы заголовков определены в поле [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/) класс. Это закрытый класс, работающий как обычное перечисление. Чтобы извлечь заголовки из электронного письма, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Загрузите сообщение электронной почты в экземпляре [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. После загрузки сообщения электронной почты мы получим его необработанное содержимое.

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) Сам класс содержит такие свойства, как From, To, Cc, Subject и т. д. Эти свойства можно извлечь из заголовков.

В следующем фрагменте кода показано, как извлекать заголовки электронных писем.

## **Получите декодированные значения заголовков**

В следующем фрагменте кода показано, как получить декодированные значения заголовков.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
MailMessage mailMessage = MailMessage.Load(dataDir + "emlWithHeaders.eml");
string decodedValue = mailMessage.Headers.GetDecodedValue("Thread-Topic");
Console.WriteLine(decodedValue);
```

## **Получите текст в виде обычного текста**

The [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) свойство возвращает текстовое представление тела сообщения.

```csharp
string plainTextBody = mailMessage.Body;
```

Примечание. Если в сообщении присутствует текстовая/обычная часть MIME, свойство возвращает текстовые данные. В противном случае оно возвращает текстовое содержимое, отделенное от [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) свойство без html-разметки.

## **Получить текст HTML в виде обычного текста**

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс предоставляет возможность извлечения HTML-тела сообщения в виде обычного текста. [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) класс предоставляет [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) метод, который возвращает тело HTML в виде обычного текста. Этот метод анализирует [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) свойство и возвращает разделенное текстовое содержимое, игнорируя разметку html. [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) метод принимает логический параметр, указывающий, должно ли тело содержать URL-адреса или нет. Передача параметру значения true означает, что тело HTML должно содержать URL-адреса.

Следующий фрагмент кода демонстрирует использование [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/gethtmlbodytext/#gethtmlbodytext) метод извлечения HTML-тела электронного письма в виде обычного текста.

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
