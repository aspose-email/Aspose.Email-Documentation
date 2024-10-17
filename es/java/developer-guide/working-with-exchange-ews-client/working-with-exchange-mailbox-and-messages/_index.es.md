---
title: "Trabajar con Buzones de Exchange y Mensajes - Leer Correo Electrónico desde el Servidor de Exchange en Java"
url: /es/java/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Trabajar con Buzones de Exchange y Mensajes"
keywords: "java leer correo electrónico desde el servidor de exchange"
---


## **Obteniendo Información del Buzón Usando EWS**
La clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) tiene miembros que se pueden usar para obtener información del buzón de un Servidor Exchange mediante la llamada al método [IEWSClient.getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#getMailboxInfo\(\)). Devuelve una instancia del tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo). Obtenga información del buzón a partir de propiedades como [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getInboxUri\(\)) y [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#setDraftsUri\(java.lang.String\)). Este artículo muestra cómo acceder a la información del buzón utilizando Servicios Web de Exchange.

Si desea conectarse al Servidor de Exchange utilizando Servicios Web de Exchange (EWS), use la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient). Esta clase usa EWS para conectarse y administrar elementos en un Servidor Exchange. El siguiente fragmento de código Java le muestra cómo obtener información del buzón usando los servicios web de exchange.



~~~Java
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener tamaño del buzón, información del buzón de exchange, URI del buzón y carpeta de entrada
System.out.println("Tamaño del buzón: " + client.getMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
System.out.println("URI del buzón: " + mailboxInfo.getMailboxUri());
System.out.println("URI de la carpeta de entrada: " + mailboxInfo.getInboxUri());
System.out.println("URI de elementos enviados: " + mailboxInfo.getSentItemsUri());
System.out.println("URI de la carpeta de borradores: " + mailboxInfo.getDraftsUri());
~~~
## **Enviando Mensajes de Correo Electrónico**
Puede enviar mensajes de correo electrónico utilizando un Servidor Exchange con la ayuda de las herramientas en [Aspose.Email.Exchange](#working-with-exchange-mailbox-and-messages). El método IEWSClient.Send() acepta una instancia de [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) como parámetro y envía el correo electrónico. Este artículo explica cómo enviar mensajes de correo electrónico utilizando Servicios Web de Exchange.

Aspose.Email proporciona la clase IEWSClient para conectarse al Servidor Microsoft Exchange usando Servicios Web de Exchange. El siguiente fragmento de código muestra cómo usar EWS para enviar correos electrónicos utilizando el Servidor Microsoft Exchange. El siguiente fragmento de código Java muestra cómo enviar mensajes de correo electrónico utilizando EWS.



~~~Java
// Crear instancia de la clase IEWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Crear instancia del tipo MailMessage
MailMessage msg = new MailMessage();
msg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("recipient@ domain.com "));
msg.setSubject("Enviando mensaje desde el servidor de exchange");
msg.setHtmlBody("<h3>enviando mensaje desde el servidor de exchange</h3>");

// Enviar el mensaje
client.send(msg);
~~~

## **Obteniendo la Clase de Mensaje**

El método [getMessageClass()](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/#getMessageClass--) de la clase [ExchangeMessageInfo](https://reference.aspose.com/email/java/com.aspose.email/exchangemessageinfo/) obtiene una cadena que representa la clase para el mensaje. El siguiente ejemplo de código muestra cómo obtener la clase de mensaje:

```java
try (IEWSClient client = EWSClient.getEWSClient(uri, credentials))
{
    ExchangeMessageInfoCollection messageInfoCollection = client.listMessagesFromPublicFolder(publicFolder);

    for (ExchangeMessageInfo messageInfo : messageInfoCollection)
    {
        System.out.println("Clase del Mensaje: " + messageInfo.getMessageClass());
    }
}
```
## **Leyendo Correos Electrónicos del Buzón de Otro Usuario**
Algunas cuentas en Servidores Exchange tienen el derecho de acceder a múltiples buzones, y algunos usuarios tienen múltiples cuentas de correo electrónico en el mismo Servidor Exchange. En ambos casos, los usuarios pueden acceder a los buzones de otros usuarios utilizando Aspose.Email para Java. Esta API proporciona un mecanismo para acceder a carpetas y correos electrónicos de otros buzones usando la clase [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Esta funcionalidad se puede lograr utilizando el método sobrecargado [getMailboxInfo()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#getMailboxInfo\(\)) y proporcionando la dirección de correo electrónico del usuario como parámetro.

El siguiente fragmento de código le muestra cómo leer correos electrónicos usando la clase [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).



~~~Java
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener información del buzón de otro cuenta de email
ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo("otherUser@domain.com");
~~~
## **Listando Mensajes**
Una lista de los mensajes de correo electrónico en un buzón de Exchange se puede obtener llamando al método [IEWSClient.listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)). Obtenga la información básica sobre los mensajes, como el asunto, de, para y ID del mensaje, utilizando el método [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)).
### **Listando Mensajes Simples**
Para listar los mensajes en un buzón de Exchange:

1. Cree una instancia de la clase [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient).
1. Llame al método listMessages y cree una colección de mensajes.
1. Recorra la colección y muestre la información del mensaje.

El siguiente fragmento de código Java le muestra cómo conectarse a un servidor de exchange utilizando EWS y listar mensajes de la carpeta de entrada.



~~~Java
// Crear instancia de la clase ExchangeWebServiceClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Llamar al método ListMessages para listar la información de los mensajes desde la carpeta de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Recorrer la colección para mostrar la información básica
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Asunto: " + msgInfo.getSubject());
    System.out.println("De: " + msgInfo.getFrom().toString());
    System.out.println("Para: " + msgInfo.getTo().toString());
    System.out.println("ID del Mensaje: " + msgInfo.getMessageId());
    System.out.println("URI Única: " + msgInfo.getUniqueUri());
}
~~~
### **Listando Mensajes desde Diferentes Carpetas**
[Los fragmentos de código anteriores](#simple-messages-listing) listan todos los mensajes en la carpeta de entrada. También es posible obtener la lista de mensajes de otras carpetas. El método [IEWSClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) acepta una URI de carpeta como parámetro. Siempre que la URI de la carpeta sea válida, puede obtener la lista de mensajes de esa carpeta. Use la propiedad IEWSClient.getMailboxInfo().getXXXFolderUri para obtener la URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes. El siguiente fragmento de código le muestra cómo listar mensajes de diferentes carpetas usando EWS.


~~~Java
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener URI de la carpeta
String strFolderURI = "";
strFolderURI = client.getMailboxInfo().getInboxUri();
strFolderURI = client.getMailboxInfo().getDeletedItemsUri();
strFolderURI = client.getMailboxInfo().getDraftsUri();
strFolderURI = client.getMailboxInfo().getSentItemsUri();

// Obtener lista de mensajes de la carpeta específica
ExchangeMessageInfoCollection msgCollection = client.listMessages(strFolderURI);
~~~
### **Listando Mensajes con Soporte de Paginación**
El siguiente fragmento de código Java le muestra cómo obtener una lista de mensajes con soporte de paginación.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com", "username", "password");
try {
    try {
        // Crear algunos mensajes de prueba para ser añadidos al servidor para su recuperación posterior
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35157_1 - " + UUID.randomUUID().toString(),
                    "EMAILNET-35157 Mover parámetros de paginación a una clase separada");
            client.appendMessage(client.getMailboxInfo().getInboxUri(), message);
        }
        // Verifique que los mensajes han sido añadidos al servidor
        ExchangeMessageInfoCollection totalMessageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
        System.out.println(totalMessageInfoCol.size());

        ////////////////// RECUPERANDO LOS MENSAJES USANDO SOPORTE DE PAGINACIÓN ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage);
        // Total de Páginas Contadas
        System.out.println(pageInfo.getTotalCount());

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), itemsPerPage, pageInfo.getPageOffset() + 1);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // conversión de foreach a while
        for (ExchangeMessagePageInfo pageCol : pages) {
            retrievedItems += pageCol.getItems().size();
        }
        // Verifique el recuento total de mensajes usando paginación
        System.out.println(retrievedItems);
    } finally {
    }
} finally {
    client.dispose();
}
~~~
### **Obteniendo Información del Tipo de Mensaje desde ExchangeMessageInfo**


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.listMessages(client.getMailboxInfo().getDeletedItemsUri());
System.out.println(list.get_Item(0).getMessageInfoType()); // MessageInfoType
~~~
## **Guardando Mensajes**
Este artículo muestra cómo obtener mensajes de un buzón del Servidor Exchange y guardarlos en el disco en formatos EML y MSG:

- Guardar como EML en el disco.
- Guardar en un flujo de memoria.
- Guardar como MSG.
### **Guardando Mensajes en EML**
Para obtener mensajes y guardarlos en formato EML:

1. Crear una instancia de la clase IEWSClient.
1. Proporcionar la mailboxUri, nombre de usuario, contraseña y dominio.
1. Llamar al método IEWSClient.listMessages() para obtener una instancia de la colección ExchangeMessagesInfoCollection.
1. Recorrer la colección ExchangeMessagesInfoCollection para obtener la URI única para cada mensaje.
1. Llamar al método IEWSClient.saveMessage() y pasar la URI única como parámetro.
1. Proporcionar al método saveMessage() una ruta donde desea guardar el archivo.

El siguiente fragmento de código le muestra cómo usar EWS para conectarse al Servidor Exchange y guardar mensajes como archivos EML.



~~~Java
// Crear instancia de la clase IEWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes desde la carpeta de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Recorrer la colección para obtener la URI del Mensaje
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Ahora guardar el mensaje en el disco
    client.saveMessage(strMessageURI, dataDir + msgInfo.getMessageId() + "out.eml");
}
~~~
### **Guardando Mensajes en un Flujo de Memoria**
En lugar de guardar archivos EML en el disco, es posible guardarlos en un flujo de memoria. Esto es útil cuando desea guardar el flujo en algún lugar de almacenamiento como una base de datos. Una vez que el flujo ha sido guardado en una base de datos, puede recargar el archivo EML en la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). El siguiente fragmento de código le muestra cómo guardar mensajes de un buzón del Servidor Exchange en un flujo de memoria usando EWS.



~~~Java
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes desde la carpeta de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Recorrer la colección para obtener la URI del Mensaje
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Ahora guardar el mensaje en un flujo de memoria
    ByteArrayOutputStream stream = new ByteArrayOutputStream();
    client.saveMessage(strMessageURI, stream);
}
~~~
### **Guardando Mensajes en Formato MSG**
El método [IEWSClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#saveMessage\(java.lang.String,%20java.lang.String\)) puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llame al método [IEWSClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchMessage\(java.lang.String\)) que devuelve una instancia de la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Luego llame al método [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.lang.String\)) para guardar el mensaje como MSG. El siguiente fragmento de código le muestra cómo obtener mensajes de un buzón del Servidor Exchange y guardarlos en formato MSG usando EWS.



~~~Java
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes desde la carpeta de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

int count = 0;
// Recorrer la colección para obtener la URI del Mensaje
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Ahora obtener los detalles del mensaje usando FetchMessage() y guardar el mensaje como Msg
    MailMessage message = client.fetchMessage(strMessageURI);
    message.save(dataDir + (count++) + "_out.msg", SaveOptions.getDefaultMsgUnicode());
}
~~~
## **Obteniendo ExchangeMessageInfo desde URI del Mensaje**
Un mensaje de correo electrónico está representado por su identificador único, URI, y es parte integral del objeto [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). En caso de que solo esté disponible la URI del mensaje, entonces el objeto [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) también se puede recuperar usando esta información disponible. La versión sobrecargada de [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.Iterable\)) toma una lista de Ids para usar [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection). El siguiente fragmento de código le muestra cómo obtener [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) desde la URI del mensaje.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<String> ids = new ArrayList<String>();
List<MailMessage> messages = new ArrayList<MailMessage>();

for (int i = 0; i < 5; i++) {
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + UUID.randomUUID().toString(),
            "EMAILNET-35033 Los mensajes guardados de la carpeta de Elementos Enviados no contienen el campo 'Para'");
    messages.add(message);
    String uri = client.appendMessage(message);
    ids.add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.listMessages(ids);

for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) messageInfoCol) {
    // Hacer algo ...
    System.out.println(messageInfo.getUniqueUri());
}
~~~
## **Recuperar Mensajes de un Buzón del Servidor Exchange**
Listar Mensajes en un Servidor Exchange usó el método [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) para obtener una lista de mensajes de un buzón del Servidor Exchange. El método [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String\)) obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, de y para. Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona el método IEWSClient.fetchMessage(). Este método acepta la URI del mensaje como parámetro y devuelve una instancia de la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). La clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) luego proporciona detalles del mensaje como cuerpo, encabezados y adjuntos. Descubra más sobre la API de [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage), o averigüe cómo administrar correos electrónicos con la clase [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Para recuperar mensajes del Buzón del Servidor Exchange:

1. Cree una instancia del tipo IEWSClient.
1. Especifique el nombre del servidor, nombre de usuario, contraseña y dominio.
1. Llame a listMessages para obtener la ExchangeMessageInfoCollection.
1. Recorra la colección ExchangeMessageInfoCollection para obtener los valores de ExchangeMessageInfo.UniqueURI.
1. Llame a IEWSClient.fetchMessage() y pase ExchangeMessageInfo.UniqueURI como parámetro.

El siguiente fragmento de código le muestra cómo conectarse al buzón del Servidor Exchange y recuperar todos los mensajes usando EWS.



~~~Java
// Crear instancia de la clase ExchangeWebServiceClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes desde la carpeta de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Recorrer la colección para obtener la URI del Mensaje
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    String strMessageURI = msgInfo.getUniqueUri();

    // Ahora obtener los detalles del mensaje utilizando FetchMessage()
    MailMessage msg = client.fetchMessage(strMessageURI);

    for (Attachment att : (Iterable<Attachment>) msg.getAttachments()) {
        System.out.println("Nombre del Adjuntado: " + att.getName());
    }
}
~~~

### **Usando el método FetchItem para recuperar un mensaje**

{{% alert color="primary" %}}

Nota, el método [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) devuelve el mensaje sin adjuntos. Para recuperar mensajes con adjuntos, use el método [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String,%20java.lang.Iterable\)), descrito en la sección siguiente. 

{{% /alert %}}

El método [FetchItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#fetchItem\(java.lang.String\)) es más preferido si desea recuperar un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) y operar con propiedades MAPI. También puede usar este método para recuperar cualquier elemento de Outlook, como un contacto, cita, tarea, etc.

```java
// Crear instancia de la clase ExchangeWebServiceClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes desde la carpeta de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Recorrer la colección para obtener la URI del Mensaje
for (ExchangeMessageInfo msgInfo : msgCollection)
{
    // Ahora obtener el mensaje usando FetchItem()
    MapiMessage msg = client.fetchItem(msgInfo.getUniqueUri());

    // Si es necesario, puede convertir el MapiMessage al tipo de item correcto para simplificar el trabajo con sus propiedades.
    MapiContact contact = (MapiContact) msg.toMapiMessageItem();
}
```

## **Tamaño de Mensaje Pre-Fetch**
Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de recuperar realmente el mensaje completo del servidor. En el caso de la API de Aspose.Email, la información de resumen recuperada del servidor Exchange está representada por la clase [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). Proporciona la misma función de recuperar el tamaño del mensaje usando la propiedad Size. Para recuperar el tamaño del mensaje, se utiliza la llamada estándar al método listMessages de IEWSClient que recupera una colección de [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo). El siguiente fragmento de código le muestra cómo mostrar el tamaño del mensaje utilizando la clase [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo).



~~~Java
// Crear instancia de la clase ExchangeWebServiceClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes desde la carpeta de entrada
ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

// Recorrer la colección para mostrar la información básica
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Asunto: " + msgInfo.getSubject());
    System.out.println("De: " + msgInfo.getFrom().toString());
    System.out.println("Para: " + msgInfo.getTo().toString());
    System.out.println("Tamaño del Mensaje: " + msgInfo.getSize());
    System.out.println("==================================");
}
~~~
## **Descargar Mensajes Recursivamente**
El método [listSubFolders()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listSubFolders\(com.aspose.email.ExchangeFolderInfo\)) de [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) se puede usar para obtener mensajes de carpetas y subcarpetas de un buzón del Servidor Exchange de forma recursiva. Esto requiere Exchange Server 2007 o superior, ya que utiliza EWS. El siguiente fragmento de código le muestra cómo descargar todo el buzón (carpetas y subcarpetas) de un Servidor Exchange. La estructura de carpetas se crea localmente y todos los mensajes se descargan.



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

        System.out.println("Descargando todos los mensajes de la carpeta de entrada....");
        // Crear instancia de la clase IEWSClient proporcionando credenciales
        IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();
        System.out.println("URI del buzón: " + mailboxInfo.getMailboxUri());
        String rootUri = client.getMailboxInfo().getRootUri();
        // Listar todas las carpetas desde el servidor Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(rootUri);
        for (ExchangeFolderInfo folderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            // Llamar al método recursivo para leer mensajes y obtener subcarpetas
            listMessagesInFolder(client, folderInfo, rootFolder);
        }

        System.out.println("Todos los mensajes descargados.");
    } catch (java.lang.RuntimeException ex) {
        System.out.println(ex.getMessage());
    }
}

// Método recursivo para obtener mensajes de carpetas y subcarpetas
private static void listMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, String rootFolder) {
    // Crear la carpeta en el disco (mismo nombre que en el servidor IMAP)
    String currentFolder = rootFolder + "\\" + folderInfo.getDisplayName();
    new File(currentFolder).mkdirs();

    // Listar mensajes
    ExchangeMessageInfoCollection msgInfoColl = client.listMessages(folderInfo.getUri());
    System.out.println("Listando mensajes....");
    int i = 0;
    for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
        // Obtener asunto y otras propiedades del mensaje
        System.out.println("Asunto: " + msgInfo.getSubject());

        // Eliminar caracteres como ? y :, que no deberían incluirse en el nombre de un archivo
        String fileName = msgInfo.getSubject().replace("?", " ").replace(":", " ");

        MailMessage msg = client.fetchMessage(msgInfo.getUniqueUri());
        msg.save(dataDir + "\\" + fileName + "-" + i + ".msg");

        i++;
    }
    System.out.println("============================\n");
    try {
        // Si esta carpeta tiene subcarpetas, llamar a este método recursivamente para obtener mensajes
        ExchangeFolderInfoCollection folderInfoCollection = client.listSubFolders(folderInfo.getUri());
        for (ExchangeFolderInfo subfolderInfo : (Iterable<ExchangeFolderInfo>) folderInfoCollection) {
            listMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    } catch (java.lang.RuntimeException e) {
    }
}
~~~
## **Descargar Mensajes de Carpetas Públicas**
Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacer esto a través de su aplicación, use la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) de Aspose.Email para conectarse al Servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. El siguiente fragmento de código le muestra cómo leer todas las carpetas públicas, y subcarpetas, y listar y descargar cualquier mensaje encontrado en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior ya que solo estos soportan EWS.



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
        System.out.println("Nombre: " + publicFolder.getDisplayName());
        System.out.println("Cantidad de Subcarpetas: " + publicFolder.getChildFolderCount());
        listMessagesFromSubFolder(publicFolder, client);

    }
}

private static void listMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client) {
    System.out.println("Nombre de la Carpeta: " + publicFolder.getDisplayName());
    ExchangeMessageInfoCollection msgInfoCollection = client.listMessagesFromPublicFolder(publicFolder);
    for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) msgInfoCollection) {
        MailMessage msg = client.fetchMessage(messageInfo.getUniqueUri());
        System.out.println(msg.getSubject());
        msg.save(dataDir + msg.getSubject() + ".msg", SaveOptions.getDefaultMsgUnicode());
    }

    // Llamar a este método recursivamente para cualquier subcarpeta
    if (publicFolder.getChildFolderCount() > 0) {
        ExchangeFolderInfoCollection subfolders = client.listSubFolders(publicFolder);
        for (ExchangeFolderInfo subfolder : (Iterable<ExchangeFolderInfo>) subfolders) {
            listMessagesFromSubFolder(subfolder, client);
        }
    }
}
~~~
## **Moviendo Mensajes**
Puede mover mensajes de correo electrónico de una carpeta a otra con la ayuda del método [move](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#moveItem\(java.lang.String,%20java.lang.String\)) de la clase [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Toma como parámetros:

- La URI única del mensaje que se va a mover.
- La URI única de la carpeta de destino.
### **Moviendo Mensajes entre Carpetas**
El siguiente fragmento de código le muestra cómo mover un mensaje en un buzón de la carpeta de entrada a una carpeta llamada Procesados. En este ejemplo, la aplicación:

1. Lee mensajes de la carpeta de entrada.
1. Procesa algunos de los mensajes según ciertos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen la condición dada a la carpeta procesada.

~~~Java
// Crear instancia de la clase IEWSClient proporcionando credenciales
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// Listar todos los mensajes desde la carpeta de entrada
System.out.println("Listando todos los mensajes desde la carpeta de entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Mover mensaje a la carpeta "Procesados", después de procesar ciertos mensajes según ciertos criterios
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("procesar este mensaje")) {
        client.moveItem(mailboxInfo.getDeletedItemsUri(), msgInfo.getUniqueUri()); // EWS
        System.out.println("Mensaje movido...." + msgInfo.getSubject());
    } else {
        // Hacer algo más
    }
}
~~~
## **Eliminando Mensajes**
Puede eliminar mensajes de correo electrónico de una carpeta con la ayuda del método [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) de la clase [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Toma la URI única del mensaje como parámetro.

El siguiente fragmento de código le muestra cómo eliminar un mensaje de la carpeta de entrada. Con el propósito de este ejemplo, el código:

1. Lee mensajes de la carpeta de entrada.
1. Procesa mensajes según ciertos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimina el mensaje.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.getMailboxInfo();

// Listar todos los mensajes desde la carpeta de entrada
System.out.println("Listando todos los mensajes desde la carpeta de entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.listMessages(mailboxInfo.getInboxUri());
for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgInfoColl) {
    // Eliminar mensaje según ciertos criterios
    if (msgInfo.getSubject() != null && msgInfo.getSubject().toLowerCase().contains("eliminar") == true) {
        client.deleteItem(msgInfo.getUniqueUri(), DeletionOptions.getDeletePermanently()); // EWS
        System.out.println("Mensaje eliminado...." + msgInfo.getSubject());
    } else {
        // Hacer algo más
    }
}
~~~
## **Copiando Mensajes**
La API de Aspose.Email permite copiar un mensaje de una carpeta a otra utilizando el método [copyItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#copyItem\(java.lang.String,%20java.lang.String\)). La versión sobrecargada de este método devuelve la URI Única del mensaje copiado como se muestra en este artículo.
### **Copiando un Mensaje a Otra Carpeta**
El siguiente fragmento de código le muestra cómo copiar un mensaje a otra carpeta.



~~~Java
try {
    // Crear instancia de la clase EWSClient proporcionando credenciales
    IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + UUID.randomUUID().toString(),
            "EMAILNET-34997 Exchange: Copiar un mensaje y obtener referencia al nuevo elemento Copiado");
    String messageUri = client.appendMessage(message);
    String newMessageUri = client.copyItem(messageUri, client.getMailboxInfo().getDeletedItemsUri());
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~