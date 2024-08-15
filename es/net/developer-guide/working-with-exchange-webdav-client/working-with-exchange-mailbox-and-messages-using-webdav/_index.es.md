---
title: "Trabajar con el buzón y los mensajes de Exchange mediante WebDAV"
url: /es/net/working-with-exchange-mailbox-and-messages-using-webdav/
weight: 20
type: docs
---


## **Obtención de información de buzones mediante WebDAV**
The [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) la clase tiene miembros que se pueden usar para obtener información de buzones de un servidor de Exchange llamando al [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) método. Devuelve una instancia de tipo [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo). Obtenga información sobre los buzones de correo de propiedades como [MailboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/mailboxuri), [InboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/inboxuri), y [DraftsUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/draftsuri). En este artículo se muestra cómo acceder a la información de los buzones directamente desde un servidor Exchange.

Para obtener la información del buzón de Exchange:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Especifique el servidor Exchange, el nombre de usuario, la contraseña y el dominio en [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) constructor.
1. Llame al [ExchangeClient.GetMailboxSize()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxsize/index) método para obtener el tamaño del buzón.
1. Llame al [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) método para obtener una instancia del [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo) class.
1. Obtenga la información del buzón de correo mediante el [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo) diferentes propiedades de la clase.

El siguiente fragmento de código muestra cómo obtener la información de los buzones de correo de Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromExchangeServer.cs" >}}
## **Envío de mensajes de correo electrónico**
Puede enviar mensajes de correo electrónico mediante un servidor de Exchange con la ayuda de las herramientas de Aspose.Email.Exchange. El [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) el método acepta un [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) instancia como parámetro y envía el correo electrónico. En este artículo se explica cómo enviar mensajes de correo electrónico mediante un servidor de Exchange.
### **Envío de mensajes de correo electrónico mediante Exchange Server**
Para enviar correos electrónicos mediante un servidor Exchange:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Especifique el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Crea una instancia del [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) class.
1. Especifique el origen, el destino, el asunto y otros [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) properties.
1. Llame al [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) método para enviar el correo electrónico.

El siguiente fragmento de código muestra cómo enviar mensajes de correo electrónico mediante Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendEmailMessagesUsingExchangeServer-SendEmailMessagesUsingExchangeServer.cs" >}}
## **Lectura de correos electrónicos del buzón de otro usuario**
Algunas cuentas de los servidores de Exchange tienen derecho a acceder a varios buzones de correo y algunos usuarios tienen varias cuentas de correo electrónico en el mismo servidor de Exchange. En ambos casos, los usuarios pueden acceder a los buzones de otros usuarios mediante Aspose.Email para.NET. Esta API proporciona un mecanismo para acceder a las carpetas y correos electrónicos de otros buzones de correo mediante [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) clase. Esta funcionalidad se puede lograr utilizando el sistema sobrecargado [GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) método y proporcionar la dirección de correo electrónico del usuario como parámetro.

El siguiente fragmento de código muestra cómo usar el [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) clase para acceder a otro buzón.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-AccessAnotherMailboxUsingExchangeClient-AccessAnotherMailboxUsingExchangeClient.cs" >}}
## **Publicar mensajes**
Para obtener una lista de los mensajes de correo electrónico de un buzón de Exchange, llame al [ExchangeClient.ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) método. Obtenga la información básica sobre los mensajes, como el asunto, el origen y el identificador del mensaje, mediante el [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) method.
### **Listado de mensajes simples**
Para enumerar los mensajes de un buzón de Exchange:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Llame al [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) método y crear una colección de mensajes.
1. Recorre la colección y muestra la información del mensaje.

El siguiente fragmento de código muestra cómo conectarse al buzón de Exchange y obtener una lista de los mensajes de la carpeta Bandeja de entrada.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListExchangeServerMessages-ListExchangeServerMessages.cs" >}}
### **Listar mensajes de diferentes carpetas**
Los fragmentos de código anteriores enumeran todos los mensajes de la carpeta Bandeja de entrada. También es posible obtener la lista de mensajes de otras carpetas. El [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) el método acepta un URI de carpeta como parámetro. Mientras el URI de la carpeta sea válido, puede obtener la lista de mensajes de esa carpeta. Utilice la propiedad ExchangeClient.MailboxInfo.xxxFolderURI para obtener el URI de las distintas carpetas. El resto del código es el mismo que para obtener una lista de mensajes. En el siguiente fragmento de código, se muestra cómo enumerar los mensajes de diferentes carpetas mediante [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesFromDifferentFolders-ListMessagesFromDifferentFolders.cs" >}}
### **Listar mensajes por ID**
El fragmento de código anterior utilizó el [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) método para enumerar todos los mensajes de una carpeta de buzones de correo de Exchange Server especificada. Si conoce de antemano el identificador de un mensaje, puede obtener el mensaje mediante el [ListMessagesbyId()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessagesbyid) método. Para recibir el mensaje, pasa el URI de la carpeta y el ID del mensaje. Este escenario es útil cuando ya conoces el ID del mensaje, por ejemplo, cuando los ID de los mensajes se guardan en la base de datos. En el siguiente fragmento de código, se muestra cómo enumerar los mensajes por ID.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesByID-ListMessagesByID.cs" >}}
## **Guardar mensajes**
En este tema se muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en el disco en formatos EML y MSG:

- Guardar como EML en el disco.
- Guardar en la secuencia de memoria.
- Guardar como MSG.
### **Guardar mensajes en EML**
Para obtener mensajes y guardarlos en formato EML:

1. Crea una instancia del [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class.
1. Proporcione el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llame al [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) método para obtener una instancia del [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) collection.
1. Recorre el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) colección para obtener la URI única de cada mensaje.
1. Llame al [ExchangeClient.SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) método y pase la URI única como parámetro.
1. Proporcione el [SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) método con una ruta al lugar donde desea guardar el archivo.

El siguiente fragmento de código muestra cómo guardar mensajes en EML.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ExchangeClientSaveMessagesInEMLFormat-ExchangeClientSaveMessagesInEMLFormat.cs" >}}
### **Guardar mensajes en un flujo de memoria**
En lugar de guardar los archivos EML en el disco, es posible guardarlos en una secuencia de memoria. Esto es útil cuando quieres guardar la transmisión en alguna ubicación de almacenamiento, como una base de datos. Una vez guardada la transmisión en una base de datos, puede volver a cargar el archivo EML en [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) clase. El siguiente fragmento de código muestra cómo guardar los mensajes de un buzón de Exchange Server en un flujo de memoria.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesToMemoryStream-SaveMessagesToMemoryStream.cs" >}}
### **Guardar mensajes en formato MSG**
The [ExchangeClient.SaveMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) El método puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llame al [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) método que devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) clase. Entonces llama al [MailMessage.Save()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index) método para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo obtener mensajes de un buzón de Exchange Server y guardarlos en formato MSG.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesInMSGFormatExchangeClient-SaveMessagesInMSGFormatExchangeClient.cs" >}}
## **Obtener mensajes de un buzón de correo de Exchange Server**
Al enumerar los mensajes de un servidor Exchange, se utilizó el [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) método para obtener una lista de mensajes de un buzón de Exchange Server. El [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) El método obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, el origen y el destino. Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) método. Este método acepta el URI del mensaje como parámetro y devuelve una instancia del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) clase. El [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) La clase luego proporciona detalles del mensaje como el cuerpo, los encabezados y los archivos adjuntos. Para obtener mensajes del buzón de Exchange Server:

1. Crear una instancia de tipo [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Especifique la URI del buzón, el nombre de usuario, la contraseña y el dominio.
1. Call [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para obtener el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Recorre el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) colección para obtener [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) values.
1. Call [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) y pase  [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) como parámetro.

El siguiente fragmento de código muestra cómo se conecta al buzón de correo de Exchange Server y obtiene todos los mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FetchMessageUsingExchangeClient-FetchMessageUsingExchangeClient.cs" >}}
## **Tamaño del mensaje de captura previa**
Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de obtener el mensaje completo del servidor. En el caso de la API Aspose.Email, la información resumida recuperada del servidor Exchange está representada por [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo) clase. Proporciona la misma función de recuperar el tamaño del mensaje mediante la propiedad Size. Para recuperar el tamaño del mensaje, la llamada estándar a ExchangeClient [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) se utiliza para recuperar la colección de [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). En el siguiente fragmento de código se muestra cómo mostrar el tamaño de los mensajes mediante el [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo) class.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-PreFetchMessageSizeUsingExchangeClient-PreFetchMessageSizeUsingExchangeClient.cs" >}}
## **Mensajes en movimiento**
Puede mover los mensajes de correo electrónico de una carpeta a otra con la ayuda del [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class [MoveItems](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/moveitems/index) método. Toma los parámetros:

- El URI único del mensaje que se va a mover.
- El URI único de la carpeta de destino.
### **Mover mensajes entre carpetas**
El siguiente fragmento de código muestra cómo mover un mensaje de un buzón de la carpeta Bandeja de entrada a una carpeta denominada Procesado. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa algunos de los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen la condición dada a la carpeta procesada.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-MoveMessageFromOneFolderToAnotherUsingExchangeClient-MoveMessageFromOneFolderToAnotherUsingExchangeClient.cs" >}}
## **Eliminar mensajes**
Puede eliminar los mensajes de correo electrónico de una carpeta con la ayuda del [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) class [DeleteMessage](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/deletemessage/index) método. Toma el URI único del mensaje como parámetro.
### **Eliminar mensajes de un servidor Exchange**
El siguiente fragmento de código muestra cómo eliminar un mensaje de la carpeta Bandeja de entrada. Para este ejemplo, el código:

1. Lee los mensajes de la carpeta Bandeja de entrada.
1. Procesa los mensajes en función de algunos criterios (en este ejemplo, encontramos una palabra clave en el asunto del mensaje).
1. Elimine el mensaje.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.cs" >}}
