---
title: "Работа с вариантом голосования с помощью MapiMessage"
url: /ru/java/working-with-voting-option-using-mapimessage/
weight: 40
type: docs
---

## **Создание варианта голосования с помощью MapiMessage**

Microsoft Outlook позволяет пользователям создавать опрос при составлении нового сообщения. Это позволяет им включать варианты голосования, такие как Да, Нет, Может быть и т.д. Aspose.Email позволяет делать то же самое при создании нового сообщения Outlook. Класс [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/) предоставляет свойство [VotingButtons](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/#getVotingButtons--), которое можно использовать для задания или получения значения вариантов голосования. Эта статья предоставляет подробный пример создания [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) с вариантами голосования для создания опроса.

### **Создание опроса с использованием MapiMessage**

Следующий фрагмент кода показывает, как создать опрос, класс [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) может быть использован, как показано в следующем фрагменте кода.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
String address = "firstname.lastname@aspose.com";
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Установить кнопки FollowUpOptions
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Да;Нет;Может быть;Точно!");
client.send(message, options);
~~~

### **Чтение вариантов голосования из MapiMessage**

Следующий фрагмент кода показывает, как прочитать варианты голосования из [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);

// Этот метод может быть полезен, когда, кроме кнопок голосования, необходимо получить другие параметры (например, категорию)
FollowUpOptions options = FollowUpManager.getOptions(message);

// Кнопки голосования будут представлены в виде строки с разделителем в виде точки с запятой
String votingButtons = options.getVotingButtons();
~~~

### **Чтение только кнопок голосования**

Следующий фрагмент кода показывает, как прочитать только кнопки голосования.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
InputStream ms = new FileInputStream(dataDir + "MapiMsgWithPoll_out.msg");
MapiMessage testMsg = MapiMessage.fromStream(ms);

// Этот метод может быть полезен, когда необходимо прочитать только кнопки голосования
// Кнопки голосования будут представлены в виде коллекции строковых значений
IList buttons = FollowUpManager.getVotingButtons(testMsg);
~~~

### **Добавление кнопки голосования в существующее сообщение**

Следующий фрагмент кода показывает, как добавить кнопку голосования в существующее сообщение.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.addVotingButton(mapi, "Действительно!");
mapi.save(dataDir + "AddVotingButtonToExistingMessage_out.msg");
~~~

### **Удаление кнопки голосования из сообщения**

Следующий фрагмент кода показывает, как удалить кнопку голоса из сообщения.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "outlook/";

// Создать новое сообщение и установить свойства FollowUpOptions, FollowUpManager
MapiMessage msg = createTestMessage(false);

FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Да;Нет;Может быть;Точно!");
FollowUpManager.setOptions(msg, options);
msg.save(dataDir + "MapiMsgWithPoll.msg");
FollowUpManager.removeVotingButton(msg, "Точно!"); // Удаление одной кнопки ИЛИ
FollowUpManager.clearVotingButtons(msg); // Удаление всех кнопок из MapiMessage
msg.save(dataDir + "MapiMsgWithPoll.msg");
~~~ 

### **Чтение информации о результатах голосования**

Следующий фрагмент кода показывает, как прочитать информацию о результатах голосования.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
// Путь к каталогу файлов.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "AddVotingButtonToExistingMessage.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Получатель: " + recipient.getDisplayName());

    // Получить свойство PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE
    System.out.println("Ответ: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE).getString());

    // Получить свойство PR_RECIPIENT_TRACKSTATUS_TIME
    System.out.println("Время ответа: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME).getDateTime());

    System.out.println();
}
~~~

### **Пример методов, используемых в примерах**

Следующий фрагмент кода показывает, как создать пример сообщения, используемого в примерах.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java
public static MapiMessage createTestMessage(boolean draft) {
    MapiMessage msg = new MapiMessage("from@test.com", "to@test.com", "Помеченное сообщение",
            "Сделайте это коротким и приятным, но описательным. Описание может появиться на страницах результатов поиска...");

    if (!draft) {
        msg.setMessageFlags(msg.getFlags() ^ MapiMessageFlags.MSGFLAG_UNSENT);
    }
    return msg;
}
~~~