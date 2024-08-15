---
title: "Управление файлами сообщений с помощью Aspose.Email.Outlook"
url: /ru/java/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---


## **Преобразование MSG в сообщение MIME**

Aspose.Email API предоставляет возможность преобразования файлов MSG в сообщения MIME с помощью [toMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMailMessage-com.aspose.email.MailConversionOptions-) method.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiMessage msg = new MapiMessage(
                            "sender@test.com",
                            "recipient1@test.com; recipient2@test.com",
                            "Test Subject",
                            "This is a body of message.");
MailConversionOptions options = new MailConversionOptions();
options.setConvertAsTnef(true);
MailMessage mail = msg.toMailMessage(options);
~~~

## **Преобразование MSG в тело RTF с сохранением EML**

API предоставляет следующие методы сохранения тела RTF при преобразовании MSG в EML:

- [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-) - Определяет или задает значение, указывающее, следует ли сохранить тело rtf в MailMessage.
- [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-) - Определяет или задает значение, указывающее, следует ли сохранить тело rtf в MailMessage.

В следующих примерах кода показано, как сохранить тело rtf в MailMessage:

- using [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-)

```java
MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveRtfContent(true);
MailMessage message = MailMessage.load("fileName", options);
```
- using [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-)

```java
MapiMessage mapi = MapiMessage.load("fileName");
MailConversionOptions options = new MailConversionOptions();
options.setPreserveRtfContent(true);
MailMessage message = mapi.toMailMessage(options);
```
## **Преобразование MSG в MHTML с сохранением заголовка категории**

Aspose.Email API предоставляет возможность добавлять заголовок категории при преобразовании сообщения в MHTML. Эта функция определена [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) класс в качестве дополнительной опции при сохранении MailMessage в формате Mhtml.

В следующем примере кода показано, как создать файл MHT (MHTML) из объекта MapiMessage, настроить форматирование и заголовки файла MHT с помощью MHTSaveOptions, задать категории для сообщения электронной почты, а затем изменить шаблоны формата и заголовки рендеринга файла MHT перед его сохранением.

```java
 MapiMessage msg = new MapiMessage("from@aaa.com", "to@aaa.com", "subj", "body");

msg.setCategories(new String[] { "Urgently", "Important" });

MhtSaveOptions saveOptions = new MhtSaveOptions();

saveOptions.getFormatTemplates().set_Item(MhtTemplateName.CATEGORIES,

    saveOptions.getFormatTemplates().get_Item(MhtTemplateName.CATEGORIES).replace("Categories", "Les catégories"));

saveOptions.getRenderingHeaders().add(MhtTemplateName.CATEGORIES);

msg.save("fileName.mhtml", saveOptions);
```

## **Чтение и запись файла шаблона Outlook (.OFT)**

Шаблоны Outlook очень полезны, если вы хотите снова и снова отправлять одно и то же сообщение электронной почты. Вместо того чтобы каждый раз готовить сообщение с нуля, сначала подготовьте сообщение в Outlook и сохраните его как шаблон Outlook (OFT). После этого каждый раз, когда вам нужно отправить сообщение, вы можете создать его на основе шаблона, сэкономив время на написании того же текста в тексте или теме письма, настройке форматирования и т. д. Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс можно использовать для загрузки и чтения файла шаблона Outlook (OFT). Как только шаблон Outlook будет загружен в экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс, вы можете обновить отправителя, получателя, текст, тему и другие свойства. После обновления свойств:

- Отправьте электронное письмо, используя [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс или
- Сохраните сообщение как MSG и выполните дальнейшие обновления/проверку с помощью Microsoft Outlook.

В приведенных ниже примерах кода мы:

1. Загрузите шаблон, используя [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Обновите некоторые свойства.
1. Сохраните сообщение в формате MSG.

В следующем фрагменте кода показано, как загрузить файл OFT, обновить сообщение и сохранить его в формате MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Load the Outlook template (OFT) file in MailMessage's instance
MailMessage message = MailMessage.load(dataDir + "sample.oft", new MsgLoadOptions());

// Set the sender and recipients information
String senderDisplayName = "John";
String senderEmailAddress = "john@abc.com";
String recipientDisplayName = "William";
String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));
message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));
message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Set the name, location and time in email body
String meetingLocation = "<u>" + "Hall 1, Convention Center, New York, USA" + "</u>";
String meetingTime = "<u>" + "Monday, June 28, 2010" + "</u>";
message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));
message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Save the message in MSG format and open in Office Outlook
MapiMessage mapimessage = MapiMessage.fromMailMessage(message);
mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapimessage.save(dataDir + "ReadAndWritingOutlookTemplateFile_out.msg");
~~~

### **Сохранение MSG-файла Outlook в качестве шаблона**

В следующем фрагменте кода показано, как сохранить файл Outlook MSG в качестве шаблона.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

try (MapiMessage mapi = new MapiMessage("test@from.to", "test@to.to", "template subject", "Template body")) {
    mapi.saveAsTemplate(dataDir + "mapiToOft.msg");
}
~~~

## **Настройка цветовой категории для файлов Outlook MSG**

Цветовая категория обозначает сообщение электронной почты, относящееся к какой-либо важности или категории. Microsoft Outlook позволяет пользователям назначать цветовые категории для различения писем. Для обработки цветовой категории используйте [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/). Он содержит такие функции, как [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-), [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-), [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) and [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-).

- [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-) takes [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) и строку цветовой категории, например «Фиолетовая категория» или «Красная категория» в качестве аргументов.
- [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-) takes [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) и строку цветовой категории, которую нужно удалить из сообщения.
- [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) используется для удаления всех цветовых категорий из сообщения.
- [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-) используется для извлечения всех цветовых категорий из определенного сообщения.

В следующем примере выполняются задачи, указанные ниже:

1. Добавьте цветовую категорию.
2. Добавьте еще одну цветовую категорию.
3. Получите список всех категорий.
4. Удалить все категории.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Add Two category
FollowUpManager.addCategory(msg, "Purple Category");
FollowUpManager.addCategory(msg, "Red Category");

// Retrieve the list of available categories
IList categories = FollowUpManager.getCategories(msg);

// Remove the specified category and then Clear all categories
FollowUpManager.removeCategory(msg, "Red Category");
FollowUpManager.clearCategories(msg);
~~~

## **Доступ к дополнительной информации из файла MSG**

Aspose.Email API предоставляет возможность доступа к последующей информации из отправленного или полученного сообщения. Он может извлекать информацию о прочтении, доставке, прочтении и результатах голосования из файла сообщения.

### **Получение информации о прочтении и получении**

В следующем фрагменте кода показано, как получить информацию о прочтении и получении.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Recipient: " + recipient.getDisplayName());

    // Get the PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY property
    System.out.println("Delivery time: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY).getDateTime());

    // Get the PR_RECIPIENT_TRACKSTATUS_TIME_READ property
    System.out.println("Read time" + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ).getDateTime());
}
~~~

## **Создание сообщений для пересылки и ответа**

Aspose.Email API предоставляет возможность создавать и форматировать сообщения для пересылки и ответа. [ReplyMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/replymessagebuilder/) and [ForwardMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/forwardmessagebuilder/) классы API используются для создания сообщений Reply и Forward соответственно. Можно указать, что сообщение «Ответить» или «Переслать» можно создать с помощью любого из режимов [OriginalMessageAdditionMode](https://reference.aspose.com/email/java/com.aspose.email/originalmessageadditionmode/) перечисление. Это перечисление имеет следующие значения:

- **OriginalMessageAdditionMode.None** - Исходное сообщение не включено в ответное сообщение.
- **OriginalMessageAdditionMode.Attachment** - Исходное сообщение включено в ответное сообщение в виде вложения
- **OriginalMessageAdditionMode.Textpart** - Исходное сообщение включено в виде текста в текст ответного сообщения

### **Создание ответного сообщения**

В следующем фрагменте кода показано, как создать ответное сообщение.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ReplyMessageBuilder builder = new ReplyMessageBuilder();

// Set ReplyMessageBuilder Properties
builder.setReplyAll(true);
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
builder.setResponseText(
        "<p><b>Dear Friend,</b></p> I want to do is introduce my co-author and co-teacher. <p><a href=\"www.google.com\">This is a first link</a></p><p><a href=\"www.google.com\">This is a second link</a></p>");

MapiMessage replyMsg = builder.buildResponse(originalMsg);
replyMsg.save(dataDir + "reply_out.msg");
~~~

### **Создание пересылающего сообщения**

В следующем фрагменте кода показано, как создать сообщение для пересылки.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ForwardMessageBuilder builder = new ForwardMessageBuilder();
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
MapiMessage forwardMsg = builder.buildResponse(originalMsg);
forwardMsg.save(dataDir + "forward_out.msg");
~~~

## **Сохраняйте пустые даты при преобразовании сообщения**

[MapiConversionOptions.setPreserveEmptyDates(boolean)](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmptyDates-boolean-) свойство, указывающее, нужно ли сохранять пустые даты при преобразовании сообщения. Этот API появляется в Aspose.Email 21.5
В следующем фрагменте кода показано, как сохранить пустые даты.

~~~java
MailMessage mailMessage = MailMessage.load("message.eml");
System.out.println(mailMessage.getDate()); // zero date
MapiConversionOptions mco = MapiConversionOptions.getUnicodeFormat();
// keep empty dates when converting a message
mco.setPreserveEmptyDates(true);
MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, mco);
System.out.println(mapiMessage.getClientSubmitTime()); // zero date
// check zero date
if (mapiMessage.getClientSubmitTime().equals(JavaHelper.ZERO_DATE))
    System.out.println("ZERO DATE");
~~~