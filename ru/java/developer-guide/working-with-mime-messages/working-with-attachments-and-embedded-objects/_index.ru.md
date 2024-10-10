---
title: "Работа с вложениями и встроенными объектами"
url: /ru/java/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---

## **Управление вложениями электронной почты**

Вложение электронной почты – это файл, который отправляется вместе с сообщением электронной почты. Файл может быть отправлен как отдельное сообщение, так и частью сообщения, к которому он прикреплен. Класс [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) используется вместе с классом [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage//). Все сообщения включают текст. В дополнение к тексту вы можете захотеть отправить дополнительные файлы. Они отправляются в качестве вложений и представлены в виде экземпляра класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//). Вы можете отправить любое количество вложений, но размер вложения ограничивается почтовым сервером. Gmail, например, не поддерживает размеры файлов более 10 МБ.
{{% alert %}}
**Попробуйте это!**

Добавьте или удалите вложения электронной почты онлайн с помощью бесплатного [**Aspose.Email Editor App**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавление вложения**

Чтобы прикрепить вложение к электронному письму, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Создайте экземпляр класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
1. Загрузите вложение в экземпляр [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
1. Добавьте экземпляр [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) в экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

Следующий код показывает, как добавить вложение к вашему электронному письму.

```java
// Create an instance of MailMessage class
MailMessage message = new MailMessage();
message.setFrom(new MailAddress("sender@from.com"));
message.getTo().add("receiver@to.com");
message.setSubject("This is message");
message.setBody("This is body");

// Load an attachment
Attachment attachment = new Attachment("1.txt");

// Add Multiple Attachment in instance of MailMessage class and Save message to disk
message.getAttachments().addItem(attachment);
message.addAttachment(new Attachment("1.jpg"));
message.addAttachment(new Attachment("1.doc"));
message.addAttachment(new Attachment("1.rar"));
message.addAttachment(new Attachment("1.pdf"));
message.save("AddAttachments.eml");
```

Выше мы описали, как добавить вложения к вашему сообщению электронной почты с помощью Aspose.Email. Далее показано, как удалить вложения и отобразить информацию о них на экране.

### **Удаление вложения**

Чтобы удалить вложение, выполните следующие шаги:

- Создайте экземпляр класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
- Загрузите вложение в экземпляр класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
- Добавьте вложение в экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Удалите вложения из экземпляра класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) с помощью экземпляра класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

Следующий код показывает, как удалить вложение.

```java
// Create an instance of MailMessage class
MailMessage eml = new MailMessage();
eml.setFrom(new MailAddress("sender@from.com"));
eml.getTo().add("receiver@to.com");

// Load an attachment
Attachment attachment = new Attachment("1.txt");
eml.getAttachments().addItem(attachment);

// Remove attachment from your MailMessage
eml.getAttachments().removeItem(attachment);
```

### **Отображение имени файла вложения**

Чтобы отобразить имя файла вложения, выполните следующие шаги:

1. Пройдитесь по вложениям в сообщении электронной почты и
   1. Сохраните каждое вложение.
   1. Отобразите каждое имя вложения на экране.

Следующий код показывает, как отобразить имя файла вложения на экране.

```java
MailMessage eml = MailMessage.load("Attachments.eml");

for (Attachment attachment : eml.getAttachments()) {
    // Display the attachment file name
    System.out.println(attachment.getName());
}
```

### **Извлечение вложений электронной почты**

Эта тема объясняет, как извлечь вложение из файла электронной почты. Вложение электронной почты – это файл, который отправляется вместе с сообщением электронной почты. Файл может быть отправлен как отдельное сообщение, так и частью сообщения, к которому он прикреплен. Все сообщения электронной почты включают опцию отправки дополнительных файлов. Эти файлы отправляются в качестве вложений и представлены экземплярами класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/). Класс [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) используется с классом [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) для работы с вложениями. Чтобы извлечь вложения из сообщения электронной почты, выполните следующие шаги:

- Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Загрузите файл электронной почты в экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Создайте экземпляр класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) в цикле для извлечения всех вложений.
- Сохраните вложение и отобразите его на экране.

|**Извлеченные вложения в электронной почте**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
Следующий код показывает, как извлечь вложения из электронной почты.

```java
MailMessage eml = MailMessage.load("Message.eml", new MsgLoadOptions());

for (Attachment attachment : eml.getAttachments()) {
    attachment.save("MessageEmbedded_out.eml");
    System.out.println(attachment.getName());
}
```

#### **Получение Content-Description из вложения**

API Aspose.Email предоставляет возможность читать Content-Description вложения из заголовка вложения. Следующий код показывает, как получить описание содержимого вложения.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");
System.out.println(eml.getAttachments().get_Item(0).getHeaders().get_Item("Content-Description"));
```

#### **Определение, является ли вложение встроенным сообщением**

Следующий код демонстрирует, как определить, является ли вложение встроенным сообщением или нет.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");

System.out.println(eml.getAttachments().get_Item(0).isEmbeddedMessage()
        ? "Attachment is an embedded message."
        : "Attachment isn't an embedded message.");
```
#### **Определение вложений в формате TNEF**

Свойство [Attachment.isTnef](https://reference.aspose.com/email/java/com.aspose.email/attachment/#isTnef--) API Aspose.Email Java указывает, является ли вложение сообщения форматом TNEF.

Следующий код демонстрирует, как определить, является ли вложение в формате TNEF:

```java
MailMessage eml = MailMessage.load(fileName);

for (Attachment attachment : eml.getAttachments()) {
    System.out.println("Is Attachment TNEF?: " + attachment.isTnef());
}
```

#### **Извлечение URI вложения, если вложение является URI-вложением**

Следующий код демонстрирует, как извлечь URI вложения.

~~~Java
MailMessage eml = MailMessage.load("fileName");

Attachment attachment = eml.getAttachments().get_Item(0);
if (attachment.isUri()) {
    InputStream inputStream = attachment.getContentStream();
    String uri = new String(IOUtils.toByteArray(inputStream), Charset.forName("utf-8"));
    System.out.println("Attachment URI: " + uri);
}
~~~

### **Добавление ссылочных вложений**

Ссылочное вложение является альтернативой локальному файловому вложению. В некоторых случаях ссылочные вложения могут быть предпочтительнее, например, если вы хотите управлять его доступом. Ниже приведены классы, используемые для управления и манипулирования сообщениями электронной почты и их вложениями:

- [ReferenceAttachment](https://reference.aspose.com/email/java/com.aspose.email/referenceattachment/) - представляет собой ссылочное вложение.
- [AttachmentPermissionType](https://reference.aspose.com/email/java/com.aspose.email/attachmentpermissiontype/) - тип данных разрешения, связанный с веб-ссылочным вложением.
- [AttachmentProviderType](https://reference.aspose.com/email/java/com.aspose.email/attachmentprovidertype/) - тип веб-сервиса, манипулирующего вложением.

Следующий пример кода демонстрирует, как загрузить сообщение электронной почты из файла, создать ссылочное вложение с определенными свойствами и добавить вложение в сообщение электронной почты:

```java
MailMessage eml = MailMessage.load("fileName");

ReferenceAttachment refAttach = new ReferenceAttachment("https://[attach_uri]");
refAttach.setName("Document.docx");
refAttach.setProviderType(AttachmentProviderType.OneDrivePro);
refAttach.setPermissionType(AttachmentPermissionType.AnyoneCanEdit);

eml.getAttachments().addItem(refAttach);
```

## **Работа с встроенными объектами**

Встроенный объект – это объект, созданный в одном приложении и заключенный в документ или файл, созданный другим приложением. Например, электронную таблицу Microsoft Excel можно встроить в отчет Microsoft Word, или видеофайл можно встроить в презентацию Microsoft PowerPoint. Когда файл встроен, а не вставлен или вставлен в другой документ, он сохраняет свой первоначальный формат. Встроенный документ можно открыть в оригинальном приложении и изменить.

### **Встраивание объектов в электронную почту**

Класс [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) используется с классом [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) для встраивания объектов в ваши сообщения электронной почты. Чтобы добавить встроенный объект, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Укажите значения от, до и темы в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Создайте экземпляр класса [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/).
1. Создайте экземпляр класса [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/).
1. Загрузите встроенный объект в [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/).
1. Добавьте загруженный встроенный объект в экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Добавьте экземпляр [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) в экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

Примеры кода ниже создают сообщение электронной почты с текстовой и HTML-частями и изображением, встроенным в HTML.

|**Изображение, встроенное в электронную почту**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Вы можете отправить любое количество встроенных объектов. Размер вложения ограничивается почтовым сервером. Gmail, например, не поддерживает размеры файлов более 10 МБ. Примеры кода ниже демонстрируют, как встроить объекты в электронную почту.

```java
// Create an instance of the MailMessage class and Set the addresses and Set the content
MailMessage mail = new MailMessage();
mail.setFrom(new MailAddress("sender@from.com"));
mail.getTo().add("receiver@to.com");
mail.setSubject("This is an email");

// Create the plain text part It is viewable by those clients that don't support HTML
AlternateView plainView = AlternateView.createAlternateViewFromString("This is my plain text content", null, "text/plain");

// Create the HTML part.To embed images, we need to use the prefix 'cid' in the img src value. 
// The cid value will map to the Content-Id of a Linked resource. 
// Thus <img src='cid:barcode'> will map to a LinkedResource with a ContentId of //'barcode'.
AlternateView htmlView = AlternateView.createAlternateViewFromString("Here is an embedded image.<img src=cid:barcode>", null, "text/html");

// Create the LinkedResource (embedded image) and Add the LinkedResource to the appropriate view
LinkedResource barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.JPEG);
barcode.setContentId("barcode");

mail.getLinkedResources().addItem(barcode);
mail.getAlternateViews().addItem(plainView);
mail.getAlternateViews().addItem(htmlView);
mail.save("EmbeddedImage_out.msg", SaveOptions.getDefaultMsgUnicode());
```

### **Удаление встроенных объектов из электронной почты**

[LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) доступна через свойство [MailMessage.LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLinkedResources--). Коллекция [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) предоставляет метод для полного удаления встроенных объектов, добавленных в сообщение электронной почты. Используйте перегруженную версию метода [LinkedResourceCollection.removeAt](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/#removeAt-int-boolean-) для удаления всех следов встроенного объекта из сообщения электронной почты.

Пример кода ниже показывает, как удалить встроенные объекты из сообщения электронной почты.

```java
// Load the test message with Linked Resources
MailMessage msg = MailMessage.load("EmlWithLinkedResources.eml");

// Remove a LinkedResource
msg.getLinkedResources().removeAt(0, true);

// Now clear the Alternate View for linked Resources
msg.getAlternateViews().get_Item(0).getLinkedResources().clear(true);
```

### **Извлечение встроенных объектов**

Эта тема объясняет, как извлечь встроенные объекты из файла электронной почты. Встроенный объект – это объект, созданный в одном приложении и заключенный в документ или файл, созданный другим приложением. Например, электронную таблицу Microsoft Excel можно встроить в отчет Microsoft Word, или видеофайл можно встроить в презентацию Microsoft PowerPoint. Когда файл встроен, а не вставлен или вставлен в другой документ, он сохраняет свой первоначальный формат. Встроенный документ можно открыть в оригинальном приложении и изменить. Чтобы извлечь встроенный объект из сообщения электронной почты, выполните следующие шаги:

1. Создайте экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Загрузите файл электронной почты в экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Создайте цикл и создайте экземпляр класса [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) в нем.
1. Сохраните вложение и отобразите его на экране.
1. Укажите адреса отправителя и получателя в экземпляре [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Отправьте электронное письмо с помощью класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).

Пример кода ниже извлекает встроенные объекты из электронной почты.

|**Извлеченные встроенные объекты в электронной почте**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
Следующий код показывает, как извлечь встроенные объекты.

```java
MailMessage mailMsg = MailMessage.load("Message.msg", new MsgLoadOptions());

for (Attachment attachment : mailMsg.getAttachments()) {
    attachment.save("MessageEmbedded_out.msg");
    System.out.println(attachment.getName());
}
```

#### **Определение и извлечение встроенного вложения из MSG, отформатированного как RTF**

Следующий код можно использовать для сообщений, отформатированных как RTF, чтобы различать и извлекать вложения, которые являются либо встроенными, либо отображаются как иконка в теле сообщения. Следующий код показывает, как идентифицировать и извлечь встроенное вложение из MSG, отформатированного как RTF.

```java
public static void extractInlineAttachments() {
    MapiMessage message = MapiMessage.load("MSG file with RTF Formatting.msg");
    for (MapiAttachment attachment : message.getAttachments()) {

        if (isAttachmentInline(attachment)) {
            try {
                saveAttachment(attachment, UUID.randomUUID().toString());
            } catch (Exception ex) {
                System.err.println(ex);
            }
        }
    }
}

static boolean isAttachmentInline(MapiAttachment attachment) {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("\u0003ObjInfo".equals(property.getName())) {
            byte[] data = property.getData();
            int odtPersist1 = data[1] << 8 | data[0];
            return (odtPersist1 & 0x40) == 0;
        }
    }
    return false;
}

static void saveAttachment(MapiAttachment attachment, String fileName) throws IOException {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("Package".equals(property.getName())) {
            try (FileOutputStream fs = new FileOutputStream(fileName)) {
                fs.write(property.getData(), 0, property.getData().length);
            }
        }
    }
}
```

## **Извлечение вложений из подписанных писем**

Подписанные письма содержат одно вложение **smime.p7m**. Это означает, что письмо зашифровано SMIME. 
Формат файла **Smime.p7m** – это цифровая подпись. 
Чтобы увидеть содержимое этого письма, используйте метод [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/). Метод возвращает объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) без цифровой подписи.

```java
MailMessage signedEml = MailMessage.load("signed.eml");

if (signedEml.isSigned()) {
    for (int i = 0; i < signedEml.getAttachments().size(); i++) {
        System.out.println("Signed email attachment" + i + ": " + signedEml.getAttachments().get_Item(i).getName());
    }

    // The email is signed. Remove a signature.
    MailMessage eml = signedEml.removeSignature();

    System.out.println("Signature removed.");

    for (int i = 0; i < eml.getAttachments().size(); i++) {
        System.out.println("Email attachment" + i + ": " + eml.getAttachments().get_Item(i).getName());
    }
}
```

### **Работа с Content-Type и Content-Disposition**

API Aspose.Email предоставляет возможность работать с [Content-Type](https://datatracker.ietf.org/doc/html/rfc2045#section-5) и [Content-Disposition](https://datatracker.ietf.org/doc/html/rfc2183) вложения из заголовка вложения. Следующий код показывает, как получить и изменить описание содержимого из вложения.

#### **Отображение параметров Content-Type и Content-Disposition**

Следующий код показывает, как отобразить параметры Content-Type и Content-Disposition на экране:

~~~Java
void run(MailMessage message) {
    // Attachments
    for (Attachment attachment : message.getAttachments()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
    // Linked Resources
    for (LinkedResource attachment : message.getLinkedResources()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
}

void printContentType(ContentType contentType) {
    System.out.println("media-type: " + contentType.getMediaType());
    System.out.println("charset: " + contentType.getCharSet());
    System.out.println("name: " + contentType.getName());
}

void printContentDisposition(ContentDisposition contentDisposition) {
    System.out.println("disposition-type: " + contentDisposition.getDispositionType());
    System.out.println("is-inline: " + contentDisposition.getInline());
    System.out.println("filename: " + contentDisposition.getFileName());
    System.out.println("creation-date: " + contentDisposition.getCreationDate());
    System.out.println("modification-date: " + contentDisposition.getModificationDate());
    System.out.println("read-date: " + contentDisposition.getReadDate());
    System.out.println("size: " + contentDisposition.getSize());
}
~~~ 

#### **Использование параметров Content-Type и Content-Disposition с вложениями**

Следующий код показывает, как использовать параметры Content-Type и Content-Disposition с вложением:

~~~Java
MailMessage eml = MailMessage.load(fileName);

Attachment attachment = new Attachment(pdfFileName, new ContentType("application/octet-stream"));
attachment.getContentDisposition().setDispositionType("attachment");
attachment.getContentDisposition().setFileName(fileName);

eml.addAttachment(attachment);
~~~