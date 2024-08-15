---
title: "Работа с вложениями и встроенными объектами"
url: /ru/java/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---


## **Управление вложениями электронной почты**

Вложение электронной почты — это файл, который отправляется вместе с сообщением электронной почты. Файл можно отправить как отдельное сообщение, так и как часть сообщения, к которому он прикреплен. [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) класс используется с [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage//) класс. Все сообщения содержат текст. Помимо основного текста, возможно, вы захотите отправить дополнительные файлы. Они отправляются в виде вложений и представлены в виде экземпляров [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) класс. Можно отправить любое количество вложений, но размер вложения ограничен почтовым сервером. Например, Gmail не поддерживает файлы размером более 10 МБ.
{{% alert %}}
**Попробуйте!**

Добавляйте или удаляйте вложения электронной почты онлайн бесплатно [**Приложение для редактирования электронной почты Aspose.Email**](https://products.aspose.app/email/ru/editor).
{{% /alert %}}

### **Добавление вложения**

Чтобы прикрепить вложение к электронному письму, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Создайте экземпляр [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
1. Загрузите крепление в [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) instance.
1. Добавьте [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) экземпляр в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.

В следующем фрагменте кода показано, как добавить вложение в электронное письмо.

```java
// Создайте экземпляр MailMessage class
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

Выше мы описали, как добавлять вложения в сообщение электронной почты с помощью Aspose.Email. Ниже показано, как удалять вложения и отображать информацию о них на экране.

### **Удаление вложения**

Чтобы удалить вложение, выполните следующие действия:

- Создайте экземпляр [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
- Грузовое крепление в случае [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
- Добавьте вложение к экземпляру [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Удалите вложения из экземпляра [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) класс, использующий [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр класса.

В следующем фрагменте кода показано, как удалить вложение.

```java
// Создайте экземпляр MailMessage class
MailMessage eml = new MailMessage();
eml.setFrom(new MailAddress("sender@from.com"));
eml.getTo().add("receiver@to.com");

// Load an attachment
Attachment attachment = new Attachment("1.txt");
eml.getAttachments().addItem(attachment);

// Remove attachment from your MailMessage
eml.getAttachments().removeItem(attachment);
```

### **Отображение имени вложенного файла**

Чтобы отобразить имя вложенного файла, выполните следующие действия:

1. Просмотрите вложения в сообщении электронной почты и
   1. Сохраните каждое вложение.
   1. Отобразите имя каждого вложения на экране.

В следующем фрагменте кода показано, как отобразить имя вложенного файла на экране.

```java
MailMessage eml = MailMessage.load("Attachments.eml");

for (Attachment attachment : eml.getAttachments()) {
    // Display the attachment file name
    System.out.println(attachment.getName());
}
```

### **Извлечение вложений электронной почты**

В этом разделе описывается, как извлечь вложение из файла электронной почты. Вложение электронной почты — это файл, который отправляется вместе с сообщением электронной почты. Файл можно отправить как отдельное сообщение, так и как часть сообщения, к которому он прикреплен. Все сообщения электронной почты включают возможность отправки дополнительных файлов. Они отправляются в виде вложений и представлены в виде экземпляров [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) класс. [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) класс используется с [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс по работе с вложениями. Чтобы извлечь вложения из сообщения электронной почты, выполните следующие действия:

- Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Загрузите файл электронной почты в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
- Создайте экземпляр [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) класс и используйте его в цикле для извлечения всех вложений.
- Сохраните вложение и отобразите его на экране.

|**Извлеченные вложения в электронном письме**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
В следующем фрагменте кода показано, как извлекать вложения электронной почты.

```java
MailMessage eml = MailMessage.load("Message.eml", new MsgLoadOptions());

for (Attachment attachment : eml.getAttachments()) {
    attachment.save("MessageEmbedded_out.eml");
    System.out.println(attachment.getName());
}
```

#### **Извлечение описания содержимого из вложения**

Aspose.Email API предоставляет возможность читать описание содержимого вложения из заголовка вложения. В следующем фрагменте кода показано, как извлечь описание содержимого из вложения.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");
System.out.println(eml.getAttachments().get_Item(0).getHeaders().get_Item("Content-Description"));
```

#### **Определение того, является ли вложение встроенным сообщением**

В следующем фрагменте кода показано, как определить, является ли вложение встроенным сообщением или нет.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");

System.out.println(eml.getAttachments().get_Item(0).isEmbeddedMessage()
        ? "Attachment is an embedded message."
        : "Attachment isn't an embedded message.");
```
#### **Определение вложений в формате TNEF**

The [Attachment.isTnef](https://reference.aspose.com/email/java/com.aspose.email/attachment/#isTnef--) свойство Java API Aspose.Email указывает, является ли вложение сообщения сообщением в формате TNEF.

В следующем фрагменте кода показано, как определить, имеет ли вложение формат TNEF:

```java
MailMessage eml = MailMessage.load(fileName);

for (Attachment attachment : eml.getAttachments()) {
    System.out.println("Is Attachment TNEF?: " + attachment.isTnef());
}
```

#### **Извлечение URI вложения, если вложение является URI-вложением**

В следующем фрагменте кода показано, как извлечь URI вложения.

~~~Java
MailMessage eml = MailMessage.load("fileName");

Attachment attachment = eml.getAttachments().get_Item(0);
if (attachment.isUri()) {
    InputStream inputStream = attachment.getContentStream();
    String uri = new String(IOUtils.toByteArray(inputStream), Charset.forName("utf-8"));
    System.out.println("Attachment URI: " + uri);
}
~~~

### **Добавление справочных вложений**

Ссылочное вложение является альтернативой локальному вложению файла. В некоторых случаях предпочтительнее использовать вложения ссылок, например, если вы хотите управлять доступом к ним. Следующие классы используются для управления сообщениями электронной почты и их вложениями и манипулирования ими:

- [ReferenceAttachment](https://reference.aspose.com/email/java/com.aspose.email/referenceattachment/) - Представляет собой справочное вложение.
- [AttachmentPermissionType](https://reference.aspose.com/email/java/com.aspose.email/attachmentpermissiontype/) - Данные типа разрешения, связанные с вложением веб-ссылки.
- [AttachmentProviderType](https://reference.aspose.com/email/java/com.aspose.email/attachmentprovidertype/) - Тип веб-сервиса, манипулирующего вложением.

В следующем примере кода показано, как загрузить сообщение электронной почты из файла, создать ссылочное вложение с определенными свойствами и добавить вложение к сообщению электронной почты:

```java
MailMessage eml = MailMessage.load("fileName");

ReferenceAttachment refAttach = new ReferenceAttachment("https://[attach_uri]")
refAttach.setName("Document.docx");
refAttach.setProviderType(AttachmentProviderType.OneDrivePro);
refAttach.setPermissionType(AttachmentPermissionType.AnyoneCanEdit);

eml.getAttachments().addItem(refAttach);
```

## **Работа со встроенными объектами**

Встроенный объект — это объект, созданный в одном приложении и вложенный в документ или файл, созданный другим приложением. Например, электронную таблицу Microsoft Excel можно встроить в отчет Microsoft Word, а видеофайл — в презентацию Microsoft PowerPoint. Когда файл встраивается, а не вставляется или вставляется в другой документ, он сохраняет свой исходный формат. Встроенный документ можно открыть в исходном приложении и изменить.

### **Встраивание объектов в электронное письмо**

The [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) класс используется с [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс для встраивания объектов в сообщения электронной почты. Чтобы добавить встроенный объект, выполните следующие действия

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Укажите значения «от», «до» и «тема» в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Создайте экземпляр [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) class.
1. Создайте экземпляр [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) class.
1. Загрузите встроенный объект в [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/).
1. Добавьте загруженный встроенный объект в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр класса.
1. Добавьте [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) экземпляр к [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр класса.

Приведенные ниже фрагменты кода создают сообщение электронной почты, содержащее как обычный текст, так и текст HTML, а также изображение, встроенное в HTML.

|**Изображение, встроенное в электронную почту**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Можно отправить любое количество встроенных объектов. Размер вложения ограничен почтовым сервером. Например, Gmail не поддерживает файлы размером более 10 МБ. В приведенных ниже фрагментах кода показано, как встраивать объекты в электронное письмо.

```java
// Создайте экземпляр MailMessage class and Set the addresses and Set the content
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

// Create the LinkedResource (embedded image) and Добавьте LinkedResource to the appropriate view
LinkedResource barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.JPEG);
barcode.setContentId("barcode");

mail.getLinkedResources().addItem(barcode);
mail.getAlternateViews().addItem(plainView);
mail.getAlternateViews().addItem(htmlView);
mail.save("EmbeddedImage_out.msg", SaveOptions.getDefaultMsgUnicode());
```

### **Удаление встроенных объектов из электронной почты**

[LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) доступ к которому осуществляется через [MailMessage.LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLinkedResources--) имущество. Это [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) коллекция предоставляет метод полного удаления встроенных объектов, добавленных в сообщение электронной почты. Используйте перегруженную версию [LinkedResourceCollection.removeAt](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/#removeAt-int-boolean-) метод удаления всех следов встроенного объекта из сообщения электронной почты.

В приведенном ниже примере кода показано, как удалить встроенные объекты из сообщения электронной почты.

```java
// Load the test message with Linked Resources
MailMessage msg = MailMessage.load("EmlWithLinkedResources.eml");

// Remove a LinkedResource
msg.getLinkedResources().removeAt(0, true);

// Now clear the Alternate View for linked Resources
msg.getAlternateViews().get_Item(0).getLinkedResources().clear(true);
```

### **Извлечение встроенных объектов**

В этом разделе описывается, как извлечь встроенные объекты из файла электронной почты. Встроенный объект — это объект, созданный в одном приложении и вложенный в документ или файл, созданный другим приложением. Например, электронную таблицу Microsoft Excel можно встроить в отчет Microsoft Word, а видеофайл — в презентацию Microsoft PowerPoint. Когда файл встраивается, а не вставляется или вставляется в другой документ, он сохраняет свой исходный формат. Встроенный документ можно открыть в исходном приложении и изменить. Чтобы извлечь встроенный объект из сообщения электронной почты, выполните следующие действия:

1. Создайте экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Загрузите файл электронной почты в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Создайте цикл и создайте экземпляр [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) класс в нем.
1. Сохраните вложение и отобразите его на экране.
1. Укажите адрес отправителя и получателя в поле [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Отправка электронной почты с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class.

Приведенный ниже фрагмент кода извлекает встроенные объекты из электронного письма.

|**Извлеченные встроенные объекты в электронной почте**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
В следующем фрагменте кода показано, как извлекать встроенные объекты.

```java
MailMessage mailMsg = MailMessage.load("Message.msg", new MsgLoadOptions());

for (Attachment attachment : mailMsg.getAttachments()) {
    attachment.save("MessageEmbedded_out.msg");
    System.out.println(attachment.getName());
}
```

#### **Определите и извлеките встроенное вложение из MSG в формате RTF**

Следующий код можно использовать для сообщений, отформатированных в формате RTF, для различения и извлечения вложений, которые находятся в строке или отображаются в виде значка в теле сообщения. В следующем фрагменте кода показано, как идентифицировать и извлечь встроенное вложение из MSG в формате RTF.

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

## **Получение вложений из подписанного электронного письма**

Подписанные письма содержат одно **smime.p7m** вложение. Это означает, что электронное письмо зашифровано с помощью SMIME.
**Smime.p7m** формат файла — цифровая подпись.
Чтобы увидеть содержимое этого письма, используйте [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/) метод. Метод возвращает [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) объект без цифровой подписи.

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

### **Работа с типом контента и расположением контента**

Aspose.Email API предоставляет возможность работы с вложением [Content-Type](https://datatracker.ietf.org/doc/html/rfc2045#section-5) and [Content-Disposition](https://datatracker.ietf.org/doc/html/rfc2183) из заголовка вложения. В следующем фрагменте кода показано, как получить и изменить описание содержимого из вложения.

#### **Отображение параметров типа контента и расположения контента**

В следующем фрагменте кода показано, как отображать на экране параметры Content-Type и Content-Disposition:

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

#### **Использование параметров типа контента и расположения содержимого с вложениями**

В следующем фрагменте кода показано, как использовать параметры Content-Type и Content-Disposition с вложением:

~~~Java
MailMessage eml = MailMessage.load(fileName);

Attachment attachment = new Attachment(pdfFileName, new ContentType("application/octet-stream"));
attachment.getContentDisposition().setDispositionType("attachment");
attachment.getContentDisposition().setFileName(fileName);

eml.addAttachment(attachment);
~~~