---
title: "Trabajando con el Buzón de Exchange y Mensajes usando WebDav"
url: /es/net/working-with-exchange-mailbox-and-messages-using-webdav/
weight: 20
type: docs
---

## **Obteniendo Información del Buzón usando WebDav**
La clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) tiene miembros que se pueden usar para obtener información del buzón de un servidor Exchange llamando al método [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index). Devuelve una instancia del tipo [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo). Obtén información del buzón de propiedades como [MailboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/mailboxuri), [InboxUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/inboxuri) y [DraftsUri](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo/properties/draftsuri). Este artículo muestra cómo acceder a la información del buzón directamente desde un servidor Exchange.

Para obtener la información del Buzón de Exchange:

1. Crea una instancia de la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Especifica el servidor Exchange, el nombre de usuario, la contraseña y el dominio en el constructor de [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Llama al método [ExchangeClient.GetMailboxSize()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxsize/index) para obtener el tamaño del buzón.
1. Llama al método [ExchangeClient.GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) para obtener una instancia de la clase [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo).
1. Obtén la información del buzón utilizando las diferentes propiedades de la clase [ExchangeMailboxInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemailboxinfo).

El siguiente fragmento de código muestra cómo obtener información del buzón de Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromExchangeServer.cs" >}}
## **Enviando Mensajes de Correo Electrónico**
Puedes enviar mensajes de correo electrónico usando un servidor Exchange con la ayuda de las herramientas en Aspose.Email.Exchange. El método [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) acepta una instancia de [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage) como parámetro y envía el correo electrónico. Este artículo explica cómo enviar mensajes de correo electrónico utilizando un servidor Exchange.
### **Enviando Mensajes de Correo Electrónico Usando el Servidor Exchange**
Para enviar correos electrónicos usando un servidor Exchange:

1. Crea una instancia de la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Especifica el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Crea una instancia de la clase [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage).
1. Especifica las propiedades de de, para, asunto y otras [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage).
1. Llama al método [ExchangeClient.Send()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/send) para enviar el correo electrónico.

El siguiente fragmento de código muestra cómo enviar mensajes de correo electrónico usando el servidor Exchange.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SendEmailMessagesUsingExchangeServer-SendEmailMessagesUsingExchangeServer.cs" >}}
## **Leyendo Correos Electrónicos del Buzón de Otro Usuario**
Algunas cuentas en servidores Exchange tienen derecho a acceder a múltiples buzones, y algunos usuarios tienen múltiples cuentas de correo electrónico en el mismo servidor Exchange. En ambos casos, los usuarios pueden acceder a los buzones de otros usuarios utilizando Aspose.Email para .NET. Esta API proporciona un mecanismo para acceder a carpetas y correos electrónicos de otros buzones usando la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient). Esta funcionalidad se puede lograr utilizando el método sobrecargado [GetMailboxInfo()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/getmailboxinfo/index) y proporcionando la dirección de correo electrónico del usuario como parámetro.

El siguiente fragmento de código muestra cómo usar la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) para acceder a otro buzón.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-AccessAnotherMailboxUsingExchangeClient-AccessAnotherMailboxUsingExchangeClient.cs" >}}
## **Listando Mensajes**
Se puede obtener una lista de los mensajes de correo electrónico en un buzón de Exchange llamando al método [ExchangeClient.ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index). Obtén la información básica sobre los mensajes, como asunto, de, a y ID del mensaje, usando el método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index).
### **Listado Simple de Mensajes**
Para listar los mensajes en un buzón de Exchange:

1. Crea una instancia de la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Llama al método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) y crea una colección de mensajes.
1. Itera a través de la colección y muestra la información del mensaje.

El siguiente fragmento de código muestra cómo conectarse al buzón de Exchange y obtener una lista de mensajes de la carpeta de entrada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListExchangeServerMessages-ListExchangeServerMessages.cs" >}}
### **Listando Mensajes de Diferentes Carpetas**
Los fragmentos de código anteriores listan todos los mensajes en la carpeta de Entrada. También es posible obtener la lista de mensajes de otras carpetas. El método [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) acepta una URI de carpeta como parámetro. Siempre que la URI de la carpeta sea válida, puedes obtener la lista de mensajes de esa carpeta. Usa la propiedad ExchangeClient.MailboxInfo.xxxFolderUri para obtener la URI de diferentes carpetas. El resto del código es el mismo que para obtener una lista de mensajes. El siguiente fragmento de código muestra cómo listar mensajes de diferentes carpetas usando [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesFromDifferentFolders-ListMessagesFromDifferentFolders.cs" >}}
### **Listando Mensajes por ID**
El fragmento de código anterior usó el método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para listar todos los mensajes en una carpeta de buzón del servidor Exchange especificado. Si conoces de antemano el ID del mensaje, puedes obtener el mensaje usando el método [ListMessagesbyId()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessagesbyid) . Para obtener el mensaje, pasa la URI de la carpeta y el ID del mensaje. Este escenario es útil cuando ya conoces el ID del mensaje, por ejemplo, cuando los ID de los mensajes están guardados en la base de datos. El siguiente fragmento de código muestra cómo listar mensajes por ID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ListMessagesByID-ListMessagesByID.cs" >}}
## **Guardando Mensajes**
Este tema muestra cómo obtener mensajes de un buzón de servidor Exchange y guardarlos en el disco en formatos EML y MSG:

- Guardar como EML en disco.
- Guardar en un flujo de memoria.
- Guardar como MSG.
### **Guardando Mensajes en EML**
Para obtener mensajes y guardarlos en formato EML:

1. Crea una instancia de la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Proporciona el nombre del servidor, el nombre de usuario, la contraseña y el dominio.
1. Llama al método [ExchangeClient.ListMessages()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para obtener una instancia de la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Itera a través de la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) para obtener la URI única de cada mensaje.
1. Llama al método [ExchangeClient.SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) y pasa la URI única como parámetro.
1. Proporciona al método [SaveMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) una ruta donde deseas guardar el archivo.

El siguiente fragmento de código muestra cómo guardar mensajes en EML.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-ExchangeClientSaveMessagesInEMLFormat-ExchangeClientSaveMessagesInEMLFormat.cs" >}}
### **Guardando Mensajes en un Flujo de Memoria**
En lugar de guardar archivos EML en disco, es posible guardarlos en un flujo de memoria. Esto es útil cuando deseas guardar el flujo en algún lugar de almacenamiento como una base de datos. Una vez que el flujo se ha guardado en una base de datos, puedes recargar el archivo EML en la clase [MailMessage](https://apireference.aspose.com/net/email/aspose.email/mailmessage). El siguiente fragmento de código muestra cómo guardar mensajes desde un buzón de servidor Exchange en un flujo de memoria.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesToMemoryStream-SaveMessagesToMemoryStream.cs" >}}
### **Guardando Mensajes en Formato MSG**
El método [ExchangeClient.SaveMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/savemessage/index) puede guardar directamente el mensaje en formato EML. Para guardar los mensajes en formato MSG, primero llama al método [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) que devuelve una instancia de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). Luego llama al método [MailMessage.Save()](https://apireference.aspose.com/email/net/aspose.email/mailmessage/methods/save/index) para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo obtener mensajes de un buzón de servidor Exchange y guardarlos en formato MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-SaveMessagesInMSGFormatExchangeClient-SaveMessagesInMSGFormatExchangeClient.cs" >}}
## **Obteniendo Mensajes de un Buzón de Servidor Exchange**
Listar mensajes en un servidor Exchange utilizó el método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para obtener una lista de mensajes de un buzón de servidor Exchange. El método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) obtiene información básica sobre los mensajes, por ejemplo, el asunto, el ID del mensaje, de y a. Para obtener los detalles completos del mensaje, Aspose.Email.Exchange proporciona el método [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage). Este método acepta la URI del mensaje como parámetro y devuelve una instancia de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). La clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) proporciona detalles del mensaje como cuerpo, encabezados y archivos adjuntos. Para obtener mensajes del Buzón de Exchange:

1. Crea una instancia del tipo [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient).
1. Especifica mailboxUri, nombre de usuario, contraseña y dominio.
1. Llama a [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) para obtener el [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection).
1. Itera a través de la colección [ExchangeMessagesInfoCollection](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfocollection) para obtener los valores [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri).
1. Llama a [ExchangeClient.FetchMessage()](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/fetchmessage) y pasa [ExchangeMessageInfo.UniqueURI](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo/properties/uniqueuri) como parámetro.

El siguiente fragmento de código muestra cómo conectarse al buzón del servidor Exchange y obtener todos los mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-FetchMessageUsingExchangeClient-FetchMessageUsingExchangeClient.cs" >}}
## **Pre-Fetch Tamaño del Mensaje**
Microsoft Outlook InterOp proporciona la función de recuperar el tamaño del mensaje antes de realmente obtener el mensaje completo del servidor. En el caso de la API Aspose.Email, la información resumen recuperada del servidor Exchange está representada por la clase [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). Proporciona la misma función de recuperar el tamaño del mensaje usando la propiedad Size. Para recuperar el tamaño del mensaje, se utiliza la llamada estándar al método [ListMessages](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/listmessages/index) del ExchangeClient que recupera la colección de [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo). El siguiente fragmento de código muestra cómo mostrar el tamaño del mensaje utilizando la clase [ExchangeMessageInfo](https://apireference.aspose.com/net/email/aspose.email.clients.exchange/exchangemessageinfo).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-PreFetchMessageSizeUsingExchangeClient-PreFetchMessageSizeUsingExchangeClient.cs" >}}
## **Moviendo Mensajes**
Puedes mover mensajes de correo electrónico de una carpeta a otra con la ayuda de la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient) y el método [MoveItems](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/moveitems/index). Toma los parámetros:

- La URI única del mensaje que se va a mover.
- La URI única de la carpeta de destino.
### **Moviendo Mensajes entre Carpetas**
El siguiente fragmento de código muestra cómo mover un mensaje en un buzón de la carpeta de Entrada a una carpeta llamada Procesados. En este ejemplo, la aplicación:

1. Lee los mensajes de la carpeta de Entrada.
1. Procesa algunos de los mensajes según ciertos criterios (en este ejemplo, buscamos una palabra clave en el asunto del mensaje).
1. Mueve los mensajes que cumplen la condición dada a la carpeta procesada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-MoveMessageFromOneFolderToAnotherUsingExchangeClient-MoveMessageFromOneFolderToAnotherUsingExchangeClient.cs" >}}
## **Eliminando Mensajes**
Puedes eliminar mensajes de correo electrónico de una carpeta con la ayuda del método [DeleteMessage](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient/methods/deletemessage/index) de la clase [ExchangeClient](https://apireference.aspose.com/net/email/aspose.email.clients.exchange.dav/exchangeclient). Toma la URI única del mensaje como parámetro.
### **Eliminando Mensajes de un Servidor Exchange**
El siguiente fragmento de código muestra cómo eliminar un mensaje de la carpeta de Entrada. Para el propósito de este ejemplo, el código:

1. Lee mensajes de la carpeta de Entrada.
1. Procesa los mensajes según ciertos criterios (en este ejemplo, buscamos una palabra clave en el asunto del mensaje).
1. Elimina el mensaje.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.cs" >}}