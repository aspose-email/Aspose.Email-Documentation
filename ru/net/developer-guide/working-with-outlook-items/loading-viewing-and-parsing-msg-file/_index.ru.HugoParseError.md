---
title: Загрузка, просмотр и разбор файла MSG
type: docs
weight: 20
url: /net/loading-viewing-and-parsing-msg-file/
---


Эта тема объясняет, как загрузить файл сообщения Microsoft Outlook (*.msg). Класс [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) используется для загрузки файлов MSG и предоставляет несколько статических функций загрузки для различных сценариев. Следующий фрагмент кода показывает, как загрузить файлы MSG из файла или из потока.

## **Загрузка файлов MSG**

Следующий фрагмент кода показывает, как загрузить файлы MSG.

```cs
// Путь к директории с файлами.
string dataDir = RunExamples.GetDataDir_Outlook();

// Создайте экземпляр MapiMessage из файла
MapiMessage msg = MapiMessage.Load(dataDir + @"message.msg");

// Получить тему
Console.WriteLine("Тема:" + msg.Subject);

// Получить адрес отправителя
Console.WriteLine("От:" + msg.SenderEmailAddress);

// Получить тело
Console.WriteLine("Тело" + msg.Body);

// Получить информацию о получателях
Console.WriteLine("Получатель: " + msg.Recipients);

// Получить вложения
foreach (MapiAttachment att in msg.Attachments)
{
    Console.Write("Имя вложения: " + att.FileName);
    Console.Write("Отображаемое имя вложения: " + att.DisplayName);
}
```

Следующий пример кода показывает, как использовать MailMessage для загрузки сообщения в формате MSG.

```csharp

MailMessage eml = MailMessage.Load("message.msg");

```

Следует отметить, что полученное сообщение конвертируется в формат EML, включая вложенные сообщения. Не используйте этот метод загрузки, если вы хотите сохранить некоторые специфические свойства формата msg оригинального сообщения.

Чтобы сохранить оригинальный формат вложенных сообщений, используйте свойство [msgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/).

```csharp

MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.PreserveEmbeddedMessageFormat = true;
var msg = MailMessage.Load(stream, msgLoadOptions);

```

## **Загрузка из потока**

Следующий фрагмент кода показывает, как загрузить файл из потока.

```cs
// Создайте экземпляр MapiMessage из файла
byte[] bytes = File.ReadAllBytes(dataDir + @"message.msg");

using (MemoryStream stream = new MemoryStream(bytes))
{
    stream.Seek(0, SeekOrigin.Begin);
    // Создайте экземпляр MapiMessage из файла
    MapiMessage msg = MapiMessage.Load(stream);

    // Получить тему
    Console.WriteLine("Тема:" + msg.Subject);

    // Получить адрес отправителя
    Console.WriteLine("От:" + msg.SenderEmailAddress);

    // Получить тело
    Console.WriteLine("Тело" + msg.Body);

}
```

Конвертация EML в MSG с сохранением формата встроенного EML

Файлы EML могут быть загружены в класс [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) путем создания объекта [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) и передачи его в метод [MapiMessage.FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/). Если файл EML содержит встроенные файлы EML, используйте [MapiConversionOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveembeddedmessageformat/) для сохранения формата встроенных файлов EML. Ниже приведен фрагмент кода, показывающий, как загрузить файлы EML в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) с сохранением формата встроенных файлов EML.

{{% alert %}}
**Попробуйте это!**

Конвертируйте электронные письма и архивы сообщений онлайн с помощью бесплатного [**Приложения Aspose.Email Conversion**](https://products.aspose.app/email/Conversion).
{{% /alert %}}

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}