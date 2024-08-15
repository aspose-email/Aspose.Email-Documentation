---
title: "Загрузка, просмотр и анализ файла MSG"
url: /ru/java/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---


В этом разделе описывается, как загрузить файл сообщений Microsoft Outlook (*.msg). [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс используется для загрузки файлов MSG и предоставляет несколько функций статической загрузки для разных сценариев. В следующем фрагменте кода показано, как загружать файлы MSG из файла или из потока.

## **Загрузка файлов MSG**

В следующем фрагменте кода показано, как загружать файлы MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = RunExamples.getDataDir_Outlook();

// Create an instance of MapiMessage from file
MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Get subject
System.out.println("Subject:" + msg.getSubject());

// Get from address
System.out.println("From:" + msg.getSenderEmailAddress());

// Get body
System.out.println("Body" + msg.getBody());

// Get recipients information
System.out.println("Recipient: " + msg.getRecipients());

// Get attachments
for (MapiAttachment att : msg.getAttachments())
{
    System.out.println("Attachment Name: " + att.getFileName());
    System.out.println("Attachment Display Name: " + att.getDisplayName());
}
~~~

В следующем примере кода показано, как использовать **MailMessage** для загрузки сообщения в формате MSG.

```Java
MailMessage eml = MailMessage.load("message.msg");
```

Следует отметить, что полученное сообщение преобразуется в формат EML, включая вложения встроенных сообщений. Не используйте этот метод загрузки, если вы хотите сохранить некоторые специфические свойства формата msg исходного сообщения.

Чтобы сохранить исходный формат вложенных сообщений, используйте [MsgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/#getPreserveEmbeddedMessageFormat--) property.

```Java
MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.setPreserveEmbeddedMessageFormat(true);
MailMessage msg = MailMessage.load(stream, msgLoadOptions);
```

## **Загрузка из потока**

В следующем фрагменте кода показано, как загрузить файл из потока.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of MapiMessage from file
try (FileInputStream stream = new FileInputStream(dataDir + "message.msg"))
{
    // Create an instance of MapiMessage from file
    MapiMessage msg = MapiMessage.fromStream(stream);

    // Get subject
    System.out.println("Subject:" + msg.getSubject());

    // Get from address
    System.out.println("From:" + msg.getSenderEmailAddress());

    // Get body
    System.out.println("Body" + msg.getBody());

}
~~~

## **Преобразование EML в MSG с сохранением встроенного формата EML**

Файлы EML можно загружать в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс путем создания экземпляра [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody()) объект и передача его [MapiMessage.fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-java.lang.String-) метод. Если файл EML содержит встроенные файлы EML, используйте [MapiConversionOptions.setPreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmbeddedMessageFormat-boolean-) для сохранения формата встроенных файлов EML. В приведенном ниже фрагменте кода показано, как загружать файлы EML в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) сохраняя при этом формат встроенных файлов EML.

{{% alert %}}
**Попробуйте!**

Конвертируйте электронные письма и архивы сообщений онлайн бесплатно [**Приложение для конвертации электронной почты Aspose.**](https://products.aspose.app/email/ru/Conversion).
{{% /alert %}}

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Email();

MailMessage eml = MailMessage.load(dataDir + "sample.eml", new EmlLoadOptions());

MapiConversionOptions options = MapiConversionOptions.getUnicodeFormat();

//Preserve Embedded Message Format
options.setPreserveEmbeddedMessageFormat(true);

//Convert EML to MSG with Options
MapiMessage msg = MapiMessage.fromMailMessage(eml, options);
~~~
