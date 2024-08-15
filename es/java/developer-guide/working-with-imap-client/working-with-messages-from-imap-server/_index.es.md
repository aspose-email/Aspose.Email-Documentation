---
title: "Trabajando con mensajes del servidor IMAP"
url: /es/java/working-with-messages-from-imap-server/
weight: 20
type: docs
---


## **Listado de identificadores de mensajes MIME del servidor**

[ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) proporciona el MIME [MessageId](https://reference.aspose.com/email/java/com.aspose.email/messageinfobase/#getMessageId--) para identificar el mensaje sin extraer el mensaje completo. En el siguiente fragmento de código, se muestra cómo incluir MIME MessageID.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");

try {
    ImapMessageInfoCollection messageInfoCol = client.listMessages("Inbox");
    for (ImapMessageInfo info : messageInfoCol) {
        // Display MIME Message ID
        System.out.println("Message Id = " + info.getMessageId());
    }
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Listado de mensajes del servidor**

Aspose.Email ofrece una variante sobrecargada para 2 miembros de [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) para recuperar un número específico de mensajes en función de una consulta. El siguiente fragmento de código muestra cómo enumerar los mensajes.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");

// Select the inbox folder and Get the message info collection
ImapQueryBuilder builder = new ImapQueryBuilder();
MailQuery query = builder
        .or(builder.or(builder.or(builder.or(builder.getSubject().contains(" (1) "), builder.getSubject().contains(" (2) ")), builder.getSubject().contains(" (3) ")),
                builder.getSubject().contains(" (4) ")), builder.getSubject().contains(" (5) "));
ImapMessageInfoCollection messageInfoCol4 = client.listMessages(query, 4);
System.out.println((messageInfoCol4.size() == 4) ? "Success" : "Failure");
~~~

## **Listar los mensajes del servidor de forma recursiva**

El protocolo IMAP admite la enumeración recursiva de los mensajes de una carpeta de buzones de correo. Esto también ayuda a enumerar los mensajes de las subcarpetas de una carpeta. En el siguiente fragmento de código, se muestra cómo enumerar los mensajes de forma recursiva.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient();
client.setHost("domain.com");
client.setUsername("username");
client.setPassword("password");
client.selectFolder("InBox");
ImapMessageInfoCollection msgsColl = client.listMessages(true);
System.out.println("Total Messages: " + msgsColl.size());
~~~

## **Listar mensajes con MultiConnection**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona un [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setUseMultiConnection-int-) propiedad que se puede usar para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se usarán durante el modo multiconexión utilizando [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setConnectionsQuantity-int-). El siguiente fragmento de código muestra el uso del modo multiconexión para enumerar los mensajes y compara su rendimiento con el modo de conexión única.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

imapClient.selectFolder("Inbox");
imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol1 = imapClient.listMessages(true);
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

imapClient.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
ImapMessageInfoCollection messageInfoCol2 = imapClient.listMessages(true);
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Performance Relation: " + performanceRelation);
~~~
{{% alert color="primary" %}}

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Recibe los mensajes en orden descendente**

Aspose.Email proporciona [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) método que enumera los mensajes con soporte de paginación. Algunas sobrecargas de [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) accept [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) como parámetro. [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) proporciona un [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) propiedad que, cuando se establece en **false**, devuelve los correos electrónicos en orden descendente.

El siguiente código de ejemplo demuestra el uso de [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) propiedad del [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) clase para cambiar el orden de los correos electrónicos.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

PageSettings pageSettings = new PageSettings();
pageSettings.setAscendingSorting(false);
ImapPageInfo pageInfo = imapClient.listMessagesByPage(5, pageSettings);
ImapMessageInfoCollection messages = pageInfo.getItems();

for (ImapMessageInfo message : messages) {
    System.out.println(message.getSubject() + " -> " + message.getDate().toString());
}
~~~

## **Recuperar mensajes del servidor y guardarlos en el disco**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) La clase puede obtener mensajes de un servidor IMAP y guardar los mensajes en formato EML en un disco local. Se requieren los siguientes pasos para guardar los mensajes en el disco:

1. Crea una instancia del [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Especifique un nombre de host, un puerto, un nombre de usuario y una contraseña en IMAPClient [constructor](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#ImapClient\(java.lang.String,%20int,%20java.lang.String,%20java.lang.String\)).
1. Seleccione la carpeta mediante [selectFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#selectFolder-com.aspose.email.IConnection-java.lang.String-) method.
1. Llame al [listMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) método para obtener el [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) object.
1. Recorra en iteración el [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) colección, llame al [saveMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#saveMessage-com.aspose.email.IConnection-int-java.io.OutputStream-) método y proporcione la ruta de salida y el nombre del archivo.

El siguiente fragmento de código muestra cómo obtener mensajes de correo electrónico de un servidor y guardarlos.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Select the inbox folder and Get the message info collection
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Download each message
for (int i = 0; i < list.size(); i++) {
    // Save the EML file locally
    client.saveMessage(list.get_Item(i).getUniqueId(), dataDir + list.get_Item(i).getUniqueId() + ".eml");
}
~~~

## **Guardar mensajes en formato MSG**

[En el ejemplo anterior](#fetch-messages-from-server-and-save-to-disc), los correos electrónicos se guardan en formato EML. Para guardar los correos electrónicos en formato MSG, el [ImapClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessage-com.aspose.email.IConnection-int-) es necesario llamar al método. Devuelve el mensaje en una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase. El [MailMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) Luego se puede llamar al método para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo guardar mensajes en formato MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the file directory.
String dataDir = "data/";

// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");

// Select the inbox folder and Get the message info collection
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Download each message
for (int i = 0; i < list.size(); i++) {
    // Save the message in MSG format
    MailMessage message = client.fetchMessage(list.get_Item(i).getUniqueId());
    message.save(dataDir + list.get_Item(i).getUniqueId() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~

## **Mensajes de búsqueda grupales**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona un [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) método que acepta números de secuencia iterables o ID únicos y devuelve una lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). El siguiente fragmento de código demuestra el uso del [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) método para buscar mensajes por números de secuencia e ID único.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
System.out.println("ListMessages Count: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (ImapMessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : imapClient.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : imapClient.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~

## **Enhebrado de correo electrónico/Organización de correos electrónicos en conversaciones**

Aspose.Email permite agrupar todos los reenvíos, respuestas y todos los mensajes relacionados con la misma conversación de forma jerárquica. Básicamente, el protocolo IMAP puede admitir la capacidad de subprocesos definida en el RFC-5256. Además, hay otra extensión IMAP proporcionada por Gmail y descrita como X-GM-EXT-1.

Están disponibles las siguientes funciones de subprocesamiento de correo electrónico:

- [getMessageThreads](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getMessageThreads-com.aspose.email.BaseSearchConditions-) método: recibe hilos de mensajes por [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
- boolean [getGmExt1Supported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getGmExt1Supported--) - Obtiene información sobre si la extensión Gmail X-GM-EXT-1 es compatible.
- boolean [getThreadSupported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadSupported--) - Obtiene información sobre si la extensión THREAD es compatible.
- String[] [getThreadAlgorithms](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadAlgorithms--) - Obtiene los algoritmos THREAD compatibles.

En los siguientes ejemplos de código se muestra el uso de estas funciones para obtener las cadenas de correo electrónico de Gmail:

```java
  ImapClient client = new ImapClient("imap.gmail.com", 993, "username", "password", SecurityOptions.SSLImplicit);

try {

    client.selectFolder(ImapFolderInfo.IN_BOX);

   // get a list of messages that we'll group by conversation

   ImapMessageInfoCollection messages = client.listMessages();

   // make sure the IMAP server supports X-GM-EXT-1 extension

   if (client.getGmExt1Supported()) {

       // gets unique conversationId for our example

       Set<String> conversationIds = new HashSet<String>();

       for (ImapMessageInfo messageInfo : messages) {

           if (messageInfo.getConversationId() != null)

                conversationIds.add(messageInfo.getConversationId());

       }

       for (String conversationId : conversationIds) {

           // create the necessary search conditions for a thread

           XGMThreadSearchConditions conditions = new XGMThreadSearchConditions();

            conditions.setConversationId(conversationId);

            conditions.setUseUId(true);

           // get results

           List<MessageThreadResult> conversation = client.getMessageThreads(conditions);

           // print the email conversation in hierarchically manner

           printConversaton("", conversation, messages);

            System.out.println("--------------------");

       }

   }

} finally {

    client.dispose();

}

/**

 * <p>

 * Prints the email conversation in hierarchically manner

 * </p>

 */

public static void printConversaton(String indent, Iterable<MessageThreadResult> conversation,

    Iterable<ImapMessageInfo> messages) {

   for (MessageThreadResult thread : conversation) {

       for (ImapMessageInfo messageInfo : messages) {

           if (thread.getUniqueId().equals(messageInfo.getUniqueId())) {

                System.out.println(indent + " (" + thread.getUniqueId() + ") " + messageInfo.getSubject());

               break;

           }

       }

       if (thread.getChildMessages().size() != 0) {

            printConversaton(indent += "-", thread.getChildMessages(), messages);

       }

   }

}
```
El código cambia ligeramente si el servidor IMAP admite la capacidad THREAD:

Compruebe si el servidor IMAP admite la extensión THREAD:

```java
 if (client.getThreadSupported())
```
Crea las condiciones de búsqueda adecuadas para un hilo:
```java
 ThreadSearchConditions conditions = new ThreadSearchConditions();

conditions.setAlgorithm(client.getThreadAlgorithms()[0]);

conditions.setUseUId(true);
```

## **Listar mensajes con soporte de paginación**

En situaciones en las que el servidor de correo electrónico contiene una gran cantidad de mensajes en el buzón, a menudo se desea enumerar o recuperar los mensajes con soporte de paginación. API Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) le permite recuperar los mensajes del servidor con soporte de paginación.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// This example shows the paging support of ImapClient for listing messages from the server
// Available in Aspose.Email for Java and onwards
final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    try {
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        // Create some test messages and append these to server's inbox
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157 - " + UUID.randomUUID(),
                    "EMAILNET-35157 Move paging parameters to separate class");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        // List messages from inbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages();
        // Verify the number of messages added
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RETREIVE THE MESSAGES USING PAGING SUPPORT////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();
        PageSettings pageSettings = new PageSettings();
        ImapPageInfo pageInfo = client.listMessagesByPage(itemsPerPage, 0, pageSettings);
        System.out.println(pageInfo.getTotalCount());
        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(itemsPerPage, pageInfo.getNextPage().getPageOffset(), pageSettings);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;

        // foreach to while statements conversion
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Obtener carpetas y leer mensajes de forma recursiva**

En este artículo, la mayoría de los [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) las funciones se utilizan para crear una aplicación que lista todas las carpetas y subcarpetas de forma recursiva de un servidor IMAP. También guarda los mensajes de cada carpeta y subcarpeta en formato MSG en un disco local. En el disco, las carpetas y los mensajes se crean y guardan en la misma estructura jerárquica que en el servidor IMAP. El siguiente fragmento de código muestra cómo obtener la información de los mensajes y las subcarpetas de forma recursiva.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() throws Exception {
    // Crea una instancia del ImapClient class
    ImapClient client = new ImapClient();

    // Specify host, username, password, Port and SecurityOptions for your client
    client.setHost("imap.gmail.com");
    client.setUsername("your.username@gmail.com");
    client.setPassword("your.password");
    client.setPort(993);
    client.setSecurityOptions(SecurityOptions.Auto);
    try {
        // The root folder (which will be created on disk) consists of host and username
        String rootFolder = client.getHost() + "-" + client.getUsername();

        // Create the root folder and List all the folders from IMAP server
        new File(rootFolder).mkdirs();
        ImapFolderInfoCollection folderInfoCollection = client.listFolders();
        for (ImapFolderInfo folderInfo : folderInfoCollection) {
            // Llame al recursive method to read messages and get sub-folders
            listMessagesInFolder(folderInfo, rootFolder, client);
        }
        // Disconnect to the remote IMAP server
        client.dispose();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex);
    }

    System.out.println("Downloaded messages recursively from IMAP server.");
}

/// Recursive method to get messages from folders and sub-folders
private static void listMessagesInFolder(ImapFolderInfo folderInfo, String rootFolder, ImapClient client) {
    // Create the folder in disk (same name as on IMAP server)
    String currentFolder = "data/";
    new File(currentFolder).mkdirs();

    // Read the messages from the current folder, if it is selectable
    if (folderInfo.getSelectable()) {
        // Send status command to get folder info
        ImapFolderInfo folderInfoStatus = client.getFolderInfo(folderInfo.getName());
        System.out.println(folderInfoStatus.getName() + " folder selected. New messages: " + folderInfoStatus.getNewMessageCount() + ", Total messages: "
                + folderInfoStatus.getTotalMessageCount());

        // Select the current folder and List messages
        client.selectFolder(folderInfo.getName());
        ImapMessageInfoCollection msgInfoColl = client.listMessages();
        System.out.println("Listing messages....");
        for (ImapMessageInfo msgInfo : msgInfoColl) {
            // Get subject and other properties of the message
            System.out.println("Subject: " + msgInfo.getSubject());
            System.out.println("Read: " + msgInfo.isRead() + ", Recent: " + msgInfo.getRecent() + ", Answered: " + msgInfo.getAnswered());

            // Get rid of characters like ? and :, which should not be included in a file name and Save the message in MSG format
            String fileName = msgInfo.getSubject().replace(":", " ").replace("?", " ");
            MailMessage msg = client.fetchMessage(msgInfo.getSequenceNumber());
            msg.save(currentFolder + "\\" + fileName + "-" + msgInfo.getSequenceNumber() + ".msg", SaveOptions.getDefaultMsgUnicode());
        }
        System.out.println("============================\n");
    } else {
        System.out.println(folderInfo.getName() + " is not selectable.");
    }

    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ImapFolderInfoCollection folderInfoCollection = client.listFolders(folderInfo.getName());
        for (ImapFolderInfo subfolderInfo : folderInfoCollection) {
            listMessagesInFolder(subfolderInfo, rootFolder, client);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~

## **Obtener el UID o el número de secuencia del mensaje**

La API pública Aspose.Email proporciona las siguientes funciones para obtener la información de identificación del mensaje, como el UID o el número de secuencia, que puede ser necesario al procesar los mensajes recibidos del servidor:

[MailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/) class: representa la información de identificación de un mensaje en un buzón.
- [getSequenceNumber()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getSequenceNumber--) método: obtiene el número de secuencia de un mensaje.
- [getUniqueId()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getUniqueId--) método: obtiene el identificador único de un mensaje.

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase: representa un mensaje de correo electrónico y permite acceder a las propiedades del mensaje, por ejemplo, el asunto, el cuerpo, las direcciones del remitente y del destinatario, etc.
- [getItemId](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getItemId--) método: representa la información de identificación de un mensaje en un buzón.

El ejemplo de código que aparece a continuación muestra cómo obtener y mostrar los detalles de los mensajes de la carpeta «INBOX» de un servidor IMAP mediante el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class:

```java
try (ImapClient client = new ImapClient(imapHost, port, emailAddress, password, securityOption)) {
    ImapMessageInfoCollection msgs = client.listMessages("INBOX");
    List<Integer> seqIds = new ArrayList<>();
    for (ImapMessageInfo msg : msgs) {
        seqIds.add(msg.getSequenceNumber());
    }
    Iterable<MailMessage> msgsViaFetch = client.fetchMessagesBySequences(seqIds);
    for (MailMessage thisMsg : msgsViaFetch) {
        System.out.println("Message ID: " + thisMsg.getItemId().getUniqueId()
                + " SequenceNumber: " + thisMsg.getItemId().getSequenceNumber()
                + " Subject: " + thisMsg.getSubject());
    }
}
```
## **Recuperación de parámetros adicionales como información resumida**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("host.domain.com", "username", "password");
try {
    MailMessage message = new MailMessage("from@domain.com", "to@doman.com", "EMAILNET-38466 - " + UUID.randomUUID().toString(),
            "EMAILNET-38466 Add extra parameters for UID FETCH command");

    // append the message to the server
    String uid = client.appendMessage(message);

    // wait for the message to be appended
    Thread.sleep(5000);

    // Define properties to be fetched from server along with the message
    List<String> messageExtraFields = Arrays.asList("X-GM-MSGID", "X-GM-THRID");

    // retreive the message summary information using it's UID
    ImapMessageInfo messageInfoUID = client.listMessage(uid, messageExtraFields);

    // retreive the message summary information using it's sequence number
    ImapMessageInfo messageInfoSeqNum = client.listMessage(1, messageExtraFields);

    // List messages in general from the server based on the defined properties
    ImapMessageInfoCollection messageInfoCol = client.listMessages(messageExtraFields);

    ImapMessageInfo messageInfoFromList = messageInfoCol.get_Item(0);

    // verify that the parameters are fetched in the summary information
    for (String paramName : messageExtraFields) {
        System.out.println(messageInfoFromList.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoUID.getExtraParameters().containsKey(paramName));
        System.out.println(messageInfoSeqNum.getExtraParameters().containsKey(paramName));
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Obtener información sobre el encabezado de la lista para cancelar la suscripción**

El encabezado List-Unsubscribe contiene la URL para cancelar la suscripción a las listas de correo electrónico, por ejemplo, anuncios, boletines informativos, etc. Para obtener el encabezado List-Unsubscribe, utilice el [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) propiedad del [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) clase. El siguiente ejemplo muestra el uso de [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) propiedad para obtener el encabezado List-Unsubscribe.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
for (ImapMessageInfo imapMessageInfo : messageInfoCol) {
    System.out.println("ListUnsubscribe Header: " + imapMessageInfo.getListUnsubscribe());
}
~~~
