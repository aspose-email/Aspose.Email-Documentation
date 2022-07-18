---
title: Working with Voting Option Using MapiMessage
type: docs
weight: 40
url: /java/working-with-voting-option-using-mapimessage/
---


## **Creating Voting Option Using MapiMessage**
Microsoft Outlook lets users create a poll when composing a new message. It lets them include voting options such as Yes, No, Maybe, etc. Aspose.Email allows the same while creating a new Outlook message. The [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/FollowUpOptions) class provides the [VotingButtons](https://reference.aspose.com/email/java/com.aspose.email/FollowUpOptions#setVotingButtons\(java.lang.String\)) property that can be used to set or get the value of voting options. This article provides a detailed example of creating a [MapiMesasge](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) with voting options for creating a poll.
### **Creating a Poll using MapiMessage**
The following code snippet shows you how to create a poll, the [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/FollowUpManager) class can be used as shown in the following code snippet.



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
### **Reading Voting Options from a MapiMessage**
The following code snippet shows you how to Read Voting Options from a [MapiMesasge](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage).



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
### **Reading Only Voting Buttons**
The following code snippet shows you how to read only voting buttons.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
InputStream ms = new FileInputStream(dataDir + "MapiMsgWithPoll_out.msg");
MapiMessage testMsg = MapiMessage.fromStream(ms);

// This method can be useful when it is necessary to read only voting buttons
// Voting buttons will be introduced as a collection of string values
IList buttons = FollowUpManager.getVotingButtons(testMsg);
~~~
### **Adding voting button to an Existing Message**
The following code snippet shows you how to add a voting button to an existing message.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.addVotingButton(mapi, "Indeed!");
mapi.save(dataDir + "AddVotingButtonToExistingMessage_out.msg");
~~~
### **Deleting Voting button from a Message**
The following code snippet shows you how to delete the vote button from a Message.



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
### **Read the Vote Results Information**
The following code snippet shows you how to read the vote results information.



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
### **Sample Methods Used In Examples**
The following code snippet shows you how to create the sample message used in examples.



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
