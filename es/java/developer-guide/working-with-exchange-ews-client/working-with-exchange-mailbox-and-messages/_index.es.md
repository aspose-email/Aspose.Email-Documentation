---
title: "Trabajando con el buzón y los mensajes de Exchange: lea el correo electrónico de Exchange Server en Java"
url: /es/java/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Trabajar con el buzón y los mensajes de Exchange"
keywords: "java lee el correo electrónico del servidor Exchange"
---


## **Obtención de información de buzones mediante EWS**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) la clase tiene miembros que se pueden usar para obtener información de buzones de un servidor de Exchange llamando al [IEWSClient.getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getMailboxInfo\(\)) método. Devuelve una instancia de tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo). Obtenga información sobre los buzones de correo de propiedades como [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getInboxUri\(\)) and [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#setDraftsUri\(java.lang.String\)). En este artículo se muestra cómo acceder a la información de los buzones de correo mediante los servicios web de Exchange.

Si desea conectarse al servidor de Exchange mediante los servicios web de Exchange (EWS), utilice el [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) clase. Esta clase usa EWS para conectarse a los elementos de un servidor Exchange y administrarlos. El siguiente fragmento de código de Java muestra cómo obtener información sobre los buzones de correo mediante los servicios web de Exchange.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get mailbox size, exchange mailbox info, Mailbox and Inbox folder URI
System.out.println("Mailbox size: " + client.getMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
System.out.println("Inbox folder URI: " + mailboxInfo.getInboxUri());
System.out.println("Sent Items URI: " + mailboxInfo.getSentItemsUri());
System.out.println("Drafts folder URI: " + mailboxInfo.getDraftsUri());
~~~
## **Envío de mensajes de correo electrónico**
Puede enviar mensajes de correo electrónico mediante un servidor de Exchange con la ayuda de las herramientas de [Aspose.Email.Exchange](#working-with-exchange-mailbox-and-messages). El método viewsClient.send () acepta un [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) instancia como parámetro y envía el correo electrónico. En este artículo se explica cómo enviar mensajes de correo electrónico mediante los servicios web de Exchange.

Aspose.Email proporciona la clase IewsClient para conectarse a Microsoft Exchange Server mediante Exchange Web Services. El siguiente fragmento de código muestra cómo usar EWS para enviar correos electrónicos mediante Microsoft Exchange Server. El siguiente fragmento de código de Java muestra cómo enviar mensajes de correo electrónico mediante EWS.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create instance of type MailMessage
MailMessage msg = new MailMessage();
msg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("recipient@ domain.com "));
msg.setSubject("Sending message from exchange server");
msg.setHtmlBody("<h3>sending message from exchange server</h3>");

// Send the message
client.send(msg);
~~~

## **Obtención de la clase de mensajes**

The [getMessageClass()](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/#getMessageClass--) método del [ExchangeMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/) class obtiene una cadena que representa la clase del mensaje. El ejemplo de código que aparece a continuación muestra cómo obtener la clase de mensaje:

```java
try (IEWSClient client = EWSClient.getEWSClient(uri, credentials))
{
    ExchangeMessageInfoCollection messageInfoCollection = client.listMessagesFromPublicFolder(publicFolder);

    for (ExchangeMessageInfo messageInfo : messageInfoCollection)
    {
        System.out.println("Message Class: " + messageInfo.getMessageClass());
    }
}
```
## **Lectura de correos electrónicos del buzón de otro usuario**
Algunas cuentas de los servidores de Exchange tienen derecho a acceder a varios buzones de correo y algunos usuarios tienen varias cuentas de correo electrónico en el mismo servidor de Exchange. En ambos casos, los usuarios pueden acceder a los buzones de otros usuarios mediante Aspose.Email para Java. Esta API proporciona un mecanismo para acceder a las carpetas y correos electrónicos de otros buzones mediante el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) clase. Esta funcionalidad se puede lograr utilizando el sistema sobrecargado [getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#getMailboxInfo\(\)) método y proporcionar la dirección de correo electrónico del usuario como parámetro.

El siguiente fragmento de código muestra cómo leer correos electrónicos usando [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo("otherUser@domain.com");
~~~
## **Publicar mensajes**
Para obtener una lista de los mensajes de correo electrónico de un buzón de Exchange, llame al [IEWSClient.listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) método. Obtenga la información básica sobre los mensajes, como el asunto, el origen y el identificador del mensaje, mediante el [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) method.
### **Listado de mensajes simples**
Para enumerar los mensajes de un buzón de correo de Exchange:

1. Crea una instancia del [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class.
1. Llame al método ListMessages y cree una colección de mensajes.
1. Recorre la colección y muestra la información del mensaje.

El siguiente fragmento de código Java muestra cómo conectarse a un servidor de Exchange mediante EWS y muestra los mensajes de la carpeta de la bandeja de entrada.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject: " + msgInfo.getSubject());
    System.out.println("From: " + msgInfo.getFrom().toString());
    System.out.println("To: " + msgInfo.getTo().toString());
    System.out.println("Message ID: " + msgInfo.getMessageId());
    System.out.println("Unique URI: " + msgInfo.getUniqueUri());
}
~~~
### **Listar mensajes de diferentes carpetas**
[Los fragmentos de código anteriores](#simple-messages-listing), lista todos los mensajes de la carpeta Bandeja de entrada. También es posible obtener la lista de mensajes de otras carpetas. El [IEWSClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) el método acepta un URI de carpeta como parámetro. Mientras el URI de la carpeta sea válido, puede obtener la lista de mensajes de esa carpeta. Utilice la propiedad IewsClient.getMailboxInfo () .getXXXFolderURI para obtener el URI de las distintas carpetas. El resto del código es el mismo que para obtener una lista de mensajes. El siguiente fragmento de código muestra cómo enumerar los mensajes de diferentes carpetas mediante EWS.


~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get folder URI
String strFolderURI = "";
strFolderURI = client.getMailboxInfo().getInboxUri();
strFolderURI = client.getMailboxInfo().getDeletedItemsUri();
strFolderURI = client.getMailboxInfo().getDraftsUri();
strFolderURI = client.getMailboxInfo().getSentItemsUri();

// Get list of messages from the specified folder
ExchangeMessageInfoCollection msgCollection = client.listMessages(strFolderURI);
~~~
### **Listar mensajes con soporte de paginación**
El siguiente fragmento de código Java muestra cómo obtener una lista de mensajes con soporte de paginación.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
try {
    try {
        // Create some test messages to be added to server for retrieval later
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157_1 - " + UUID.randomUUID().toString(),
                    "EMAILNET-35157 Move paging parameters to separate class");
            client.appendMessage(client.getMailboxInfo().getInboxUri(), message);
        }
        // Verfiy that the messages have been added to the server
        ExchangeMessageInfoCollection totalMessageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RETREIVING THE MESSAGES USING PAGING SUPPORT ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
        // Total Pages Count
        System.out.println(pageInfo.getTotalCount());

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage, pageInfo.getPageOffset() + 1);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // foreach to while statements conversion
        for (ExchangeMessagePageInfo pageCol : pages) {
            retrievedItems += pageCol.getItems().size();
        }
        // Verify total message count using paging
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    client.dispose();
}
~~~
### **Obtener información sobre el tipo de mensaje de ExchangeMessageInfo**


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.listMessages(client.getMailboxInfo().getDeletedItemsUri());
System.out.println(list.get_Item(0).getMessageInfoType()); // MessageInfoType
~~~
## **Guardar mensajes**
En este artículo se muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en el disco en formatos EML y MSG:

- Guardar como EML en el disco.
- Guardar en la secuencia de memoria.
- Guardar como MSG.
### **Guardar mensajes en EML**
Para obtener mensajes y guardarlos en formato EML:

1. Crea una instancia de la clase IewsClient.
1. Proporcione la URI del buzón, el nombre de usuario, la contraseña y el dominio.
1. Llame al método iewsClient.listMessages () para obtener una instancia de la colección ExchangeMessagesInfoCollection.
1. Recorre la colección ExchangeMessagesInfoCollection para obtener el URI único de cada mensaje.
1. Llame al método IewsClient.saveMessage () y pase el URI único como parámetro.
1. Proporcione un método saveMessage () con una ruta al lugar donde desea guardar el archivo.

El siguiente fragmento de código muestra cómo usar EWS para conectarse al servidor Exchange y guardar los mensajes como archivos EML.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now save the message in disk
    client.saveMessage(strMessageURI, dataDir + msgInfo.getMessageId() + "out.eml");
}
~~~
### **Guardar mensajes en un flujo de memoria**
En lugar de guardar los archivos EML en el disco, es posible guardarlos en una secuencia de memoria. Esto es útil cuando quieres guardar la transmisión en alguna ubicación de almacenamiento, como una base de datos. Una vez guardada la transmisión en una base de datos, puede volver a cargar el archivo EML en [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) clase. El siguiente fragmento de código muestra cómo guardar los mensajes de un buzón de Exchange Server en un flujo de memoria mediante EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now save the message in memory stream
    ByteArrayOutputStream stream = new ByteArrayOutputStream();
    client.saveMessage(strMessageURI, stream);
}
~~~
### **Guardar mensajes en formato MSG**
The [IEWSClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#saveMessage\(java.lang.String,%20java.lang.String\)) El método puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llame al [IEWSClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchMessage\(java.lang.String\)) método que devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) clase. Entonces llama al [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.lang.String\)) método para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en formato MSG mediante EWS.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

int count = 0;
// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now get the message details using FetchMessage() and Save message as Msg
    MailMessage message = client.fetchMessage(strMessageURI);
    message.save(dataDir + (count++) + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~
## **Obtener ExchangeMessageInfo del URI del mensaje**
Un mensaje de correo electrónico está representado por su identificador único, URI, y forma parte integral del [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) objeto. En caso de que solo esté disponible el URI del mensaje, entonces [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) el objeto también se puede recuperar utilizando esta información disponible. La versión de sobrecarga de [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.Iterable\)) toma una lista de identificaciones para usar [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection). El siguiente fragmento de código muestra cómo obtener [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) del URI del mensaje.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<String> ids = new ArrayList<String>();
List<MailMessage> messages = new ArrayList<MailMessage>();

for (int i = 0; i < 5; i++) {
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + UUID.randomUUID().toString(),
            "EMAILNET-35033 Messages saved from Sent Items folder doesn't contain 'To' field");
    messages.add(message);
    String uri = client.appendMessage(message);
    ids.add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(ids);

for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) messageInfoCol) {
    // Do something ...
    System.out.println(messageInfo.getUniqueUri());
}
~~~
## **Obtener mensajes de un buzón de correo de Exchange Server**
Al enumerar los mensajes de un servidor Exchange, se utilizó el [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) método para obtener una lista de mensajes de un buzón de Exchange Server. El [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) El método obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, el origen y el destino. Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona el método iewsClient.fetchMessage (). Este método acepta el URI del mensaje como parámetro y devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) clase. El [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) La clase luego proporciona detalles del mensaje como el cuerpo, los encabezados y los archivos adjuntos. Obtenga más información sobre [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) API, o descubre cómo administrar los correos electrónicos con la [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) clase. Para obtener mensajes del buzón de Exchange Server:

1. Crea una instancia de tipo iewsClient.
1. Especifique el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llame a ListMessages para obtener la colección ExchangeMessageInfoCollection.
1. Recorra la colección ExchangeMessageInfoCollection para obtener los valores ExchangeMessageInfo.uniqueURI.
1. Llame a IewsClient.fetchMessage () y pase ExchangeMessageInfo.uniqueURI como parámetro.

El siguiente fragmento de código muestra cómo se conecta al buzón de correo de Exchange Server y obtiene todos los mensajes mediante EWS.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Now get the message details using FetchMessage()
    MailMessage msg = client.fetchMessage(strMessageURI);

    for (Attachment att : (Iterable<Attachment>) msg.getAttachments()) {
        System.out.println("Attachment Name: " + att.getName());
    }
}
~~~

### **Uso del método fetchItem para obtener un mensaje**

{{% alert color="primary" %}}

Tenga en cuenta que el [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) el método devuelve el mensaje sin archivos adjuntos. Para buscar mensajes con archivos adjuntos, utilice el [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)) método, descrito en la sección siguiente.

{{% /alert %}}

The [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\))  el método es más preferido si desea obtener un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) y funcionan con las propiedades de MAPI. También puede utilizar este método para recuperar cualquier elemento de Outlook, como un contacto, una cita, una tarea, etc.

```java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to get Message URI
for (ExchangeMessageInfo msgInfo : msgCollection)
{
    // Now get the message using FetchItem()
    MapiMessage msg = client.fetchItem(msgInfo.getUniqueUri());

    // If necessary, you can cast the MapiMessage to the proper item type to simplify working with its properties.
    MapiContact contact = (MapiContact) msg.toMapiMessageItem();
}
```

## **Tamaño del mensaje de captura previa**
Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de obtener el mensaje completo del servidor. En el caso de la API Aspose.Email, la información resumida recuperada del servidor Exchange está representada por [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) clase. Proporciona la misma función de recuperar el tamaño del mensaje mediante la propiedad Size. Para recuperar el tamaño del mensaje, se utiliza la llamada estándar a ListMessages de IewsClient, que recupera la colección de [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). En el siguiente fragmento de código se muestra cómo mostrar el tamaño de los mensajes mediante el [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) class.



~~~Java
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Loop through the collection to display the basic information
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject: " + msgInfo.getSubject());
    System.out.println("From: " + msgInfo.getFrom().toString());
    System.out.println("To: " + msgInfo.getTo().toString());
    System.out.println("Message Size: " + msgInfo.getSize());
    System.out.println("==================================");
}
~~~
## **Descargar mensajes de forma recursiva**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient)’s [listSubFolders()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listSubFolders\(com.aspose.email.ExchangeFolderInfo\)) El método se puede utilizar para obtener mensajes de carpetas y subcarpetas de un buzón de Exchange Server de forma recursiva. Esto requiere Exchange Server 2007 o superior, ya que utiliza EWS. En el siguiente fragmento de código se muestra cómo descargar todo el buzón (carpetas y subcarpetas) de un servidor Exchange. La estructura de carpetas se crea localmente y todos los mensajes se descargan.



~~~Java
public static void run() {
    try {
        downloadAllMessages();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void downloadAllMessages() {
    try {
        String rootFolder = domain + "-" + username;
        new File(rootFolder).mkdirs();
        String inboxFolder = rootFolder + "\\Inbox";
        new File(inboxFolder).mkdirs();

        System.out.println("Downloading all messages from Inbox....");
        // Create instance of IEWSClient class by giving credentials
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("Mailbox URI: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Call the recursive method to read messages and get sub-folders
            listMessagesInFolder(client, folderInfo, rootFolder);
        }

        System.out.println("All messages downloaded.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

// Recursive method to get messages from folders and sub-folders
private static void listMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, String rootFolder) {
    // Create the folder in disk (same name as on IMAP server)
    String currentFolder = rootFolder + "\\" + folderInfo.getDisplayName();
    new File(currentFolder).mkdirs();

    // List messages
    ExchangeMessageInfoCollection msgInfoColl = client.listMessages(folderInfo.getUri());
    System.out.println("Listing messages....");
    int i = 0;
    for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
        // Get subject and other properties of the message
        System.out.println("Subject: " + msgInfo.getSubject());

        // Get rid of characters like ? and :, which should not be included in a file name
        String fileName = msgInfo.getSubject().replace("?", " ").replace(":", " ");

        MailMessage msg = client.fetchMessage(msgInfo.getUniqueUri());
        msg.save(dataDir + "\\" + fileName + "-" + i + ".msg");

        i++;
    }
    System.out.println("============================\n");
    try {
        // If this folder has sub-folders, call this method recursively to get messages
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Descargar mensajes de carpetas públicas**
Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de su aplicación, utilice Aspose.Email [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase para conectarse al servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. El siguiente fragmento de código muestra cómo leer todas las carpetas y subcarpetas públicas, y muestra y descarga todos los mensajes que se encuentran en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.



~~~Java
public static void run() {
    try {
        readPublicFolders();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

private static void readPublicFolders() {
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.listPublicFolders();
    for (ExchangeFolderInfo publicFolder : (Iterable<ExchangeFolderInfo>) folders) {
        System.out.println("Name: " + publicFolder.getDisplayName());
        System.out.println("Subfolders count: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Folder Name: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Call this method recursively for any subfolders
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Mensajes en movimiento**
Puede mover los mensajes de correo electrónico de una carpeta a otra con la ayuda del [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class [move](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#moveItem\(java.lang.String,%20java.lang.String\)) método. Toma los parámetros:

- El URI único del mensaje que se va a mover.
- El URI único de la carpeta de destino.
### **Mover mensajes entre carpetas**
El siguiente fragmento de código muestra cómo mover un mensaje de un buzón de la carpeta Bandeja de entrada a una carpeta denominada Procesado. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa algunos de los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen la condición dada a la carpeta procesada.

~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// List all messages from Inbox folder
System.out.println("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Move message to "Processed" folder, after processing certain messages based on some criteria
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("process this message")) {
        client.moveItem(mailboxInfo.getDeletedItemsUri(), msgInfo.getUniqueUri()); // EWS
        System.out.println("Message moved...." + msgInfo.getSubject());
    } else {
        // Do something else
    }
}
~~~
## **Eliminar mensajes**
Puede eliminar los mensajes de correo electrónico de una carpeta con la ayuda del [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) método. Toma el URI único del mensaje como parámetro.

El siguiente fragmento de código muestra cómo eliminar un mensaje de la carpeta Bandeja de entrada. Para este ejemplo, el código:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimina el mensaje.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// List all messages from Inbox folder
System.out.println("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Delete message based on some criteria
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("delete") == true) {
        client.deleteItem(msgInfo.getUniqueUri(), DeletionOptions.getDeletePermanently()); // EWS
        System.out.println("Message deleted...." + msgInfo.getSubject());
    } else {
        // Do something else
    }
}
~~~
## **Copiar mensajes**
La API Aspose.Email permite copiar un mensaje de una carpeta a otra mediante el [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)) método. La versión sobrecargada de este método devuelve el URI único del mensaje copiado, como se muestra en este artículo.
### **Copiar un mensaje a otra carpeta**
El siguiente fragmento de código muestra cómo copiar un mensaje a otra carpeta.



~~~Java
try {
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
