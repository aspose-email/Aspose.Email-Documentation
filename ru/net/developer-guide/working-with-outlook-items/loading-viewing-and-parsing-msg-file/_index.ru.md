---
title: "Загрузка, просмотр и анализ файла MSG"
url: /ru/net/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


В этом разделе описывается, как загрузить файл сообщений Microsoft Outlook (*.msg). [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) класс используется для загрузки файлов MSG и предоставляет несколько функций статической загрузки для разных сценариев. В следующем фрагменте кода показано, как загружать файлы MSG из файла или из потока.

## **Загрузка файлов MSG**

В следующем фрагменте кода показано, как загружать файлы MSG.

```cs
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Outlook();

// Create an instance of MapiMessage from file
MapiMessage msg = MapiMessage.Load(dataDir + @"message.msg");

// Get subject
Console.WriteLine("Subject:" + msg.Subject);

// Get from address
Console.WriteLine("From:" + msg.SenderEmailAddress);

// Get body
Console.WriteLine("Body" + msg.Body);

// Get recipients information
Console.WriteLine("Recipient: " + msg.Recipients);

// Get attachments
foreach (MapiAttachment att in msg.Attachments)
{
    Console.Write("Attachment Name: " + att.FileName);
    Console.Write("Attachment Display Name: " + att.DisplayName);
}
```

В следующем примере кода показано, как использовать MailMessage для загрузки сообщения в формате MSG.

```csharp

MailMessage eml = MailMessage.Load("message.msg");

```

Следует отметить, что полученное сообщение преобразуется в формат EML, включая вложения встроенных сообщений. Не используйте этот метод загрузки, если вы хотите сохранить некоторые специфические свойства формата msg исходного сообщения.

Чтобы сохранить исходный формат вложенных сообщений, используйте [msgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email/loadoptions/preserveembeddedmessageformat/) property.

```csharp

MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.PreserveEmbeddedMessageFormat = true;
var msg = MailMessage.Load(stream, msgLoadOptions);

```

## **Загрузка из стрима**

В следующем фрагменте кода показано, как загрузить файл из потока.

```cs
// Create an instance of MapiMessage from file
byte[] bytes = File.ReadAllBytes(dataDir + @"message.msg");

using (MemoryStream stream = new MemoryStream(bytes))
{
    stream.Seek(0, SeekOrigin.Begin);
    // Create an instance of MapiMessage from file
    MapiMessage msg = MapiMessage.Load(stream);

    // Get subject
    Console.WriteLine("Subject:" + msg.Subject);

    // Get from address
    Console.WriteLine("From:" + msg.SenderEmailAddress);

    // Get body
    Console.WriteLine("Body" + msg.Body);

}
```

Преобразование EML в MSG с сохранением встроенного формата EML

Файлы EML можно загружать в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) класс путем создания экземпляра [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) объект и передача его [MapiMessage.FromMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/frommailmessage/#frommailmessage/) метод. Если файл EML содержит встроенные файлы EML, используйте [MapiConversionOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/net/aspose.email.mapi/mapiconversionoptions/preserveembeddedmessageformat/) для сохранения формата встроенных файлов EML. В приведенном ниже фрагменте кода показано, как загружать файлы EML в [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) сохраняя при этом формат встроенных файлов EML.

{{% alert %}}
**Попробуйте!**

Конвертируйте электронные письма и архивы сообщений онлайн бесплатно [**Приложение для конвертации электронной почты Aspose.**](https://products.aspose.app/email/ru/Conversion).
{{% /alert %}}

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-PreservingEmbeddedMsgFormat-PreservingEmbeddedMsgFormat.cs" >}}
