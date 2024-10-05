---
title: Парсинг файлов сообщений Outlook
type: docs
weight: 40
url: /java/parsing-outlook-message-files/
---

{{% alert color="primary" %}} 

Используя Aspose.Email для Java, разработчики могут не только загружать, но и парсить содержимое файлов сообщений Outlook.

- Для загрузки файлов MSG с диска используйте статический метод [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-) класса [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
- Для парсинга содержимого файла MSG класс [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) предоставляет ряд методов.

Эта тема показывает, как загрузить и затем парсить файл MSG для отображения его содержимого.

{{% /alert %}} 

Aspose.Email для Java предоставляет класс [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) , который используется для открытия и парсинга файла MSG. Поскольку в файле MSG может быть много получателей, класс [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) выставляет метод [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) , который возвращает [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) , представляющий собой коллекцию объектов [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/). Объект [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) дополнительно предлагает методы для работы с атрибутами получателя.

Следующая последовательность шагов служит этой цели:

1. Создайте экземпляр класса [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) для загрузки файла MSG с помощью статического метода [Load](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#load-java.lang.String-).
2. Отобразите имя отправителя, тему и текст сообщения из файла MSG, используя методы [getSenderName()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSenderName--), [getSubject()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getSubject--) и [getBody()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getBody--) .
3. Вызовите метод [getRecipients()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#getRecipients--) , предоставленный классом [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/), чтобы получить ссылку на коллекцию объектов [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/), связанных с файлом MSG.
4. Переберите коллекцию [MapiRecipientCollection](https://reference.aspose.com/email/java/com.aspose.email/mapirecipientcollection/) , чтобы отобразить содержимое для каждого объекта [MapiRecipient](https://reference.aspose.com/email/java/com.aspose.email/mapirecipient/) через его публичные методы.

```java
// Путь к каталогу ресурсов.
String dataDir = Utils.getSharedDataDir(ParsingOutlookMessageFiles.class) + "outlook/";

//Создание файла MSG для загрузки файла MSG с диска
MapiMessage outlookMessageFile = MapiMessage.fromFile(dataDir + "message.msg");
//Отображение имени отправителя
System.out.println("Sender Name : " + outlookMessageFile.getSenderName());
//Отображение темы
System.out.println("Subject : " + outlookMessageFile.getSubject());
//Отображение текста
System.out.println("Body : " + outlookMessageFile.getBody());
//Отображение информации о получателе
System.out.println("Recipients : \n");

//Перебор коллекции получателей, связанной с объектом MapiMessage
for (int i = 0; i < outlookMessageFile.getRecipients().size(); i++) {
	//Установка ссылки на объект MapiRecipient
	MapiRecipient rcp = (MapiRecipient) outlookMessageFile.getRecipients().get_Item(i);
	//Отображение адреса электронной почты получателя
	System.out.println("Email : " + rcp.getEmailAddress());
	//Отображение имени получателя
	System.out.println("Name : " + rcp.getDisplayName());
	//Отображение типа получателя
	System.out.println("Recipient Type : " + rcp.getRecipientType());
}
```

{{% alert %}}
**Попробуйте это!**

Парсите электронные письма онлайн с помощью бесплатного [**Aspose.Email Parser App**](https://products.aspose.app/email/parser).
{{% /alert %}}

## **Получение типа элемента MAPI-сообщения**

Aspose.Email предлагает перечисление [MapiItemType](https://reference.aspose.com/email/java/com.aspose.email/mapiitemtype/) , которое представляет собой тип элемента. Оно может быть использовано для преобразования сообщения в объект соответствующего класса, производного от интерфейса [IMapiMessageItem](https://reference.aspose.com/email/java/com.aspose.email/imapimessageitem). Это позволяет пользователям не проверять значение свойства MessageClass перед преобразованием сообщения.

Следующий пример кода демонстрирует, как перебрать сообщения в папке и преобразовать каждое MAPI-сообщение в соответствующий тип элемента MAPI, в зависимости от типа сообщения:

```java
for (MessageInfo messageInfo : folder.enumerateMessages()) {
    MapiMessage msg = pst.extractMessage(messageInfo);

    switch (msg.getSupportedType()) {
        // Неподдерживаемый тип. MapiMessage не может быть преобразовано в соответствующий тип элемента.
        // Просто используйте в формате MSG.
        case MapiItemType.None:
            break;
        // Электронное сообщение. Преобразование не требуется.
        case MapiItemType.Message:
            break;
        // Элемент контакта. Может быть преобразовано в MapiContact.
        case MapiItemType.Contact:
            MapiContact contact = (MapiContact) msg.toMapiMessageItem();
            break;
        // Элемент календаря. Может быть преобразовано в MapiCalendar.
        case MapiItemType.Calendar:
            MapiCalendar calendar = (MapiCalendar) msg.toMapiMessageItem();
            break;
        // Рассылка. Может быть преобразовано в MapiDistributionList.
        case MapiItemType.DistList:
            MapiDistributionList dl = (MapiDistributionList) msg.toMapiMessageItem();
            break;
        // Запись журнала. Может быть преобразовано в MapiJournal.
        case MapiItemType.Journal:
            MapiJournal journal = (MapiJournal) msg.toMapiMessageItem();
            break;
        // Заметка. Может быть преобразовано в MapiNote.
        case MapiItemType.Note:
            MapiNote note = (MapiNote) msg.toMapiMessageItem();
            break;
        // Задача. Может быть преобразовано в MapiTask.
        case MapiItemType.Task:
            MapiTask task = (MapiTask) msg.toMapiMessageItem();
            break;
    }
}
```