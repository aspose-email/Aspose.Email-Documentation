---
title: "Управление файлами сообщений с помощью Aspose.Email.Outlook"
url: /ru/java/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Преобразование MSG в MIME-сообщение**

API Aspose.Email предоставляет возможность преобразования файлов MSG в MIME-сообщения с помощью метода [toMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMailMessage-com.aspose.email.MailConversionOptions-).

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
MapiMessage msg = new MapiMessage(
                            "sender@test.com",
                            "recipient1@test.com; recipient2@test.com",
                            "Тема теста",
                            "Это тело сообщения.");
MailConversionOptions options = new MailConversionOptions();
options.setConvertAsTnef(true);
MailMessage mail = msg.toMailMessage(options);
~~~

## **Преобразование MSG в EML с сохранением RTF-содержимого**

API предоставляет следующие методы для сохранения RTF-содержимого при преобразовании MSG в EML:

- [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-) - Получает или задает значение, указывающее, следует ли сохранять RTF-содержимое в MailMessage.
- [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-) - Получает или задает значение, указывающее, следует ли сохранять RTF-содержимое в MailMessage.

Следующие примеры кода демонстрируют, как сохранить RTF-содержимое в MailMessage:

- используя [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-)

```java
MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveRtfContent(true);
MailMessage message = MailMessage.load("fileName", options);
```
- используя [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-)

```java
MapiMessage mapi = MapiMessage.load("fileName");
MailConversionOptions options = new MailConversionOptions();
options.setPreserveRtfContent(true);
MailMessage message = mapi.toMailMessage(options);
```
## **Преобразование MSG в MHTML с сохранением заголовка категории**

API Aspose.Email предоставляет возможность добавления заголовка категории при преобразовании сообщения в MHTML. Эта функция задается классом [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) в качестве дополнительной опции при сохранении MailMessage в формате Mhtml.

Следующий пример кода демонстрирует, как создать файл MHT (MHTML) из объекта MapiMessage, настроить форматирование и заголовки MHT файла с использованием MhtSaveOptions, установить категории для электронного сообщения и затем изменить шаблоны формата и заголовков рендеринга для MHT файла перед его сохранением.

```java
 MapiMessage msg = new MapiMessage("from@aaa.com", "to@aaa.com", "subj", "body");

msg.setCategories(new String[] { "Срочно", "Важно" });

MhtSaveOptions saveOptions = new MhtSaveOptions();

saveOptions.getFormatTemplates().set_Item(MhtTemplateName.CATEGORIES,

    saveOptions.getFormatTemplates().get_Item(MhtTemplateName.CATEGORIES).replace("Categories", "Категории"));

saveOptions.getRenderingHeaders().add(MhtTemplateName.CATEGORIES);

msg.save("fileName.mhtml", saveOptions);
```

## **Чтение и запись файла шаблона Outlook (.OFT)**

Шаблоны Outlook очень полезны, когда вы хотите постоянно отправлять аналогичные электронные сообщения. Вместо того чтобы каждый раз готовить сообщение с нуля, сначала подготовьте сообщение в Outlook и сохраните его как шаблон Outlook (OFT). После этого, когда вам нужно будет отправить сообщение, вы можете создать его из шаблона, экономя время на написание одного и того же текста в теле или строке темы, установке форматирования и так далее. Класс Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) может использоваться для загрузки и чтения файла шаблона Outlook (OFT). После загрузки шаблона Outlook в экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) вы можете обновить отправителя, получателя, тело, тему и другие свойства. После обновления свойств:

- Отправьте электронное письмо с использованием класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) или
- Сохраните сообщение в формате MSG и выполните дальнейшие обновления/валидацию с помощью Microsoft Outlook.

В следующих примерах кода мы:

1. Загружаем шаблон с использованием класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Обновляем некоторые свойства.
1. Сохраняем сообщение в формате MSG.

Следующий фрагмент кода показывает, как загрузить файл OFT, обновить сообщение и сохранить его в формате MSG.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

// Загрузка файла шаблона Outlook (OFT) в экземпляре MailMessage
MailMessage message = MailMessage.load(dataDir + "sample.oft", new MsgLoadOptions());

// Установка информации об отправителе и получателе
String senderDisplayName = "Джон";
String senderEmailAddress = "john@abc.com";
String recipientDisplayName = "Уильям";
String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));
message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));
message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Установка имени, места и времени в теле электронной почты
String meetingLocation = "<u>" + "Зал 1, Конгресс-центр, Нью-Йорк, США" + "</u>";
String meetingTime = "<u>" + "Понедельник, 28 июня 2010 года" + "</u>";
message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));
message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Сохранение сообщения в формате MSG и открытие в Office Outlook
MapiMessage mapimessage = MapiMessage.fromMailMessage(message);
mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapimessage.save(dataDir + "ReadAndWritingOutlookTemplateFile_out.msg");
~~~ 

### **Сохранение файла Outlook MSG в качестве шаблона**

Следующий фрагмент кода показывает, как сохранить файл Outlook MSG в качестве шаблона.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

try (MapiMessage mapi = new MapiMessage("test@from.to", "test@to.to", "тема шаблона", "Тело шаблона")) {
    mapi.saveAsTemplate(dataDir + "mapiToOft.msg");
}
~~~ 

## **Установка цветовой категории для файлов Outlook MSG**

Цветовая категория помечает электронное сообщение как важное или относящееся к определенной категории. Microsoft Outlook позволяет пользователям назначать цветовые категории для различения электронных писем. Для работы с цветовой категорией используйте [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/). Он содержит функции такие как [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-), [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-), [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) и [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-).

- [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-) принимает [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) и строку цветовой категории, например, "Фиолетовая категория" или "Красная категория" в качестве аргументов.
- [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-) принимает [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) и строку цветовой категории, которую нужно удалить из сообщения.
- [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) используется для удаления всех цветовых категорий из сообщения.
- [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-) используется для извлечения всех цветовых категорий из конкретного сообщения.

Следующий пример выполняет указанные ниже задачи:

1. Добавить цветовую категорию.
2. Добавить другую цветовую категорию.
3. Извлечь список всех категорий.
4. Удалить все категории.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Добавить две категории
FollowUpManager.addCategory(msg, "Фиолетовая категория");
FollowUpManager.addCategory(msg, "Красная категория");

// Извлечь список доступных категорий
IList categories = FollowUpManager.getCategories(msg);

// Удалить указанную категорию, а затем очистить все категории
FollowUpManager.removeCategory(msg, "Красная категория");
FollowUpManager.clearCategories(msg);
~~~ 

## **Получение информации об отслеживании из файла MSG**

API Aspose.Email предоставляет возможность доступа к информации об отслеживании из отправленного или полученного сообщения. Он может извлекать информацию о прочтении, подтверждении доставки и результатах голосования из файла сообщения.

### **Извлечение информации о прочтении и подтверждении доставки**

Следующий фрагмент кода показывает, как извлечь информацию о прочтении и подтверждении доставки.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Получатель: " + recipient.getDisplayName());

    // Получить свойство PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY
    System.out.println("Время доставки: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY).getDateTime());

    // Получить свойство PR_RECIPIENT_TRACKSTATUS_TIME_READ
    System.out.println("Время прочтения: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ).getDateTime());
}
~~~ 

## **Создание сообщений "Переслать" и "Ответить"**

API Aspose.Email предоставляет возможность создания и форматирования сообщений "Переслать" и "Ответить". Классы [ReplyMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/replymessagebuilder/) и [ForwardMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/forwardmessagebuilder/) API используются для создания сообщений "Ответ" и "Переслать", соответственно. Сообщение "Ответ" или "Переслать" может быть указано на создание с использованием любого из режимов перечисления [OriginalMessageAdditionMode](https://reference.aspose.com/email/java/com.aspose.email/originalmessageadditionmode/). Это перечисление имеет следующие значения:

- **OriginalMessageAdditionMode.None** - Исходное сообщение не включается в ответное сообщение.
- **OriginalMessageAdditionMode.Attachment** - Исходное сообщение включается как вложение в ответное сообщение
- **OriginalMessageAdditionMode.Textpart** - Исходное сообщение включается как текст в теле ответного сообщения.

### **Создание сообщения "Ответ"**

Следующий фрагмент кода показывает, как создать сообщение "Ответ".

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ReplyMessageBuilder builder = new ReplyMessageBuilder();

// Установка свойств ReplyMessageBuilder
builder.setReplyAll(true);
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
builder.setResponseText(
        "<p><b>Дорогой друг,</b></p> Я хочу представить моего соавтора и сослуживца. <p><a href=\"www.google.com\">Это первая ссылка</a></p><p><a href=\"www.google.com\">Это вторая ссылка</a></p>");

MapiMessage replyMsg = builder.buildResponse(originalMsg);
replyMsg.save(dataDir + "reply_out.msg");
~~~ 

### **Создание сообщения "Переслать"**

Следующий фрагмент кода показывает, как создать сообщение "Переслать".

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по ссылке https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к директории файлов.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ForwardMessageBuilder builder = new ForwardMessageBuilder();
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
MapiMessage forwardMsg = builder.buildResponse(originalMsg);
forwardMsg.save(dataDir + "forward_out.msg");
~~~ 

## **Сохранение пустых дат при преобразовании сообщения**

Свойство [MapiConversionOptions.setPreserveEmptyDates(boolean)](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmptyDates-boolean-) указывает, необходимо ли сохранять пустые даты при преобразовании сообщения. Этот API появился в Aspose.Email 21.5. Следующий фрагмент кода показывает, как сохранить пустые даты.

~~~java
MailMessage mailMessage = MailMessage.load("message.eml");
System.out.println(mailMessage.getDate()); // нулевая дата
MapiConversionOptions mco = MapiConversionOptions.getUnicodeFormat();
// сохранить пустые даты при преобразовании сообщения
mco.setPreserveEmptyDates(true);
MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, mco);
System.out.println(mapiMessage.getClientSubmitTime()); // нулевая дата
// проверка нулевой даты
if (mapiMessage.getClientSubmitTime().equals(JavaHelper.ZERO_DATE))
    System.out.println("НУЛЕВАЯ ДАТА");
~~~