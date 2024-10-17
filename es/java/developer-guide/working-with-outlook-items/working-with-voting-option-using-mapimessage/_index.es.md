---
title: "Trabajando con la Opción de Votación Usando MapiMessage"
url: /es/java/working-with-voting-option-using-mapimessage/
weight: 40
type: docs
---

## **Creando Opción de Votación Usando MapiMessage**

Microsoft Outlook permite a los usuarios crear una encuesta al redactar un nuevo mensaje. Les permite incluir opciones de votación como Sí, No, Quizás, etc. Aspose.Email permite lo mismo al crear un nuevo mensaje de Outlook. La clase [FollowUpOptions](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/) proporciona la propiedad [VotingButtons](https://reference.aspose.com/email/java/com.aspose.email/followupoptions/#getVotingButtons--) que se puede usar para establecer o obtener el valor de las opciones de votación. Este artículo proporciona un ejemplo detallado de la creación de un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) con opciones de votación para crear una encuesta.

### **Creando una Encuesta usando MapiMessage**

El siguiente fragmento de código muestra cómo crear una encuesta, la clase [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/) se puede utilizar como se muestra en el siguiente fragmento de código.

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

### **Leyendo Opciones de Votación de un MapiMessage**

El siguiente fragmento de código muestra cómo leer opciones de votación de un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).

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

### **Leyendo Solo Botones de Votación**

El siguiente fragmento de código muestra cómo leer solo los botones de votación.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
InputStream ms = new FileInputStream(dataDir + "MapiMsgWithPoll_out.msg");
MapiMessage testMsg = MapiMessage.fromStream(ms);

// This method can be useful when it is necessary to read only voting buttons
// Voting buttons will be introduced as a collection of string values
IList buttons = FollowUpManager.getVotingButtons(testMsg);
~~~

### **Agregando un botón de votación a un Mensaje Existente**

El siguiente fragmento de código muestra cómo agregar un botón de votación a un mensaje existente.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage mapi = MapiMessage.fromFile(dataDir + "message.msg");
FollowUpManager.addVotingButton(mapi, "Indeed!");
mapi.save(dataDir + "AddVotingButtonToExistingMessage_out.msg");
~~~

### **Eliminando un Botón de Votación de un Mensaje**

El siguiente fragmento de código muestra cómo eliminar un botón de votación de un mensaje.

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

### **Leer la Información de Resultados de Votación**

El siguiente fragmento de código muestra cómo leer la información de los resultados de la votación.

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

### **Métodos de Muestra Usados en Ejemplos**

El siguiente fragmento de código muestra cómo crear un mensaje de muestra utilizado en ejemplos.

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