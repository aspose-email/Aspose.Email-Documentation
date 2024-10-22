---
title: "Trabajando con Mensajes desde el Servidor IMAP"
url: /es/java/trabajando-con-mensajes-desde-el-servidor-imap/
weight: 20
type: docs
---

## **Listado de IDs de Mensaje MIME desde el Servidor**

[ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/) proporciona el MIME [MessageId](https://reference.aspose.com/email/java/com.aspose.email/messageinfobase/#getMessageId--) para la identificación de mensajes sin necesidad de extraer el mensaje completo. El siguiente fragmento de código muestra cómo listar el messageId MIME.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient client = new ImapClient();
client.setHost("dominio.com");
client.setUsername("usuario");
client.setPassword("contraseña");

try {
    ImapMessageInfoCollection messageInfoCol = client.listMessages("Bandeja de entrada");
    for (ImapMessageInfo info : messageInfoCol) {
        // Mostrar ID de Mensaje MIME
        System.out.println("ID de Mensaje = " + info.getMessageId());
    }
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~ 

## **Listado de Mensajes desde el Servidor**

Aspose.Email proporciona una variante sobrecargada de 2 miembros de [listMessages()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) para recuperar un número específico de mensajes basado en una consulta. El siguiente fragmento de código muestra cómo listar mensajes.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// Crear un imapclient con host, usuario y contraseña
ImapClient client = new ImapClient("localhost", "usuario", "contraseña");

// Seleccionar la carpeta de la bandeja de entrada y obtener la colección de información de mensajes
ImapQueryBuilder builder = new ImapQueryBuilder();
MailQuery query = builder
        .or(builder.or(builder.or(builder.or(builder.getSubject().contains(" (1) "), builder.getSubject().contains(" (2) ")), builder.getSubject().contains(" (3) ")),
                builder.getSubject().contains(" (4) ")), builder.getSubject().contains(" (5) "));
ImapMessageInfoCollection messageInfoCol4 = client.listMessages(query, 4);
System.out.println((messageInfoCol4.size() == 4) ? "Éxito" : "Fallo");
~~~ 

## **Listado de Mensajes desde el Servidor Recursivamente**

El protocolo IMAP admite el listado de mensajes recursivamente desde una carpeta de correo. Esto también ayuda a listar mensajes desde subcarpetas de una carpeta. El siguiente fragmento de código muestra cómo listar mensajes recursivamente.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// Crear un imapclient con host, usuario y contraseña
ImapClient client = new ImapClient();
client.setHost("dominio.com");
client.setUsername("usuario");
client.setPassword("contraseña");
client.selectFolder("Bandeja de entrada");
ImapMessageInfoCollection msgsColl = client.listMessages(true);
System.out.println("Total de Mensajes: " + msgsColl.size());
~~~ 

## **Listado de Mensajes con MultiConexión**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona una propiedad [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setUseMultiConnection-int-) que puede usarse para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se utilizarán durante el modo de multiconexión utilizando [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setConnectionsQuantity-int-). El siguiente fragmento de código demuestra el uso del modo de multiconexión para listar mensajes y compara su rendimiento con el modo de conexión única.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USUARIO>");
imapClient.setPassword("<CONTRASEÑA>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

imapClient.selectFolder("Bandeja de entrada");
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
System.out.println("Relación de Rendimiento: " + performanceRelation);
~~~ 
{{% alert color="primary" %}} 

Tenga en cuenta que el uso del modo de multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}} 

## **Obtener Mensajes en orden descendente**

Aspose.Email proporciona el método [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) que lista mensajes con soporte para paginación. Algunos sobrecargas de [ImapClient.listMessagesByPage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessagesByPage-com.aspose.email.IConnection-com.aspose.email.PageInfo-) aceptan [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) como parámetro. [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) proporciona una propiedad [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) que, al establecerla en **false**, devuelve correos electrónicos en orden descendente.

El siguiente ejemplo de código demuestra el uso de la propiedad [AscendingSorting](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/#getAscendingSorting--) de la clase [PageSettings](https://reference.aspose.com/email/java/com.aspose.email/pagesettings/) para cambiar el orden de los correos electrónicos.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USUARIO>");
imapClient.setPassword("<CONTRASEÑA>");
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

## **Buscar Mensajes desde el Servidor y Guardar en disco**

La clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) puede buscar mensajes desde un servidor IMAP y guardar los mensajes en formato EML en un disco local. Se requieren los siguientes pasos para guardar los mensajes en el disco:

1. Crear una instancia de la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Especificar un nombre de host, puerto, nombre de usuario y contraseña en el [constructor](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#ImapClient\(java.lang.String,%20int,%20java.lang.String,%20java.lang.String\)) de ImapClient.
1. Seleccionar la carpeta utilizando el método [selectFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#selectFolder-com.aspose.email.IConnection-java.lang.String-).
1. Llamar al método [listMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listMessages--) para obtener el objeto [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/).
1. Iterar a través de la colección [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/), llamar al método [saveMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#saveMessage-com.aspose.email.IConnection-int-java.io.OutputStream-) y proporcionar la ruta de salida y el nombre del archivo.

El siguiente fragmento de código muestra cómo buscar mensajes de correo electrónico desde un servidor y guardarlos.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// Seleccionar la carpeta de la bandeja de entrada y obtener la colección de información de mensajes
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Descargar cada mensaje
for (int i = 0; i < list.size(); i++) {
    // Guardar el archivo EML localmente
    client.saveMessage(list.get_Item(i).getUniqueId(), dataDir + list.get_Item(i).getUniqueId() + ".eml");
}
~~~ 

## **Guardar Mensajes en Formato MSG**

[En el ejemplo anterior](#fetch-messages-from-server-and-save-to-disc), los correos electrónicos se guardan en formato EML. Para guardar correos electrónicos en formato MSG, se debe llamar al método [ImapClient.fetchMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessage-com.aspose.email.IConnection-int-). Devuelve el mensaje en una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). El método [MailMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) puede ser llamado para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo guardar mensajes en formato MSG.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "data/";

// Crear un imapclient con host, usuario y contraseña
ImapClient client = new ImapClient("localhost", "usuario", "contraseña");

// Seleccionar la carpeta de la bandeja de entrada y Obtener la colección de información de mensajes
client.selectFolder(ImapFolderInfo.IN_BOX);
ImapMessageInfoCollection list = client.listMessages();

// Descargar cada mensaje
for (int i = 0; i < list.size(); i++) {
    // Guardar el mensaje en formato MSG
    MailMessage message = client.fetchMessage(list.get_Item(i).getUniqueId());
    message.save(dataDir + list.get_Item(i).getUniqueId() + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~ 

## **Grupo de Búsqueda de Mensajes**

[ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona un método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) que acepta iterable de Números de Secuencia o ID Único y devuelve una lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). El siguiente fragmento de código demuestra el uso del método [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) para buscar mensajes por Números de Secuencia y ID Único.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USUARIO>");
imapClient.setPassword("<CONTRASEÑA>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
System.out.println("Contador de ListMessages: " + messageInfoCol.size());

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

## **Hilos de Correo/Organizar Correos en Conversaciones**

Aspose.Email hace posible agrupar todos los mensajes de reenvío, respuestas y respuesta a todos relacionados con la misma conversación de manera jerárquica. Básicamente, el protocolo IMAP puede admitir la capacidad THREAD definida en RFC-5256. Además, hay otra extensión IMAP proporcionada por Gmail y descrita como X-GM-EXT-1.

Las siguientes características de hilo de correo están disponibles para uso:

- [getMessageThreads](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getMessageThreads-com.aspose.email.BaseSearchConditions-) método - Recibe hilos de mensajes por [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
- boolean [getGmExt1Supported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getGmExt1Supported--) - Obtiene información sobre si la extensión X-GM-EXT-1 de Gmail es compatible.
- boolean [getThreadSupported](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadSupported--) - Obtiene información sobre si la extensión THREAD es compatible.
- String[] [getThreadAlgorithms](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getThreadAlgorithms--) - Obtiene algoritmos THREAD compatibles.

Los siguientes ejemplos de código muestran el uso de estas características para obtener los hilos de correo de Gmail:

```java
  ImapClient client = new ImapClient("imap.gmail.com", 993, "usuario", "contraseña", SecurityOptions.SSLImplicit);

try {

    client.selectFolder(ImapFolderInfo.IN_BOX);

   // obtener una lista de mensajes que agruparemos por conversación

   ImapMessageInfoCollection messages = client.listMessages();

   // asegurarse de que el servidor IMAP admite la extensión X-GM-EXT-1

   if (client.getGmExt1Supported()) {

       // obtener el unique conversationId para nuestro ejemplo

       Set<String> conversationIds = new HashSet<String>();

       for (ImapMessageInfo messageInfo : messages) {

           if (messageInfo.getConversationId() != null)

                conversationIds.add(messageInfo.getConversationId());

       }

       for (String conversationId : conversationIds) {

           // crear las condiciones de búsqueda necesarias para un hilo

           XGMThreadSearchConditions conditions = new XGMThreadSearchConditions();

            conditions.setConversationId(conversationId);

            conditions.setUseUId(true);

           // obtener resultados

           List<MessageThreadResult> conversation = client.getMessageThreads(conditions);

           // imprimir la conversación de correo de manera jerárquica

           printConversaton("", conversation, messages);

            System.out.println("--------------------");

       }

   }

} finally {

    client.dispose();

}

/**

 * <p>

 * Imprime la conversación de correo de manera jerárquica

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

Verifique si el servidor IMAP admite la extensión THREAD:

```java
 if (client.getThreadSupported())
```
Cree las condiciones de búsqueda adecuadas para un hilo:
```java
 ThreadSearchConditions conditions = new ThreadSearchConditions();

conditions.setAlgorithm(client.getThreadAlgorithms()[0]);

conditions.setUseUId(true);
``` 

## **Listado de Mensajes con Soporte de Paginación**

En escenarios donde el servidor de correo contiene una gran cantidad de mensajes en la bandeja de entrada, a menudo se desea listar o recuperar los mensajes con soporte de paginación. La API de Aspose.Email [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) le permite recuperar los mensajes del servidor con soporte de paginación.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
// Este ejemplo muestra el soporte de paginación de ImapClient para listar mensajes desde el servidor
// Disponible en Aspose.Email para Java y versiones posteriores
final ImapClient client = new ImapClient("host.dominio.com", 993, "usuario", "contraseña");
try {
    try {
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        // Crear algunos mensajes de prueba y agregar estos a la bandeja de entrada del servidor
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@dominio.com", "to@dominio.com", "EMAILNET-35157 - " + UUID.randomUUID(),
                    "EMAILNET-35157 Mover parámetros de paginación a una clase separada");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        // Listar mensajes de la bandeja de entrada
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages();
        // Verificar el número de mensajes añadidos
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RECUPERAR LOS MENSAJES USANDO SOPORTE DE PAGINACIÓN ////////////////////////

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

        // conversión de declaraciones foreach a while
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

## **Obtención de Carpetas y Lectura de Mensajes Recursivamente**

En este artículo, se utilizan la mayoría de las características de [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) para crear una aplicación que lista todas las carpetas y subcarpetas recursivamente desde un servidor IMAP. También guarda los mensajes en cada carpeta y subcarpeta en formato MSG en un disco local. En el disco, las carpetas y mensajes se crean y guardan en la misma estructura jerárquica que en el servidor IMAP. El siguiente fragmento de código muestra cómo obtener los mensajes y la información de subcarpetas de manera recursiva.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() throws Exception {
    // Crear una instancia de la clase ImapClient
    ImapClient client = new ImapClient();

    // Especificar host, nombre de usuario, contraseña, puerto y opciones de seguridad para su cliente
    client.setHost("imap.gmail.com");
    client.setUsername("tu.usuario@gmail.com");
    client.setPassword("tu.contraseña");
    client.setPort(993);
    client.setSecurityOptions(SecurityOptions.Auto);
    try {
        // La carpeta raíz (que se creará en el disco) consiste en el host y el nombre de usuario
        String rootFolder = client.getHost() + "-" + client.getUsername();

        // Crear la carpeta raíz y listar todas las carpetas desde el servidor IMAP
        new File(rootFolder).mkdirs();
        ImapFolderInfoCollection folderInfoCollection = client.listFolders();
        for (ImapFolderInfo folderInfo : folderInfoCollection) {
            // Llamar al método recursivo para leer mensajes y obtener subcarpetas
            listMessagesInFolder(folderInfo, rootFolder, client);
        }
        // Desconectar del servidor IMAP remoto
        client.dispose();
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex);
    }

    System.out.println("Mensajes descargados recursivamente desde el servidor IMAP.");
}

/// Método recursivo para obtener mensajes de carpetas y subcarpetas
private static void listMessagesInFolder(ImapFolderInfo folderInfo, String rootFolder, ImapClient client) {
    // Crear la carpeta en el disco (mismo nombre que en el servidor IMAP)
    String currentFolder = "data/";
    new File(currentFolder).mkdirs();

    // Leer los mensajes de la carpeta actual, si es seleccionable
    if (folderInfo.getSelectable()) {
        // Enviar comando de estado para obtener información de la carpeta
        ImapFolderInfo folderInfoStatus = client.getFolderInfo(folderInfo.getName());
        System.out.println(folderInfoStatus.getName() + " carpeta seleccionada. Nuevos mensajes: " + folderInfoStatus.getNewMessageCount() + ", Total de mensajes: "
                + folderInfoStatus.getTotalMessageCount());

        // Seleccionar la carpeta actual y listar mensajes
        client.selectFolder(folderInfo.getName());
        ImapMessageInfoCollection msgInfoColl = client.listMessages();
        System.out.println("Listando mensajes....");
        for (ImapMessageInfo msgInfo : msgInfoColl) {
            // Obtener el asunto y otras propiedades del mensaje
            System.out.println("Asunto: " + msgInfo.getSubject());
            System.out.println("Leído: " + msgInfo.isRead() + ", Reciente: " + msgInfo.getRecent() + ", Contestada: " + msgInfo.getAnswered());

            // Deshacerse de caracteres como ? y :, que no deben incluirse en un nombre de archivo y guardar el mensaje en formato MSG
            String fileName = msgInfo.getSubject().replace(":", " ").replace("?", " ");
            MailMessage msg = client.fetchMessage(msgInfo.getSequenceNumber());
            msg.save(currentFolder + "\\" + fileName + "-" + msgInfo.getSequenceNumber() + ".msg", SaveOptions.getDefaultMsgUnicode());
        }
        System.out.println("============================\n");
    } else {
        System.out.println(folderInfo.getName() + " no es seleccionable.");
    }

    try {
        // Si esta carpeta tiene subcarpetas, llamar a este método recursivamente para obtener mensajes
        ImapFolderInfoCollection folderInfoCollection = client.listFolders(folderInfo.getName());
        for (ImapFolderInfo subfolderInfo : folderInfoCollection) {
            listMessagesInFolder(subfolderInfo, rootFolder, client);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~ 

## **Obtener UID de Mensaje o Número de Secuencia**

La API pública de Aspose.Email proporciona las siguientes características para obtener la información de identificación del mensaje, como UID o número de secuencia, que podría ser necesaria al procesar mensajes recibidos del servidor:

[MailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/) clase - Representa la información de identificación sobre un mensaje en un buzón.
- [getSequenceNumber()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getSequenceNumber--) método - Obtiene el número de secuencia de un mensaje.
- [getUniqueId()](https://reference.aspose.com/email/java/com.aspose.email/mailboxinfo/#getUniqueId--) método - Obtiene el id único de un mensaje.

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase - Representa un mensaje de correo electrónico y permite acceder a las propiedades del mensaje, ex. asunto, cuerpo, remitente y direcciones de los destinatarios, etc.
- [getItemId](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getItemId--) método - Representa la información de identificación sobre un mensaje en un buzón.

El siguiente ejemplo de código demuestra cómo buscar y mostrar los detalles de los mensajes desde la carpeta "BANDEJA DE ENTRADA" en un servidor IMAP utilizando la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
try (ImapClient client = new ImapClient(imapHost, port, emailAddress, password, securityOption)) {
    ImapMessageInfoCollection msgs = client.listMessages("BANDEJA DE ENTRADA");
    List<Integer> seqIds = new ArrayList<>();
    for (ImapMessageInfo msg : msgs) {
        seqIds.add(msg.getSequenceNumber());
    }
    Iterable<MailMessage> msgsViaFetch = client.fetchMessagesBySequences(seqIds);
    for (MailMessage thisMsg : msgsViaFetch) {
        System.out.println("ID de Mensaje: " + thisMsg.getItemId().getUniqueId()
                + " Número de Secuencia: " + thisMsg.getItemId().getSequenceNumber()
                + " Asunto: " + thisMsg.getSubject());
    }
}
```
## **Recuperando Parámetros Adicionales como Información Resumida**

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("host.dominio.com", "usuario", "contraseña");
try {
    MailMessage message = new MailMessage("from@dominio.com", "to@doman.com", "EMAILNET-38466 - " + UUID.randomUUID().toString(),
            "EMAILNET-38466 Agregar parámetros adicionales para el comando UID FETCH");

    // agregar el mensaje al servidor
    String uid = client.appendMessage(message);

    // esperar a que el mensaje sea agregado
    Thread.sleep(5000);

    // Definir propiedades que se obtendrán del servidor junto con el mensaje
    List<String> messageExtraFields = Arrays.asList("X-GM-MSGID", "X-GM-THRID");

    // recuperar la información de resumen del mensaje usando su UID
    ImapMessageInfo messageInfoUID = client.listMessage(uid, messageExtraFields);

    // recuperar la información de resumen del mensaje usando su número de secuencia
    ImapMessageInfo messageInfoSeqNum = client.listMessage(1, messageExtraFields);

    // Listar mensajes en general desde el servidor basado en las propiedades definidas
    ImapMessageInfoCollection messageInfoCol = client.listMessages(messageExtraFields);

    ImapMessageInfo messageInfoFromList = messageInfoCol.get_Item(0);

    // verificar que los parámetros se hayan recuperado en la información de resumen
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

## **Obteniendo Información del Encabezado List-Unsubscribe**

El encabezado List-Unsubscribe contiene la URL para darse de baja de listas de correo electrónico, como anuncios, boletines, etc. Para obtener el encabezado List-Unsubscribe, use la propiedad [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) de la clase [ImapMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/). El siguiente ejemplo muestra el uso de la propiedad [listUnsubscribe](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfo/#getListUnsubscribe--) para obtener el encabezado List-Unsubscribe.

~~~Java
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USUARIO>");
imapClient.setPassword("<CONTRASEÑA>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMessageInfoCollection messageInfoCol = imapClient.listMessages();
for (ImapMessageInfo imapMessageInfo : messageInfoCol) {
    System.out.println("Encabezado ListUnsubscribe: " + imapMessageInfo.getListUnsubscribe());
}
~~~