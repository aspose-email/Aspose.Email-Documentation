---
title: "Trabajando con el buzón y los mensajes de Exchange: lea el correo electrónico de Exchange Server en C#"
url: /es/net/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Trabajar con el buzón y los mensajes de Exchange"
keywords: "c# lee el correo electrónico del servidor Exchange"
---


## **Obtención de información de buzones mediante EWS**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) la clase tiene miembros que se pueden usar para obtener información de buzones de un servidor de Exchange llamando al [IEWSClient.GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getmailboxinfo/) método. Devuelve una instancia de tipo [ExchangeMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/). Obtenga información sobre los buzones de correo de propiedades como [MailboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/mailboxuri/), [InboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/inboxuri/) and [DraftsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/draftsuri/). En este artículo se muestra cómo acceder a la información de los buzones de correo mediante los servicios web de Exchange.

Si desea conectarse al servidor de Exchange mediante los servicios web de Exchange (EWS), utilice el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) clase en el espacio de nombres Aspose.Email.Exchange. Esta clase usa EWS para conectarse y administrar los elementos de un servidor Exchange. El siguiente fragmento de código de C# muestra cómo obtener información sobre los buzones de correo mediante los servicios web de Exchange.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials        
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get mailbox size, exchange mailbox info, Mailbox and Inbox folder URI
Console.WriteLine("Mailbox size: " + client.GetMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
Console.WriteLine("Mailbox URI: " + mailboxInfo.MailboxUri);
Console.WriteLine("Inbox folder URI: " + mailboxInfo.InboxUri);
Console.WriteLine("Sent Items URI: " + mailboxInfo.SentItemsUri);
Console.WriteLine("Drafts folder URI: " + mailboxInfo.DraftsUri);
```

## **Envío de mensajes de correo electrónico**

Puede enviar mensajes de correo electrónico mediante un servidor de Exchange con la ayuda de las herramientas de [Aspose.Email.Exchange](https://reference.aspose.com/email/net/aspose.email.clients.exchange/). El [IEWSClient.Send()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/) el método acepta un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instancia como parámetro y envía el correo electrónico. En este artículo se explica cómo enviar mensajes de correo electrónico mediante los servicios web de Exchange.

Aspose.Email proporciona la [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) clase para conectarse a Microsoft Exchange Server mediante los servicios web de Exchange. El siguiente fragmento de código muestra cómo usar EWS para enviar correos electrónicos con Microsoft Exchange Server. El siguiente fragmento de código de C# muestra cómo enviar mensajes de correo electrónico mediante EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Create instance of type MailMessage
MailMessage msg = new MailMessage();
msg.From = "sender@domain.com";
msg.To = "recipient@ domain.com ";
msg.Subject = "Sending message from exchange server";
msg.HtmlBody = "<h3>sending message from exchange server</h3>";

// Send the message
client.Send(msg);
```

## **Uri del artículo que se está enviando**

Un identificador de correo electrónico enviado se puede recuperar del servidor Exchange con el siguiente código de ejemplo:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password"))
{
    // Register the event handler
    client.ItemSent += new EventHandler<SentItemEventArgs>(ItemSentHandler);

    MailMessage eml = new MailMessage("test@test.com", "test@test.com", "test message", "This is a test message");

    client.Send(eml);
}
```

donde el método delegado es:

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Define an event handler method
private static void ItemSentHandler(object sender, SentItemEventArgs e)
{
   
    // Now we can get an id of sent email, which was saved in Sent Items folder
    string id = e.SentFolderItemId;
}
```

## **Lectura de correos electrónicos del buzón de otro usuario**

Algunas cuentas de los servidores de Exchange tienen derecho a acceder a varios buzones de correo y algunos usuarios tienen varias cuentas de correo electrónico en el mismo servidor de Exchange. En ambos casos, los usuarios pueden acceder a los buzones de otros usuarios mediante Aspose.Email para.NET. Esta API proporciona un mecanismo para acceder a las carpetas y correos electrónicos de otros buzones mediante el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#methods) interfaz. Esta funcionalidad se puede lograr utilizando la función sobrecargada [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/getmailboxinfo/#getmailboxinfo) método y proporcionar la dirección de correo electrónico del usuario como parámetro.

El siguiente fragmento de código de C# muestra cómo leer correos electrónicos con la clase IEWSClient.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get Exchange mailbox info of other email account
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo("otherUser@domain.com");
```

## **Publicar mensajes**

Para obtener una lista de los mensajes de correo electrónico de un buzón de Exchange, llame al [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) método. Obtenga la información básica sobre los mensajes, como el asunto, el origen y el identificador del mensaje, mediante el método ListMessage.

### **Listado de mensajes simples**

Para enumerar los mensajes de un buzón de correo de Exchange:

1. Crea una instancia del [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) método y crear una colección de mensajes.
1. Recorre la colección y muestra la información del mensaje.

El siguiente fragmento de código de C# muestra cómo conectarse a un servidor de Exchange mediante EWS y muestra los mensajes de la carpeta de la bandeja de entrada.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorre el collection to display the basic information
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Subject: " + msgInfo.Subject);
    Console.WriteLine("From: " + msgInfo.From.ToString());
    Console.WriteLine("To: " + msgInfo.To.ToString());
    Console.WriteLine("Message ID: " + msgInfo.MessageId);
    Console.WriteLine("Unique URI: " + msgInfo.UniqueUri);
}
```

### **Listar mensajes de diferentes carpetas**

[Los fragmentos de código anteriores](#simple-messages-listing) lista todos los mensajes de la carpeta Bandeja de entrada. También es posible obtener la lista de mensajes de otras carpetas. El [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) el método acepta un URI de carpeta como parámetro. Mientras el URI de la carpeta sea válido, puede obtener la lista de mensajes de esa carpeta. Usa el [IEWSClient.MailboxInfo.xxxFolderUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/#properties) propiedad para obtener la URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes. El siguiente fragmento de código muestra cómo enumerar los mensajes de diferentes carpetas mediante EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Get folder URI
string strFolderURI = string.Empty;
strFolderURI = client.MailboxInfo.InboxUri;
strFolderURI = client.MailboxInfo.DeletedItemsUri;
strFolderURI = client.MailboxInfo.DraftsUri;
strFolderURI = client.MailboxInfo.SentItemsUri;

// Get list of messages from the specified folder
ExchangeMessageInfoCollection msgCollection = client.ListMessages(strFolderURI);
```

### **Listar mensajes con soporte de paginación**

El siguiente fragmento de código muestra cómo obtener una lista de mensajes con soporte de paginación.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("exchange.domain.com", "username", "password"))
{
    try
    {
        // Create some test messages to be added to server for retrieval later
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++)
        {
            message = new MailMessage(
                "from@domain.com",
                "to@domain.com",
                "EMAILNET-35157_1 - " + Guid.NewGuid().ToString(),
                "EMAILNET-35157 Move paging parameters to separate class");
            client.AppendMessage(client.MailboxInfo.InboxUri, message);
        }
        // Verfiy that the messages have been added to the server
        ExchangeMessageInfoCollection totalMessageInfoCol = client.ListMessages(client.MailboxInfo.InboxUri);
        Console.WriteLine(totalMessageInfoCol.Count);

        ////////////////// RETREIVING THE MESSAGES USING PAGING SUPPORT ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new List<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage);
        // Total Pages Count
        Console.WriteLine(pageInfo.TotalCount);

        pages.Add(pageInfo);
        while (!pageInfo.LastPage)
        {
            pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage, pageInfo.PageOffset + 1);
            pages.Add(pageInfo);
        }
        int retrievedItems = 0;
        foreach (ExchangeMessagePageInfo pageCol in pages)
            retrievedItems += pageCol.Items.Count;
        // Verify total message count using paging
        Console.WriteLine(retrievedItems);
    }
    finally
    {
    }
}         
```

### **Obtener información sobre el tipo de mensaje de ExchangeMessageInfo**

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
const string mailboxUri = "https://exchange/ews/exchange.asmx";
const string domain = @"";
const string username = @"username@ASE305.onmicrosoft.com";
const string password = @"password";
NetworkCredential credentials = new NetworkCredential(username, password, domain);

IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.ListMessages(client.MailboxInfo.DeletedItemsUri);
Console.WriteLine(list[0].MessageInfoType.ToString());
```
### **Recuperando la clase de mensaje del objeto ExchangeMessageInfo**

La clase de mensaje representa el tipo de elemento del almacén de Exchange. Al obtener la clase de mensaje, puede determinar el tipo de mensaje de correo electrónico de Exchange y realizar operaciones específicas en función de su clasificación.

A continuación, se muestra un ejemplo de cómo obtener la clase de mensaje mediante [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) clase de Aspose.Email para.NET:

**Ejemplo de código**

```cs
using (var client = EWSClient.GetEWSClient(uri, credentials))
{
    var messageInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);

    foreach (var messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Message Class: {0}", messageInfo.MessageClass);
    }
}
```

## **Guardar mensajes**

En este artículo se muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en el disco en formatos EML y MSG:

- Guardar como EML en el disco.
- Guardar en la secuencia de memoria.
- Guardar como MSG.
 
### **Guardar mensajes en EML**

Para obtener mensajes y guardarlos en formato EML:

1. Crea una instancia del [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Proporcione la URI del buzón, el nombre de usuario, la contraseña y el dominio.
1. Llame al [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) método para obtener una instancia del [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/).
1. Recorre el [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/) para obtener la URI única de cada mensaje.
1. Llame al [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) método y pase la URI única como parámetro.
1. Proporcione un [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) método con una ruta al lugar donde desea guardar el archivo.

El siguiente fragmento de código muestra cómo usar EWS para conectarse al servidor Exchange y guardar los mensajes como archivos EML.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Create instance of IEWSClient interface by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorre el collection para obtener Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Now save the message in disk
    client.SaveMessage(strMessageURI, dataDir + msgInfo.MessageId + "out.eml");
}
```

### **Guardar mensajes en un flujo de memoria**

En lugar de guardar los archivos EML en el disco, es posible guardarlos en una secuencia de memoria. Esto es útil cuando quieres guardar la transmisión en alguna ubicación de almacenamiento, como una base de datos. Una vez guardada la transmisión en una base de datos, puede volver a cargar el archivo EML en [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. El siguiente fragmento de código muestra cómo guardar los mensajes de un buzón de Exchange Server en un flujo de memoria mediante EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
string datadir = RunExamples.GetDataDir_Exchange();
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorre el collection para obtener Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Now save the message in memory stream
    MemoryStream stream = new MemoryStream();
    client.SaveMessage(strMessageURI, datadir + stream);
}
```

### **Guardar mensajes en formato MSG**

The [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) El método puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llame al [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) método que devuelve una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Entonces llama al [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en formato MSG mediante EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

int count = 0;
// Recorre el collection para obtener Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;
   
    // Now get the message details using FetchMessage() and Save message as Msg
    MailMessage message = client.FetchMessage(strMessageURI);
    message.Save(dataDir + (count++) + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

## **Obtener ExchangeMessageInfo del URI del mensaje**

Un mensaje de correo electrónico está representado por su identificador único, URI, y forma parte integral del [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) objeto. En caso de que solo esté disponible el URI del mensaje, entonces [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) el objeto también se puede recuperar utilizando esta información disponible. La versión de sobrecarga de [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) toma una lista de identificaciones para usar [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/). El siguiente fragmento de código muestra cómo obtener [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) del URI del mensaje.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<string> ids = new List<string>();
List<MailMessage> messages = new List<MailMessage>();

for (int i = 0; i < 5; i++)
{
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + Guid.NewGuid().ToString(), "EMAILNET-35033 Messages saved from Sent Items folder doesn't contain 'To' field");
    messages.Add(message);
    string uri = client.AppendMessage(message);
    ids.Add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.ListMessages(ids);

foreach (ExchangeMessageInfo messageInfo in messageInfoCol)
{
    // Do something ...
    Console.WriteLine(messageInfo.UniqueUri);
}
```

## **Obtener mensajes de un buzón de correo de Exchange Server**

Para enumerar mensajes en un servidor Exchange [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) el método se usa para obtener una lista de mensajes de un buzón de Exchange Server. El [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) El método obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, el origen y el destino. Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) método. Este método acepta el URI del mensaje como parámetro y devuelve una instancia del [Aspose.Email.MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. El [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) La clase luego proporciona detalles del mensaje como el cuerpo, los encabezados y los archivos adjuntos. Obtenga más información sobre la API MailMessage o descubra cómo administrar los correos electrónicos con la [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. Para obtener mensajes del buzón de Exchange Server:

1. Crear una instancia de tipo [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Especifique el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Call [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) para obtener el [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/).
1. Recorre el [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) para obtener [ExchangeMessageInfo.UniqueURI](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) values.
1. Call [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) y pase [ExchangeMessageInfo.UniqueURI()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) como parámetro.

El siguiente fragmento de código muestra cómo conectarse al buzón de correo de Exchange Server y recuperar todos los mensajes mediante EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorre el collection para obtener Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
 String strMessageURI = msgInfo.UniqueUri;

 // Now get the message details using FetchMessage()
 MailMessage msg = client.FetchMessage(strMessageURI);

    foreach (Attachment att in msg.Attachments)
 {
  Console.WriteLine("Attachment Name: " + att.Name);
 }
}
```

### **Uso del método fetchItem para obtener un mensaje**

{{% alert color="primary" %}}

Tenga en cuenta que el [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) el método devuelve el mensaje sin archivos adjuntos. Para buscar mensajes con archivos adjuntos, utilice el [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) método, descrito en la sección siguiente.

{{% /alert %}}

The [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/fetchitem) el método es más preferido si desea obtener un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/mapimessage/) y funcionan con las propiedades de MAPI. También puede utilizar este método para recuperar cualquier elemento de Outlook, como un contacto, una cita, una tarea, etc.

```csharp
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Contacts folder
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.ContactsUri);

// Recorre el collection para obtener Message URI
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
   // Now get the message using FetchItem()
   MapiMessage msg = client.FetchItem(msgInfo.UniqueUri);

   // If necessary, you can cast the MapiMessage to the proper item type to simplify working with its properties.
   MapiContact contact = (MapiContact) msg.ToMapiMessageItem();
}
```

### **Uso del método fetchItems**

Lo descrito anteriormente [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) el método devuelve el mensaje **sin archivos adjuntos**, en un intento por mantener el rendimiento.

Para buscar mensajes con archivos adjuntos, usa la más potente [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) método, que permite pasar el [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/) options.

```csharp
var uriList = client.ListItems(client.MailboxInfo.InboxUri);
var items = client.FetchItems(EwsFetchItems.Create().AddUris(uriList).WithAttachments());
```

## **Obtención de artículos con archivos adjuntos**

The [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method)El método (opciones EWSFetchItems) de EWSClient recupera los elementos de correo electrónico de un servidor Exchange. Acepta una instancia de [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) clase como parámetro para definir varias opciones para obtener los elementos.

El siguiente código muestra cómo obtener artículos con archivos adjuntos:

```cs
// Llame al ListMessages method to retrieve a list of message from the Inbox folder
var messageInfoList = ewsClient.ListMessages(ewsClient.MailboxInfo.InboxUri);

// Crea una instancia del EwsFetchItems class and assign it to the options variable
var options = EwsFetchItems.Create();

// Generate a new collection of messages which is then converted to a List.
var uriList = messageInfoList.Select(item => item.UniqueUri).ToList();

// Fetch only messages containing attachments
var items = ewsClient.FetchItems(options.AddUris(uriList).WithAttachments());
```

## **Tamaño del mensaje de captura previa**

Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de obtener el mensaje completo del servidor. En el caso de la API Aspose.Email, la información resumida recuperada del servidor Exchange está representada por [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) clase. Proporciona la misma función de recuperar el tamaño del mensaje mediante el [Size](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/size/) propiedad. Para recuperar el tamaño del mensaje, la llamada estándar a [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) se utiliza para recuperar la colección de [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). En el siguiente fragmento de código se muestra cómo mostrar el tamaño de los mensajes mediante el [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) class.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of ExchangeWebServiceClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Call ListMessages method to list messages info from Inbox
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorre el collection to display the basic information
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Subject: " + msgInfo.Subject);
    Console.WriteLine("From: " + msgInfo.From.ToString());
    Console.WriteLine("To: " + msgInfo.To.ToString());
    Console.WriteLine("Message Size: " + msgInfo.Size);
    Console.WriteLine("==================================");
}
```

## **Descargar mensajes de forma recursiva**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) [ListSubFolders()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/listsubfolders/#listsubfolders/) El método se puede utilizar para obtener mensajes de carpetas y subcarpetas de un buzón de Exchange Server de forma recursiva. Esto requiere Exchange Server 2007 o superior, ya que utiliza EWS. En el siguiente fragmento de código se muestra cómo descargar todo el buzón (carpetas y subcarpetas) de un servidor Exchange. La estructura de carpetas se crea localmente y se descargan todos los mensajes.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
static string username = "administrator";
static string password = "pwd";
static string domain = "ex2010.local";
private static string dataDir = RunExamples.GetDataDir_Exchange();
public static void Run()
{
    // Register callback method for SSL validation event
    ServicePointManager.ServerCertificateValidationCallback += RemoteCertificateValidationHandler;
    try
    {
        DownloadAllMessages();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void DownloadAllMessages()
{
    try
    {
        string rootFolder = domain + "-" + username;
        Directory.CreateDirectory(rootFolder);
        string inboxFolder = rootFolder + "\\Inbox";
        Directory.CreateDirectory(inboxFolder);

        Console.WriteLine("Downloading all messages from Inbox....");
        // Create instance of IEWSClient class by giving credentials
        IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
        Console.WriteLine("Mailbox URI: " + mailboxInfo.MailboxUri);
        string rootUri = client.GetMailboxInfo().RootUri;
        // List all the folders from Exchange server
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(rootUri);
        foreach (ExchangeFolderInfo folderInfo in folderInfoCollection)
        {
            // Llame al recursive method to read messages and get sub-folders
            ListMessagesInFolder(client, folderInfo, rootFolder);
        }

        Console.WriteLine("All messages downloaded.");
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

// Recursive method para obtener messages from folders and sub-folders
private static void ListMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, string rootFolder)
{
    // Create the folder in disk (same name as on IMAP server)
    string currentFolder = rootFolder + "\\" + folderInfo.DisplayName;
    Directory.CreateDirectory(currentFolder);

    // List messages
    ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(folderInfo.Uri);
    Console.WriteLine("Listing messages....");
    int i = 0;
    foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
    {
        // Get subject and other properties of the message
        Console.WriteLine("Subject: " + msgInfo.Subject);

        // Get rid of characters like ? and :, which should not be included in a file name
        string fileName = msgInfo.Subject.Replace(":", " ").Replace("?", " ");

        MailMessage msg = client.FetchMessage(msgInfo.UniqueUri);
        msg.Save(dataDir + "\\" + fileName + "-" + i + ".msg");
 
        i++;
    }
    Console.WriteLine("============================\n");
    try
    {
        // If this folder has sub-folders, call this method recursively para obtener messages
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(folderInfo.Uri);
        foreach (ExchangeFolderInfo subfolderInfo in folderInfoCollection)
        {
            ListMessagesInFolder(client, subfolderInfo, currentFolder);
        }
    }
    catch (Exception)
    {
    }
}
private static bool RemoteCertificateValidationHandler(object sender, X509Certificate certificate, X509Chain chain, SslPolicyErrors sslPolicyErrors)
{
    return true; // Ignore the checks and go ahead
}
```

## **Descargar mensajes de carpetas públicas**

Microsoft Exchange Server permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de su aplicación, utilice Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase para conectarse al servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. En el siguiente fragmento de código se muestra cómo leer todas las carpetas y subcarpetas públicas, y cómo mostrar y descargar los mensajes que se encuentran en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos son compatibles con EWS.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
public static string dataDir = RunExamples.GetDataDir_Exchange();
public static string mailboxUri = "https://exchange/ews/exchange.asmx"; // EWS
public static string username = "administrator";
public static string password = "pwd";
public static string domain = "ex2013.local";

public static void Run()
{
    try
    {
        ReadPublicFolders();
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

private static void ReadPublicFolders()
{
    NetworkCredential credential = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credential);

    ExchangeFolderInfoCollection folders = client.ListPublicFolders();
    foreach (ExchangeFolderInfo publicFolder in folders)
    {
        Console.WriteLine("Name: " + publicFolder.DisplayName);
        Console.WriteLine("Subfolders count: " + publicFolder.ChildFolderCount);
        ListMessagesFromSubFolder(publicFolder, client);

    }
}

private static void ListMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client)
{
    Console.WriteLine("Folder Name: " + publicFolder.DisplayName);
    ExchangeMessageInfoCollection msgInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);
    foreach (ExchangeMessageInfo messageInfo in msgInfoCollection)
    {
        MailMessage msg = client.FetchMessage(messageInfo.UniqueUri);
        Console.WriteLine(msg.Subject);
        msg.Save(dataDir +  msg.Subject + ".msg",  SaveOptions.DefaultMsgUnicode);
    }

    // Call this method recursively for any subfolders
    if (publicFolder.ChildFolderCount > 0)
    {
        ExchangeFolderInfoCollection subfolders = client.ListSubFolders(publicFolder);
        foreach (ExchangeFolderInfo subfolder in subfolders)
        {
            ListMessagesFromSubFolder(subfolder, client);
        }
    }
}
```

## **Mensajes en movimiento**

Puede mover los mensajes de correo electrónico de una carpeta a otra con la ayuda del [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface [Move](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveitem/) método. Toma los parámetros:

- El URI único del mensaje que se va a mover.
- El URI único de la carpeta de destino.
 
### **Mover mensajes entre carpetas**

El siguiente fragmento de código muestra cómo mover un mensaje de un buzón de la carpeta Bandeja de entrada a una carpeta denominada Procesado. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa algunos de los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen la condición dada a la carpeta procesada.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// List all messages from Inbox folder
Console.WriteLine("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Move message to "Processed" folder, after processing certain messages based on some criteria
    if (msgInfo.Subject != null &&
        msgInfo.Subject.ToLower().Contains("process this message") == true)
    {
        client.MoveItem(mailboxInfo.DeletedItemsUri, msgInfo.UniqueUri); // EWS
        Console.WriteLine("Message moved...." + msgInfo.Subject);
    }
    else
    {
        // Do something else
    }
}
```

## **Eliminar mensajes**

Puede eliminar los mensajes de correo electrónico de una carpeta con la ayuda del [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/exchangeclient/) class [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletemessage/) método. Toma un URI único de un mensaje como parámetro.

El siguiente fragmento de código muestra cómo eliminar un mensaje de la carpeta Bandeja de entrada. Para este ejemplo, el código:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimina el mensaje.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
           
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// List all messages from Inbox folder
Console.WriteLine("Listing all messages from Inbox....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Delete message based on some criteria
    if (msgInfo.Subject != null && msgInfo.Subject.ToLower().Contains("delete") == true)
    {
        client.DeleteItem(msgInfo.UniqueUri, DeletionOptions.DeletePermanently); // EWS
        Console.WriteLine("Message deleted...." + msgInfo.Subject);
    }
    else
    {
        // Do something else
    }
}
```

## **Copiar mensajes**

La API Aspose.Email permite copiar un mensaje de una carpeta a otra mediante el [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/) método. La versión sobrecargada de este método devuelve el URI único del mensaje copiado, como se muestra en este artículo.

### **Copiar un mensaje a otra carpeta**

El siguiente fragmento de código muestra cómo copiar un mensaje a otra carpeta.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
try
{
    // Create instance of EWSClient class by giving credentials
    IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + Guid.NewGuid().ToString(), "EMAILNET-34997 Exchange: Copy a message and get reference to the new Copy item");
    string messageUri = client.AppendMessage(message);
    string newMessageUri = client.CopyItem(messageUri, client.MailboxInfo.DeletedItemsUri);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```
