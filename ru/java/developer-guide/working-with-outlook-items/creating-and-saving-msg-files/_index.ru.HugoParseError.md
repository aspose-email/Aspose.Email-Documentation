---
title: Создание и Сохранение MSG Файлов
type: docs
weight: 10
url: /java/creating-and-saving-msg-files/
---


Aspose.Email поддерживает создание файлов сообщений Outlook (MSG). В этой статье объясняется, как:

- Создавать сообщения MSG.
- Создавать сообщения MSG с вложениями.
- Создавать сообщение MSG с телом RTF.
- Сохранять сообщение как черновик.
- Работать с компрессией тела.
  
## **Создание и Сохранение Сообщений Outlook**

Класс [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) имеет метод [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-), который может сохранять файлы Outlook MSG на диск или в поток. Приведенные ниже кодовые фрагменты создают экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), устанавливают свойства, такие как от, до, тема и тело. Метод [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) принимает имя файла в качестве аргумента. Кроме того, сообщения Outlook могут быть созданы с [сжатоe телом RTF](#creating-msg-files-with-rtf-body) с использованием [MapiConversionOptions](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/).

1. Создайте новый экземпляр класса [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) и установите свойства From, To, Subject и Body.
1. Вызовите метод [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) класса [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), который принимает объект типа [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Метод [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) преобразует [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) (MSG).
1. Вызовите метод [MapiMessage.save](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-), чтобы сохранить файл MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setBody("This is test body");

// Create an instance of the MapiMessage class and pass MailMessage as argument
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);

// Save the message (MSG) file
String strMsgFile = "CreatingAndSavingOutlookMessages_out.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~

## **Создание MSG Файлов С Вложениями**

[В приведенном выше примере](#creating-and-saving-outlook-messages) мы создали простой файл MSG. Aspose.Email также поддерживает сохранение файлов сообщений с вложениями. Все, что вам нужно сделать, это добавить вложения в экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Добавьте вложения, вызвав метод *addItem* на коллекции [MailMessage.Attachments](https://reference.aspose.com/email/java/com.aspose.email/attachmentcollection/).

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

String[] files = new String[2];
files[0] = "attachment.doc";
files[1] = "attachment.png";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setBody("This is test body");

// Add the attachments
for (String strFileName : files)
{
    mailMsg.getAttachments().addItem(new Attachment(strFileName));
}

// Create an instance of MapiMessage class and pass MailMessage as argument
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
String strMsgFile = "CreateMessagesWithAttachments.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~

## **Создание MSG Файлов С Телом RTF**

Вы также можете создавать файлы сообщений Outlook (MSG) с телом с богатым текстом (RTF) с помощью Aspose.Email. Тело RTF поддерживает форматирование текста. Создайте его, установив свойство [MailMessage.HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-). Когда вы преобразуете экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) в экземпляр [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), HTML тело преобразуется в RTF. Таким образом, форматирование тела электронной почты сохраняется.

Следующий пример создает файл MSG с телом RTF. В нем есть один заголовок, примененное жирное и подчеркивающее форматирование в HTML теле. Это форматирование сохраняется при преобразовании HTML в RTF.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Create an instance of the MailMessage class
MailMessage mailMsg = new MailMessage();

// Set from, to, subject and body properties
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("This is test message");
mailMsg.setHtmlBody("<h3>rtf example</h3><p>создание <b><u>файла сообщения outlook (msg)</u></b> с использованием Aspose.Email.</p>");

MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
outlookMsg.save(dataDir + "CreatingMSGFilesWithRTFBody_out.msg");
~~~

## **Сохранение Сообщения в Статусе Черновика**

Электронные письма сохраняются как черновики, когда кто-то начал их редактировать, но хочет вернуться к ним позже, чтобы завершить. Aspose.Email поддерживает сохранение электронных сообщений в статусе черновика, устанавливая флаг сообщения. Ниже приведен пример кода для сохранения электронной почты Outlook (MSG) как черновика.

{{% alert %}}
Обратите внимание, что в статусе черновика Outlook не отображает никакой информации о отправителе, назначенной MapiMessage.
Если нам нужно отобразить информацию отправителя, мы должны установить флаг MSGFLAG_READ.
{{% /alert %}}


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Change properties of an existing MSG file
String strExistingMsg = "message.msg";

// Load the existing file in MailMessage and Change the properties
MailMessage msg = MailMessage.load(dataDir + strExistingMsg, new MsgLoadOptions());
msg.setSubject(msg.getSubject() + " НОВАЯ ТЕМА (обновлено Aspose.Email)");
msg.setHtmlBody(msg.getHtmlBody() + " НОВОЕ ТЕЛО (обновлено Aspose.Email)");

// Create an instance of type MapiMessage from MailMessage, Set message flag to un-sent (draft status) and Save it
MapiMessage mapiMsg = MapiMessage.fromMailMessage(msg);
mapiMsg.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapiMsg.save(dataDir + "SavingMessageInDraftStatus_out.msg");
~~~

## **Последствия Компрессии Тела**

Метод компрессии тела RTF может использоваться для создания файла MSG меньшего размера. Однако это приводит к снижению скорости создания. Чтобы создавать сообщения с улучшенной скоростью, установите флаг в **false**. Этот флаг, в свою очередь, влияет на созданные PST: меньшие файлы MSG приводят к меньшим PST, а большие файлы MSG приводят к медленному созданию PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MailMessage message = MailMessage.load(fileName);
MapiConversionOptions options = new MapiConversionOptions();
options.setUseBodyCompression(true);
MapiMessage ae_mapi = MapiMessage.fromMailMessage(message, options);
~~~