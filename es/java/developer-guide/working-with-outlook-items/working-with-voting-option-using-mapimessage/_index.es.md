---
title: "Trabajando con la opción de votación usando MapiMessage"
url: /es/java/working-with-voting-option-using-mapimessage/
weight: 40
type: docs
---


## **Creación de una opción de votación con MapiMessage**

Microsoft Outlook permite a los usuarios crear una encuesta al redactar un mensaje nuevo. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. El [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/) la clase proporciona la [VotingButtons](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/#getVotingButtons--) propiedad que se puede usar para establecer u obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de cómo crear un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) con opciones de votación para crear una encuesta.

### **Creación de una encuesta con MapiMessage**

El siguiente fragmento de código muestra cómo crear una encuesta, el [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) la clase se puede usar como se muestra en el siguiente fragmento de código.

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

### **Lectura de las opciones de votación desde un mapiMessage**

El siguiente fragmento de código muestra cómo leer las opciones de votación de un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

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

### **Botones de votación de solo lectura**

El siguiente fragmento de código muestra cómo leer solo los botones de votación.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
InputStream ms = new FileInputStream(dataDir + "MapiMsgWithPoll_out.msg");
MapiMessage testMsg = MapiMessage.fromStream(ms);

// This method can be useful when it is necessary to read only voting buttons
// Voting buttons will be introduced as a collection of string values
IList buttons = FollowUpManager.getVotingButtons(testMsg);
~~~

### **Añadir un botón de votación a un mensaje existente**

El siguiente fragmento de código muestra cómo añadir un botón de votación a un mensaje existente.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.addVotingButton(mapi, "Indeed!");
mapi.save(dataDir + "AddVotingButtonToExistingMessage_out.msg");
~~~

### **Eliminar un botón de votación de un mensaje**

El siguiente fragmento de código muestra cómo eliminar un botón de voto de un mensaje.

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

### **Lea la información sobre los resultados de la votación**

El siguiente fragmento de código muestra cómo leer la información de los resultados de las votaciones.

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

### **Métodos de muestra utilizados en los ejemplos**

En el siguiente fragmento de código, se muestra cómo crear un mensaje de ejemplo que se utiliza en los ejemplos.

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
