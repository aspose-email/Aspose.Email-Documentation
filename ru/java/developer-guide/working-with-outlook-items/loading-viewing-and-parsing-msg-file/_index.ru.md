---
title: "Загрузка, просмотр и парсинг MSG файла"
url: /ru/java/loading-viewing-and-parsing-msg-file/
weight: 20
type: docs
---

Эта тема объясняет, как загрузить файл сообщения Microsoft Outlook (*.msg). Класс [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) используется для загрузки MSG файлов и предоставляет несколько статических функций загрузки для различных сценариев. Следующий фрагмент кода показывает, как загрузить MSG файлы из файла или из потока.

## **Загрузка MSG файлов**

Следующий фрагмент кода показывает, как загрузить MSG файлы.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = RunExamples.getDataDir_Outlook();

// Создание экземпляра MapiMessage из файла
MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Получение темы
System.out.println("Тема:" + msg.getSubject());

// Получение адреса отправителя
System.out.println("От:" + msg.getSenderEmailAddress());

// Получение тела
System.out.println("Тело" + msg.getBody());

// Получение информации о получателях
System.out.println("Получатель: " + msg.getRecipients());

// Получение вложений
for (MapiAttachment att : msg.getAttachments())
{
    System.out.println("Имя вложения: " + att.getFileName());
    System.out.println("Отображаемое имя вложения: " + att.getDisplayName());
}
~~~

Следующий кодовый пример показывает, как использовать **MailMessage** для загрузки сообщения в формате MSG.

```Java
MailMessage eml = MailMessage.load("message.msg");
```

Следует отметить, что результирующее сообщение конвертируется в формат EML, включая вложенные сообщения. Не используйте этот метод загрузки, если хотите сохранить некоторые специфические свойства формата msg оригинального сообщения.

Чтобы сохранить оригинальный формат вложенных сообщений, используйте свойство [MsgLoadOptions.PreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/loadoptions/#getPreserveEmbeddedMessageFormat--).

```Java
MsgLoadOptions msgLoadOptions = new MsgLoadOptions();
msgLoadOptions.setPreserveEmbeddedMessageFormat(true);
MailMessage msg = MailMessage.load(stream, msgLoadOptions);
```

## **Загрузка из потока**

Следующий фрагмент кода показывает, как загрузить файл из потока.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
// Создание экземпляра MapiMessage из файла
try (FileInputStream stream = new FileInputStream(dataDir + "message.msg"))
{
    // Создание экземпляра MapiMessage из файла
    MapiMessage msg = MapiMessage.fromStream(stream);

    // Получение темы
    System.out.println("Тема:" + msg.getSubject());

    // Получение адреса отправителя
    System.out.println("От:" + msg.getSenderEmailAddress());

    // Получение тела
    System.out.println("Тело" + msg.getBody());

}
~~~

## **Конвертирование EML в MSG с сохранением встроенного формата EML**

EML файлы могут быть загружены в класс [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) путем создания объекта [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody()) и передачи его в метод [MapiMessage.fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-java.lang.String-). Если файл EML содержит встроенные файлы EML, используйте [MapiConversionOptions.setPreserveEmbeddedMessageFormat](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmbeddedMessageFormat-boolean-), чтобы сохранить формат встроенных файлов EML. Ниже приведен фрагмент кода, который показывает, как загрузить EML файлы в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) с сохранением формата встроенных файлов EML.

{{% alert %}}
**Попробуйте!**

Конвертируйте электронные письма и архивы сообщений онлайн с помощью бесплатного [**Aspose.Email Conversion App**](https://products.aspose.app/email/ru/Conversion).
{{% /alert %}}

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите на https://github.com/aspose-email/Aspose.Email-for-Java
String dataDir = RunExamples.getDataDir_Email();

MailMessage eml = MailMessage.load(dataDir + "sample.eml", new EmlLoadOptions());

MapiConversionOptions options = MapiConversionOptions.getUnicodeFormat();

//Сохранение формата вложенного сообщения
options.setPreserveEmbeddedMessageFormat(true);

//Конвертация EML в MSG с параметрами
MapiMessage msg = MapiMessage.fromMailMessage(eml, options);
~~~
