---
title: "Разбор файлов сообщений Outlook"
url: /ru/java/parsing-outlook-message-files/
weight: 40
type: docs
---

{{% alert color="primary" %}}

Используя Aspose.Email для Java, разработчики могут не только загружать, но и анализировать содержимое файлов сообщений Outlook.

- Чтобы загрузить файлы MSG с диска, используйте [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс статический [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) method.
- Чтобы проанализировать содержимое файла MSG, [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) раскрывает ряд методов.

В этом разделе показано, как загрузить, а затем проанализировать файл MSG для отображения его содержимого.

{{% /alert %}}

Aspose.Email для Java предоставляет [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс, который используется для открытия и анализа файла MSG. Поскольку в файле MSG может быть много получателей, [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс раскрывает [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) метод, возвращающий [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) который представляет собой коллекцию [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) объекты. [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) объект дополнительно предоставляет методы работы с атрибутами получателя.

Для этого используется следующая последовательность шагов:

1. Создайте экземпляр [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) класс для загрузки файла MSG из [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) статический метод.
2. Отобразите имя, тему и текст отправителя из файла MSG, используя [getSenderName()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSenderName--), [getSubject()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSubject--) and [getBody()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getBody--) methods.
3. Позвоните [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) метод, представленный [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) класс, чтобы получить ссылку на коллекцию [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) объекты, связанные с файлом MSG.
4. Пройдите через [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) коллекция для отображения содержимого каждого [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) объект с помощью публичных методов.

```java
// The path to the resource directory.
String dataDir = Utils.getSharedDataDir(ParsingOutlookMessageFiles.class) + "outlook/";

//Instantiate an MSG file to load an MSG file from disk
MapiMessage outlookMessageFile = MapiMessage.fromFile(dataDir + "message.msg");
//Display sender's name
System.out.println("Sender Name : " + outlookMessageFile.getSenderName());
//Display Subject
System.out.println("Subject : " + outlookMessageFile.getSubject());
//Display Body
System.out.println("Body : " + outlookMessageFile.getBody());
//Display Recipient's info
System.out.println("Recipients : \n");

//Пройдите через recipients collection associated with the MapiMessage object
for (int i = 0; i < outlookMessageFile.getRecipients().size(); i++) {
	//Set a reference to the MapiRecipient object
	MapiRecipient rcp = (MapiRecipient) outlookMessageFile.getRecipients().get_Item(i);
	//Display recipient email address
	System.out.println("Email : " + rcp.getEmailAddress());
	//Display recipient name
	System.out.println("Name : " + rcp.getDisplayName());
	//Display recipient type
	System.out.println("Recipient Type : " + rcp.getRecipientType());
}
```

{{% alert %}}
**Попробуйте!**

Анализируйте файлы электронной почты онлайн бесплатно [**Приложение для парсера электронной почты Aspose.Email**](https://products.aspose.app/email/ru/parser).
{{% /alert %}}

## **Получите тип элемента сообщения MAPI**

Aspose.Email предлагает [MapiItemType](https://reference.aspose.com/email/java/com.aspose.email/mapiitemtype/) перечисление, представляющее тип элемента. Его можно использовать для преобразования сообщений в объект соответствующего класса, производный от [IMapiMessageItem](https://reference.aspose.com/email/java/com.aspose.email/imapimessageitem) интерфейс. Это позволяет пользователям не проверять значение свойства MessageClass перед преобразованием сообщения.

В следующем примере кода показано, как перебирать сообщения в папке и преобразовывать каждое сообщение MAPI в соответствующий тип элемента MAPI в зависимости от типа сообщения:

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    MapiMessage msg = pst.extractMessage(messageInfo);

    switch (msg.getSupportedType()) {
        // Non-supported type. MapiMessage cannot be converted to an appropriate item type.
        // Just use in MSG format.
        case MapiItemType.None:
            break;
        // An email message. Conversion isn't required.
        case MapiItemType.Message:
            break;
        // A contact item. Can be converted to MapiContact.
        case MapiItemType.Contact:
            MapiContact contact = (MapiContact) msg.toMapiMessageItem();
            break;
        // A calendar item. Can be converted to MapiCalendar.
        case MapiItemType.Calendar:
            MapiCalendar calendar = (MapiCalendar) msg.toMapiMessageItem();
            break;
        // A distribution list. Can be converted to MapiDistributionList.
        case MapiItemType.DistList:
            MapiDistributionList dl = (MapiDistributionList) msg.toMapiMessageItem();
            break;
        // A Journal entry. Can be converted to MapiJournal.
        case MapiItemType.Journal:
            MapiJournal journal = (MapiJournal) msg.toMapiMessageItem();
            break;
        // A StickyNote. Can be converted to MapiNote.
        case MapiItemType.Note:
            MapiNote note = (MapiNote) msg.toMapiMessageItem();
            break;
        // A Task item. Can be converted to MapiTask.
        case MapiItemType.Task:
            MapiTask task = (MapiTask) msg.toMapiMessageItem();
            break;
    }
}
```

