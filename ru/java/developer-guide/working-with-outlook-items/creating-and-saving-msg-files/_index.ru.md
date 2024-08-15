---
title: "Создание и сохранение файлов MSG"
url: /ru/java/creating-and-saving-msg-files/
weight: 10
type: docs
---


Aspose.Email поддерживает создание файлов сообщений Outlook (MSG). В этой статье объясняется, как:

- Создавайте сообщения MSG.
- Создавайте сообщения MSG с вложениями.
- Создайте сообщение MSG с телом RTF.
- Сохраните сообщение как черновик.
- Работа со сжатием тела.
 
## **Создание и сохранение сообщений Outlook**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс имеет [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) метод, позволяющий сохранять файлы Outlook MSG на диск или в потоковом режиме. Приведенные ниже фрагменты кода создают экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс, задайте такие свойства, как from, to, subject и body. [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) метод принимает имя файла в качестве аргумента. Кроме того, сообщения Outlook можно создавать с помощью [сжатый корпус RTF](#creating-msg-files-with-rtf-body) используя [MapiConversionOptions](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/).

1. Создайте новый экземпляр [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) класс и задайте свойства From, To, Subject и Body.
1. Позвоните [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) метод, который принимает объект [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) тип. The [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) метод преобразует [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) (MSG).
1. Позвоните [MapiMessage.save](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) метод сохранения файла MSG.

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

## **Создание файлов MSG с вложениями**

[В приведенном выше примере](#creating-and-saving-outlook-messages), мы создали простой файл MSG. Aspose.Email также поддерживает сохранение файлов сообщений с вложениями. Все, что вам нужно сделать, это добавить вложения в [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр. Добавьте вложения, вызвав *addItem* метод на [MailMessage.Attachments](https://reference.aspose.com/email/java/com.aspose.email/attachmentcollection/) collection.

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

## **Создание файлов MSG с помощью тела RTF**

С помощью Aspose.Email можно также создавать файлы сообщений Outlook (MSG) с телами RTF. Тело RTF поддерживает форматирование текста. Создайте его, установив [MailMessage.HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) имущество. Когда вы конвертируете [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) экземпляр в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) Например, тело HTML преобразуется в RTF. Таким образом, форматирование тела письма сохраняется.

В следующем примере создается файл MSG с телом RTF. В тексте HTML используется один заголовок, полужирный шрифт и подчеркивание. Это форматирование сохраняется при преобразовании HTML в RTF.

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
mailMsg.setHtmlBody("<h3>rtf example</h3><p>creating an <b><u>outlook message (msg)</u></b> file using Aspose.Email.</p>");

MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
outlookMsg.save(dataDir + "CreatingMSGFilesWithRTFBody_out.msg");
~~~

## **Сохранение сообщения в статусе черновика**

Письма сохраняются как черновики, когда кто-то начал их редактировать, но хочет вернуться к ним, чтобы завершить их позже. Aspose.Email поддерживает сохранение сообщений электронной почты в черновом статусе, установив флаг сообщения. Ниже приведен пример кода для сохранения сообщения электронной почты Outlook (MSG) в виде черновика.

{{% alert %}}
Обратите внимание, что в статусе черновика Outlook не отображает информацию об отправителе, назначенную MapiMessage.
Если нам нужно отобразить информацию об отправителе, мы должны установить флаг MSGFLAG_READ.
{{% /alert %}}


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Change properties of an existing MSG file
String strExistingMsg = "message.msg";

// Load the existing file in MailMessage and Change the properties
MailMessage msg = MailMessage.load(dataDir + strExistingMsg, new MsgLoadOptions());
msg.setSubject(msg.getSubject() + " NEW SUBJECT (updated by Aspose.Email)");
msg.setHtmlBody(msg.getHtmlBody() + " NEW BODY (udpated by Aspose.Email)");

// Create an instance of type MapiMessage from MailMessage, Set message flag to un-sent (draft status) and Save it
MapiMessage mapiMsg = MapiMessage.fromMailMessage(msg);
mapiMsg.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapiMsg.save(dataDir + "SavingMessageInDraftStatus_out.msg");
~~~

## **Последствия компрессии тела**

Метод сжатия тела RTF можно использовать для получения глутамата натрия меньшего размера. Однако это приводит к снижению скорости создания. Чтобы создавать сообщения с повышенной скоростью, установите флаг на **false**. Этот флаг, в свою очередь, влияет на созданные файлы PST: файлы MSG меньшего размера приводят к уменьшению размера PST, а большие файлы MSG замедляют создание PST.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MailMessage message = MailMessage.load(fileName);
MapiConversionOptions options = new MapiConversionOptions();
options.setUseBodyCompression(true);
MapiMessage ae_mapi = MapiMessage.fromMailMessage(message, options);
~~~
