---
title: "Trabajando con la Buzón de Exchange y Mensajes - Leer correo electrónico desde el servidor de Exchange en C#"
url: /es/net/working-with-exchange-mailbox-and-messages/
weight: 20
type: docs
linktitle: "Trabajando con la Buzón de Exchange y Mensajes"
keywords: "c# leer correo electrónico desde el servidor de exchange"
---

## **Obteniendo información de la Buzón usando EWS**

La clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) tiene miembros que se pueden utilizar para obtener información de la buzón de un Servidor Exchange llamando al método [IEWSClient.GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getmailboxinfo/). Devuelve una instancia del tipo [ExchangeMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/). Obtenga información de la buzón de propiedades como [MailboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/mailboxuri/), [InboxUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/inboxuri/) y [DraftsUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/draftsuri/). Este artículo muestra cómo acceder a la información de la buzón utilizando Servicios Web de Exchange.

Si desea conectarse al Servidor Exchange utilizando Servicios Web de Exchange (EWS), use la clase [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) en el espacio de nombres Aspose.Email.Exchange. Esta clase utiliza EWS para conectarse y administrar elementos en un Servidor Exchange. El siguiente fragmento de código en C# le muestra cómo obtener información de la buzón utilizando los servicios web de intercambio.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase EWSClient proporcionando credenciales         
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener tamaño de la buzón, información de buzón de exchange, URI de buzón y carpeta de bandeja de entrada
Console.WriteLine("Tamaño de la buzón: " + client.GetMailboxSize() + " bytes");
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
Console.WriteLine("URI de la buzón: " + mailboxInfo.MailboxUri);
Console.WriteLine("URI de la carpeta de entrada: " + mailboxInfo.InboxUri);
Console.WriteLine("URI de elementos enviados: " + mailboxInfo.SentItemsUri);
Console.WriteLine("URI de la carpeta de borradores: " + mailboxInfo.DraftsUri);
```

## **Enviando Mensajes de Correo Electrónico**

Puede enviar mensajes de correo electrónico utilizando un Servidor Exchange con la ayuda de las herramientas en [Aspose.Email.Exchange](https://reference.aspose.com/email/net/aspose.email.clients.exchange/). El método [IEWSClient.Send()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/send/) acepta una instancia de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) como parámetro y envía el correo electrónico. Este artículo explica cómo enviar mensajes de correo electrónico utilizando Servicios Web de Exchange.

Aspose.Email proporciona la clase [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) para conectarse a Microsoft Exchange Server utilizando Servicios Web de Exchange. El siguiente fragmento de código en C# le muestra cómo usar EWS para enviar correos electrónicos con Microsoft Exchange Server. 

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase IEWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Crear instancia del tipo MailMessage
MailMessage msg = new MailMessage();
msg.From = "sender@domain.com";
msg.To = "recipient@domain.com";
msg.Subject = "Enviando mensaje desde el servidor de exchange";
msg.HtmlBody = "<h3>enviando mensaje desde el servidor de exchange</h3>";

// Enviar el mensaje
client.Send(msg);
```

## **Obteniendo URI de Elementos Enviados**

Se puede recuperar un Id de correo electrónico enviado desde el servidor de Exchange con el siguiente código de muestra:

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password"))
{
    // Registrar el manejador del evento
    client.ItemSent += new EventHandler<SentItemEventArgs>(ItemSentHandler);

    MailMessage eml = new MailMessage("test@test.com", "test@test.com", "mensaje de prueba", "Este es un mensaje de prueba");

    client.Send(eml);
}
```

donde el método delegado es:

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Definir un método de manejador de eventos
private static void ItemSentHandler(object sender, SentItemEventArgs e)
{
    
    // Ahora podemos obtener un id del correo electrónico enviado, que fue guardado en la carpeta de elementos enviados
    string id = e.SentFolderItemId;
}
```

## **Leyendo Correos Electrónicos desde la Buzón de Otro Usuario**

Algunas cuentas en los Servidores Exchange tienen el derecho de acceder a múltiples buzones, y algunos usuarios tienen múltiples cuentas de correo electrónico en el mismo Servidor Exchange. En ambos casos, los usuarios pueden acceder a las buzones de otros usuarios utilizando Aspose.Email para .NET. Esta API proporciona un mecanismo para acceder a carpetas y correos electrónicos de otras buzones utilizando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#methods). Esta funcionalidad se puede lograr utilizando el método sobrecargado [GetMailboxInfo()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/getmailboxinfo/#getmailboxinfo) y proporcionando la dirección de correo electrónico del usuario como parámetro.

El siguiente fragmento de código en C# le muestra cómo leer correos electrónicos utilizando la clase IEWSClient.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener información de la buzón de otra cuenta de correo electrónico
ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo("otherUser@domain.com");
```

## **Listando Mensajes**

Una lista de los mensajes de correo electrónico en una buzón de Exchange se puede obtener llamando al método [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/). Obtenga la información básica sobre los mensajes, como el asunto, de, a y el ID del mensaje, utilizando el método ListMessage.

### **Listado Simple de Mensajes**

Para listar los mensajes en una buzón de Exchange:

1. Cree una instancia de la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llame al método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) y cree una colección de mensajes.
1. Recorra la colección y muestre la información del mensaje.

El siguiente fragmento de código en C# le muestra cómo conectarse a un servidor de intercambio utilizando EWS y listar mensajes de la carpeta de bandeja de entrada.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase ExchangeWebServiceClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "UserName", "Password");

// Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorrer la colección para mostrar la información básica
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Asunto: " + msgInfo.Subject);
    Console.WriteLine("De: " + msgInfo.From.ToString());
    Console.WriteLine("A: " + msgInfo.To.ToString());
    Console.WriteLine("ID del Mensaje: " + msgInfo.MessageId);
    Console.WriteLine("URI Único: " + msgInfo.UniqueUri);
}
```

### **Listando Mensajes desde Diferentes Carpetas**

[Los fragmentos de código anteriores](#simple-messages-listing) listan todos los mensajes en la carpeta de Bandeja de Entrada. También es posible obtener la lista de mensajes de otras carpetas. El método [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) acepta un URI de carpeta como parámetro. Siempre que el URI de la carpeta sea válido, puede obtener la lista de mensajes de esa carpeta. Use la propiedad [IEWSClient.MailboxInfo.xxxFolderUri](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/#properties) para obtener el URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes. El siguiente fragmento de código le muestra cómo listar mensajes de diferentes carpetas utilizando EWS.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Obtener URI de carpeta
string strFolderURI = string.Empty;
strFolderURI = client.MailboxInfo.InboxUri;
strFolderURI = client.MailboxInfo.DeletedItemsUri;
strFolderURI = client.MailboxInfo.DraftsUri;
strFolderURI = client.MailboxInfo.SentItemsUri;

// Obtener lista de mensajes de la carpeta especificada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(strFolderURI);
```

### **Listando Mensajes con Soporte de Paginación**

El siguiente fragmento de código le muestra cómo obtener una lista de mensajes con soporte de paginación.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
using (IEWSClient client = EWSClient.GetEWSClient("exchange.domain.com", "username", "password"))
{
    try
    {
        // Crear algunos mensajes de prueba para ser añadidos al servidor para su recuperación posterior
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++)
        {
            message = new MailMessage(
                "from@domain.com",
                "to@domain.com",
                "EMAILNET-35157_1 - " + Guid.NewGuid().ToString(),
                "EMAILNET-35157 Mover los parámetros de paginación a una clase separada");
            client.AppendMessage(client.MailboxInfo.InboxUri, message);
        }
        // Verificar que los mensajes han sido añadidos al servidor
        ExchangeMessageInfoCollection totalMessageInfoCol = client.ListMessages(client.MailboxInfo.InboxUri);
        Console.WriteLine(totalMessageInfoCol.Count);

        ////////////////// RECUPERANDO LOS MENSAJES USANDO SOPORTE DE PAGINACIÓN ////////////////////////////////////

        List<ExchangeMessagePageInfo> pages = new List<ExchangeMessagePageInfo>();
        ExchangeMessagePageInfo pageInfo = client.ListMessagesByPage(client.MailboxInfo.InboxUri, itemsPerPage);
        // Total de páginas contadas
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
        // Verificar el conteo total de mensajes utilizando paginación
        Console.WriteLine(retrievedItems);
    }
    finally
    {
    }
}          
```

### **Obteniendo Información del Tipo de Mensaje de ExchangeMessageInfo**

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
const string mailboxUri = "https://exchange/ews/exchange.asmx";
const string domain = @""; 
const string username = @"username@ASE305.onmicrosoft.com";
const string password = @"password"; 
NetworkCredential credentials = new NetworkCredential(username, password, domain);

IEWSClient client = EWSClient.GetEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection list = client.ListMessages(client.MailboxInfo.DeletedItemsUri);
Console.WriteLine(list[0].MessageInfoType.ToString());
```
### **Recuperando la Clase de Mensaje del Objeto ExchangeMessageInfo**

La clase de mensaje representa el tipo de un elemento en la tienda de Exchange. Al obtener la clase de mensaje, puede determinar el tipo del mensaje de correo de Exchange y realizar operaciones específicas según su clasificación.

A continuación se muestra un ejemplo de obtener la clase de mensaje utilizando la clase [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) de Aspose.Email para .NET:

**Ejemplo de código**

```cs
using (var client = EWSClient.GetEWSClient(uri, credentials))
{
    var messageInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);

    foreach (var messageInfo in messageInfoCollection)
    {
        Console.WriteLine("Clase de Mensaje: {0}", messageInfo.MessageClass);
    }
}
```

## **Guardando Mensajes**

Este artículo muestra cómo obtener mensajes de una buzón de Servidor Exchange y guardarlos en disco en formatos EML y MSG:

- Guardar como EML en disco.
- Guardar en una memoria.
- Guardar como MSG.

### **Guardando Mensajes como EML**

Para obtener mensajes y guardarlos en formato EML:

1. Crear una instancia de la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Proporcionar el mailboxUri, username, password y domain.
1. Llamar al método [IEWSClient.ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) para obtener una instancia de [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/).
1. Recorrer la [ExchangeMessagesInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/) para obtener el URI único de cada mensaje.
1. Llamar al método [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) y pasar el URI único como parámetro.
1. Proporcionar un path al método [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) donde desea guardar el archivo.

El siguiente fragmento de código le muestra cómo usar EWS para conectarse al Servidor Exchange y guardar mensajes como archivos EML.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Crear instancia de la interfaz IEWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorrer la colección para obtener el URI del Mensaje
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Ahora guardar el mensaje en el disco
    client.SaveMessage(strMessageURI, dataDir + msgInfo.MessageId + "out.eml");
}
```

### **Guardando Mensajes en un Flujo de Memoria**

En lugar de guardar archivos EML en disco, es posible guardarlos en un flujo de memoria. Esto es útil cuando desea guardar el flujo en alguna ubicación de almacenamiento, como una base de datos. Una vez que el flujo se ha guardado en una base de datos, puede recargar el archivo EML en la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El siguiente fragmento de código le muestra cómo guardar mensajes de una buzón de Servidor Exchange en un flujo de memoria utilizando EWS.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
string dataDir = RunExamples.GetDataDir_Exchange();
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorrer la colección para obtener el URI del Mensaje
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;

    // Ahora guardar el mensaje en el flujo de memoria
    MemoryStream stream = new MemoryStream();
    client.SaveMessage(strMessageURI, dataDir + stream);
}
```

### **Guardando Mensajes en Formato MSG**

El método [IEWSClient.SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/savemessage/) puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llame al método [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) que devuelve una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Luego llame al método [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) para guardar el mensaje en MSG. El siguiente fragmento de código le muestra cómo obtener mensajes de una buzón de Servidor Exchange y guardarlos en formato MSG utilizando EWS.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase EWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

int count = 0;
// Recorrer la colección para obtener el URI del Mensaje
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    string strMessageURI = msgInfo.UniqueUri;
    
    // Ahora obtener los detalles del mensaje utilizando FetchMessage() y guardar el mensaje como Msg 
    MailMessage message = client.FetchMessage(strMessageURI);
    message.Save(dataDir + (count++) + "_out.msg", SaveOptions.DefaultMsgUnicode);
}
```

## **Obteniendo ExchangeMessageInfo desde el URI del Mensaje**

Un mensaje de correo electrónico se representa por su identificador único, URI, y es parte integral del objeto [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). En caso de que solo el URI del mensaje esté disponible, también se puede recuperar el objeto [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) utilizando esta información disponible. La versión sobrecargada de [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) toma una lista de Ids para usar [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/). El siguiente fragmento de código le muestra cómo obtener [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/) desde el URI del mensaje.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "user@domain.com", "pwd", "domain");

List<string> ids = new List<string>();
List<MailMessage> messages = new List<MailMessage>();

for (int i = 0; i < 5; i++)
{
    MailMessage message = new MailMessage("user@domain.com", "receiver@domain.com", "EMAILNET-35033 - " + Guid.NewGuid().ToString(), "EMAILNET-35033 Los mensajes guardados desde la carpeta de elementos enviados no contienen el campo 'Para'");
    messages.Add(message);
    string uri = client.AppendMessage(message);
    ids.Add(uri);
}

ExchangeMessageInfoCollection messageInfoCol = client.ListMessages(ids);

foreach (ExchangeMessageInfo messageInfo in messageInfoCol)
{
    // Hacer algo ...
    Console.WriteLine(messageInfo.UniqueUri);
}
```

## **Recuperando Mensajes de una Buzón de Servidor Exchange**

Para listar mensajes en un Servidor Exchange se utiliza el método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) para obtener una lista de mensajes de una buzón del Servidor Exchange. El método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, de y a. Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona el método [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/). Este método acepta el URI del mensaje como parámetro y devuelve una instancia de la clase [Aspose.Email.MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). La clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) proporciona detalles del mensaje como el cuerpo, encabezados y archivos adjuntos. Descubra más sobre la API de MailMessage, o descubra cómo administrar correos electrónicos con la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Para recuperar mensajes de la Buzón de Servidor Exchange:

1. Crear una instancia del tipo [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Especificar el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llamar a [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) para obtener [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/).
1. Recorrer el [ExchangeMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfocollection/exchangemessageinfocollection/) para obtener los valores de [ExchangeMessageInfo.UniqueURI](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/).
1. Llamar a [IEWSClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchmessage/) y pasar [ExchangeMessageInfo.UniqueURI()](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/uniqueuri/) como parámetro.

El siguiente fragmento de código le muestra cómo conectarse a la buzón del Servidor Exchange y recuperar todos los mensajes utilizando EWS.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase ExchangeWebServiceClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorrer la colección para obtener el URI del Mensaje
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
 String strMessageURI = msgInfo.UniqueUri;

 // Ahora obtener los detalles del mensaje utilizando FetchMessage()
 MailMessage msg = client.FetchMessage(strMessageURI);
 
    foreach (Attachment att in msg.Attachments)
 {
  Console.WriteLine("Nombre del Archivo Adjunto: " + att.Name);
 }
}
```

### **Usando el método FetchItem para obtener un mensaje**

{{% alert color="primary" %}}

Tenga en cuenta que el método [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) devuelve el mensaje sin archivos adjuntos. Para recuperar mensajes con archivos adjuntos, use el método [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) que se describe en la sección siguiente.

{{% /alert %}}

El método [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/methods/fetchitem) es más preferido si desea recuperar un [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/mapimessage/) y operar con propiedades MAPI. También puede usar este método para recuperar cualquier elemento de Outlook, como un contacto, una cita, una tarea, etc.

```csharp
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
// Llamar al método ListMessages para listar la información de los mensajes de la carpeta de Contactos
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.ContactsUri);

// Recorrer la colección para obtener el URI del Mensaje
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
   // Ahora obtener el mensaje utilizando FetchItem()
   MapiMessage msg = client.FetchItem(msgInfo.UniqueUri);

   // Si es necesario, puede convertir el MapiMessage al tipo de elemento correcto para simplificar el trabajo con sus propiedades.
   MapiContact contact = (MapiContact) msg.ToMapiMessageItem();
}
```

### **Usando el método FetchItems**

El método [FetchItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitem/) descrito anteriormente devuelve el mensaje **sin archivos adjuntos**, en un intento de mantener el rendimiento.

Para recuperar mensajes con archivos adjuntos, use el más poderoso método [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/) que permite pasar las opciones [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/).

```csharp
var uriList = client.ListItems(client.MailboxInfo.InboxUri);
var items = client.FetchItems(EwsFetchItems.Create().AddUris(uriList).WithAttachments());
```

## **Recuperando Elementos con Archivos Adjuntos**

El método [FetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method)(EwsFetchItems options) del EwsClient recupera elementos de correo electrónico de un servidor de Exchange. Acepta una instancia de la clase [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) como parámetro para definir varias opciones para recuperar los elementos.

El siguiente código muestra cómo obtener elementos con archivos adjuntos:

```cs
// Llamar al método ListMessages para recuperar una lista de mensajes de la carpeta de Bandeja de Entrada
var messageInfoList = ewsClient.ListMessages(ewsClient.MailboxInfo.InboxUri);

// Crear una instancia de la clase EwsFetchItems y asignarla a la variable options
var options = EwsFetchItems.Create();

// Generar una nueva colección de mensajes que luego se convierte en una Lista.
var uriList = messageInfoList.Select(item => item.UniqueUri).ToList();

// Recuperar solo mensajes que contengan archivos adjuntos
var items = ewsClient.FetchItems(options.AddUris(uriList).WithAttachments());
```

## **Tamaño de Mensaje Pre-Fetch**

Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de realmente recuperar el mensaje completo del servidor. En el caso de la API de Aspose.Email, la información resumen recuperada del servidor Exchange está representada por la clase [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). Proporciona la misma función de recuperar el tamaño del mensaje utilizando la propiedad [Size](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/size/). Para recuperar el tamaño del mensaje, se utiliza la llamada estándar a [IEWSClient.ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) que recupera una colección de [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/). El siguiente fragmento de código le muestra cómo mostrar el tamaño del mensaje utilizando la clase [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/).

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase ExchangeWebServiceClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Llamar al método ListMessages para listar la información de los mensajes de la bandeja de entrada
ExchangeMessageInfoCollection msgCollection = client.ListMessages(client.MailboxInfo.InboxUri);

// Recorrer la colección para mostrar la información básica
foreach (ExchangeMessageInfo msgInfo in msgCollection)
{
    Console.WriteLine("Asunto: " + msgInfo.Subject);
    Console.WriteLine("De: " + msgInfo.From.ToString());
    Console.WriteLine("A: " + msgInfo.To.ToString());
    Console.WriteLine("Tamaño del Mensaje: " + msgInfo.Size);
    Console.WriteLine("==================================");
}
```

## **Descargando Mensajes Recursivamente**

El método [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) [ListSubFolders()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/listsubfolders/#listsubfolders/) se puede usar para obtener mensajes de carpetas y subcarpetas de una buzón de un Servidor Exchange de manera recursiva. Esto requiere Exchange Server 2007 o mayor, porque utiliza EWS. El siguiente fragmento de código muestra cómo descargar toda la buzón (carpetas y subcarpetas) de un Servidor Exchange. La estructura de carpetas se crea localmente y se descargan todos los mensajes.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
static string username = "administrator";
static string password = "pwd";
static string domain = "ex2010.local";
private static string dataDir = RunExamples.GetDataDir_Exchange();
public static void Run()
{
    // Registrar el método de retorno de llamada para el evento de validación de SSL
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
        string inboxFolder = rootFolder + "\\Bandeja de Entrada";
        Directory.CreateDirectory(inboxFolder);

        Console.WriteLine("Descargando todos los mensajes de la Bandeja de Entrada....");
        // Crear instancia de la clase IEWSClient proporcionando credenciales
        IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", username, password, domain);

        ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();
        Console.WriteLine("URI de la Buzón: " + mailboxInfo.MailboxUri);
        string rootUri = client.GetMailboxInfo().RootUri;
        // Listar todas las carpetas del servidor Exchange
        ExchangeFolderInfoCollection folderInfoCollection = client.ListSubFolders(rootUri);
        foreach (ExchangeFolderInfo folderInfo in folderInfoCollection)
        {
            // Llamar al método recursivo para leer mensajes y obtener subcarpetas
            ListMessagesInFolder(client, folderInfo, rootFolder);
        }

        Console.WriteLine("Todos los mensajes descargados.");
    }
    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
    }
}

// Método recursivo para obtener mensajes de carpetas y subcarpetas
private static void ListMessagesInFolder(IEWSClient client, ExchangeFolderInfo folderInfo, string rootFolder)
{
    // Crear la carpeta en disco (mismo nombre que en el servidor de IMAP)
    string currentFolder = rootFolder + "\\" + folderInfo.DisplayName;
    Directory.CreateDirectory(currentFolder);

    // Listar mensajes
    ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(folderInfo.Uri);
    Console.WriteLine("Listando mensajes....");
    int i = 0;
    foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
    {
        // Obtener asunto y otras propiedades del mensaje
        Console.WriteLine("Asunto: " + msgInfo.Subject);

        // Evitar caracteres como ? y :, que no deberían incluirse en un nombre de archivo
        string fileName = msgInfo.Subject.Replace(":", " ").Replace("?", " ");

        MailMessage msg = client.FetchMessage(msgInfo.UniqueUri);
        msg.Save(dataDir + "\\" + fileName + "-" + i + ".msg");
  
        i++;
    }
    Console.WriteLine("============================\n");
    try
    {
        // Si esta carpeta tiene subcarpetas, llamar a este método recursivamente para obtener mensajes
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
    return true; // Ignorar las verificaciones y continuar
}
```

## **Descargando Mensajes de Carpetas Públicas**

El Servidor Microsoft Exchange permite a los usuarios crear carpetas públicas y publicar mensajes en ellas. Para hacerlo a través de su aplicación, use la clase Aspose.Email [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) para conectarse al Servidor Exchange y leer y descargar mensajes y publicaciones de carpetas públicas. El siguiente fragmento de código le muestra cómo leer todas las carpetas públicas, y subcarpetas, y listar y descargar cualquier mensaje encontrado en estas carpetas. Este ejemplo solo funciona con Microsoft Exchange Server 2007 o superior, ya que solo estos soportan EWS.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
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
        Console.WriteLine("Nombre: " + publicFolder.DisplayName);
        Console.WriteLine("Cantidad de Subcarpetas: " + publicFolder.ChildFolderCount);
        ListMessagesFromSubFolder(publicFolder, client);
    }
}

private static void ListMessagesFromSubFolder(ExchangeFolderInfo publicFolder, IEWSClient client)
{
    Console.WriteLine("Nombre de la Carpeta: " + publicFolder.DisplayName);
    ExchangeMessageInfoCollection msgInfoCollection = client.ListMessagesFromPublicFolder(publicFolder);
    foreach (ExchangeMessageInfo messageInfo in msgInfoCollection)
    {
        MailMessage msg = client.FetchMessage(messageInfo.UniqueUri);
        Console.WriteLine(msg.Subject);
        msg.Save(dataDir + msg.Subject + ".msg", SaveOptions.DefaultMsgUnicode);
    }

    // Llamar a este método recursivamente para cualquier subcarpeta
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

## **Moviendo Mensajes**

Puede mover mensajes de correo electrónico de una carpeta a otra con la ayuda de la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) método [Move](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/moveitem/). Toma los parámetros:

- El URI único del mensaje que se va a mover.
- El URI único de la carpeta de destino.

### **Moviendo Mensajes entre Carpetas**

El siguiente fragmento de código le muestra cómo mover un mensaje en una buzón desde la carpeta de Bandeja de Entrada a una carpeta llamada Procesados. En este ejemplo, la aplicación:

1. Lee mensajes de la carpeta de Bandeja de Entrada.
2. Procesa algunos de los mensajes según algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
3. Mueve los mensajes que cumplen con la condición dada a la carpeta procesada.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
// Crear instancia de la clase IEWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// Listar todos los mensajes de la carpeta de Bandeja de Entrada
Console.WriteLine("Listando todos los mensajes de la Bandeja de Entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Mover mensaje a la carpeta "Procesados", después de procesar ciertos mensajes basados en criterios específicos
    if (msgInfo.Subject != null &&
        msgInfo.Subject.ToLower().Contains("procesar este mensaje") == true)
    {
        client.MoveItem(mailboxInfo.DeletedItemsUri, msgInfo.UniqueUri); // EWS
        Console.WriteLine("Mensaje movido...." + msgInfo.Subject);
    }
    else
    {
        // Hacer algo más
    }
}
```

## **Eliminando Mensajes**

Puede eliminar mensajes de correo electrónico de una carpeta con la ayuda de la clase [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/exchangeclient/) método [DeleteMessage](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletemessage/) toma un URI único de un mensaje como parámetro.

El siguiente fragmento de código le muestra cómo eliminar un mensaje de la carpeta de Bandeja de Entrada. Con el fin de realizar este ejemplo, el código:

1. Lee mensajes de la carpeta de Bandeja de Entrada.
2. Procesa mensajes según algunos criterios (en este caso, encontramos una palabra clave en el asunto del mensaje).
3. Elimina el mensaje.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
            
// Crear instancia de la clase IEWSClient proporcionando credenciales
IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

ExchangeMailboxInfo mailboxInfo = client.GetMailboxInfo();

// Listar todos los mensajes de la carpeta de Bandeja de Entrada
Console.WriteLine("Listando todos los mensajes de la Bandeja de Entrada....");
ExchangeMessageInfoCollection msgInfoColl = client.ListMessages(mailboxInfo.InboxUri);
foreach (ExchangeMessageInfo msgInfo in msgInfoColl)
{
    // Eliminar mensaje basado en ciertos criterios
    if (msgInfo.Subject != null && msgInfo.Subject.ToLower().Contains("eliminar") == true)
    {
        client.DeleteItem(msgInfo.UniqueUri, DeletionOptions.DeletePermanently); // EWS
        Console.WriteLine("Mensaje eliminado...." + msgInfo.Subject);
    }
    else
    {
        // Hacer algo más
    }
}
```

## **Copiando Mensajes**

La API de Aspose.Email permite copiar un mensaje de una carpeta a otra utilizando el método [CopyItem](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/copyitem/). La versión sobrecargada de este método devuelve el URI Único del mensaje copiado, como se muestra en este artículo.

### **Copiando un Mensaje a Otra Carpeta**

El siguiente fragmento de código le muestra cómo copiar un mensaje a otra carpeta.

```csharp
// Para ejemplos completos y archivos de datos, por favor dirígete a https://github.com/aspose-email/Aspose.Email-for-.NET
try
{
    // Crear instancia de la clase EWSClient proporcionando credenciales
    IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
    MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-34997 - " + Guid.NewGuid().ToString(), "EMAILNET-34997 Exchange: Copiar un mensaje y obtener referencia al nuevo elemento Copiado");
    string messageUri = client.AppendMessage(message);
    string newMessageUri = client.CopyItem(messageUri, client.MailboxInfo.DeletedItemsUri);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```