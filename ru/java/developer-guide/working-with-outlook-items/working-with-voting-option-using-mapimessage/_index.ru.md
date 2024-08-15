---
title: "Работа с опцией голосования с помощью MapiMessage"
url: /ru/java/working-with-voting-option-using-mapimessage/
weight: 40
type: docs
---


## **Создание опции голосования с помощью MapiMessage**

Microsoft Outlook позволяет пользователям создавать опрос при создании нового сообщения. Это позволяет им включать такие варианты голосования, как «Да», «Нет», «Возможно» и т. д. Aspose.Email позволяет использовать то же самое при создании нового сообщения Outlook. [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/) класс предоставляет [VotingButtons](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/#getVotingButtons--) свойство, которое можно использовать для установки или получения значения опций голосования. В этой статье представлен подробный пример создания [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) с вариантами голосования для создания опроса.

### **Создание опроса с помощью MapiMessage**

В следующем фрагменте кода показано, как создать опрос, [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) класс можно использовать, как показано в следующем фрагменте кода.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String address = "firstname.lastname@aspose.com";
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Set FollowUpOptions Buttons
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Yes;No;Maybe;Exactly!");
client.send(message, options);
~~~

### **Чтение вариантов голосования из MapiMessage**

В следующем фрагменте кода показано, как читать варианты голосования из [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String fileName = "outlook/message.msg";

MapiMessage message = MapiMessage.fromFile(fileName);

// This method can be useful when except voting buttons it is necessary to get other parameters (ex. a category)
FollowUpOptions options = FollowUpManager.getOptions(message);

// Voting buttons will be introduced as a string with semi-column as a separator
String votingButtons = options.getVotingButtons();
~~~

### **Кнопки голосования только для чтения**

В следующем фрагменте кода показано, как читать только кнопки голосования.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
InputStream ms = new FileInputStream(dataDir + "MapiMsgWithPoll_out.msg");
MapiMessage testMsg = MapiMessage.fromStream(ms);

// This method can be useful when it is necessary to read only voting buttons
// Voting buttons will be introduced as a collection of string values
IList buttons = FollowUpManager.getVotingButtons(testMsg);
~~~

### **Добавление кнопки голосования к существующему сообщению**

В следующем фрагменте кода показано, как добавить кнопку голосования к существующему сообщению.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.addVotingButton(mapi, "Indeed!");
mapi.save(dataDir + "AddVotingButtonToExistingMessage_out.msg");
~~~

### **Удаление кнопки голосования из сообщения**

В следующем фрагменте кода показано, как удалить кнопку голосования из сообщения.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Create New Message and set FollowUpOptions, FollowUpManager properties
MapiMessage msg = createTestMessage(false);

FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Yes;No;Maybe;Exactly!");
FollowUpManager.setOptions(msg, options);
msg.save(dataDir + "MapiMsgWithPoll.msg");
FollowUpManager.removeVotingButton(msg, "Exactly!"); // Deleting a single button OR
FollowUpManager.clearVotingButtons(msg); // Deleting all buttons from a MapiMessage
msg.save(dataDir + "MapiMsgWithPoll.msg");
~~~

### **Ознакомьтесь с информацией о результатах голосования**

В следующем фрагменте кода показано, как читать информацию о результатах голосования.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "AddVotingButtonToExistingMessage.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Recipient: " + recipient.getDisplayName());

    // Get the PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE property
    System.out.println("Response: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_AUTORESPONSE_PROP_RESPONSE).getString());

    // Get the PR_RECIPIENT_TRACKSTATUS_TIME property
    System.out.println("Response time: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME).getDateTime());

    System.out.println();
}
~~~

### **Примерные методы, используемые в примерах**

В следующем фрагменте кода показано, как создать образец сообщения, используемый в примерах.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static MapiMessage createTestMessage(boolean draft) {
    MapiMessage msg = new MapiMessage("from@test.com", "to@test.com", "Flagged message",
            "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...");

    if (!draft) {
        msg.setMessageFlags(msg.getFlags() ^ MapiMessageFlags.MSGFLAG_UNSENT);
    }
    return msg;
}
~~~
