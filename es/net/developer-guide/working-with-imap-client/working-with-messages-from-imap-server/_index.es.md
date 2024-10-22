---
title: "Trabajando con Mensajes del Servidor IMAP"
url: /es/net/working-with-messages-from-imap-server/
weight: 20
type: docs
---

## **Obtención de la información de identificación para mensajes recibidos de un buzón de correo**

Al recuperar y procesar mensajes de correo electrónico, puedes obtener los detalles de esos mensajes utilizando sus números de secuencia. Las siguientes características se utilizan para interactuar con un buzón de correo IMAP:

- `Aspose.Email.MailboxInfo` clase - Representa información de identificación sobre un mensaje en un buzón de correo.

    - `Aspose.Email.MailboxInfo.SequenceNumber` propiedad - El número de secuencia de un mensaje.

    - `Aspose.Email.MailboxInfo.UniqueId` propiedad - El ID único de un mensaje.

- `Aspose.Email.MailMessage.ItemId` propiedad - Representa información de identificación sobre el mensaje en un buzón de correo.

El siguiente fragmento de código muestra cómo obtener información de identificación sobre los mensajes:

```cs
using (var client = new ImapClient(imapHost, port, emailAddress, password, securityOption))
{
    var msgs = client.ListMessages("INBOX").Take(5);
    var seqIds = msgs.Select(t => t.SequenceNumber);
    var msgsViaFetch = client.FetchMessages(seqIds);
    
    for (var i = 0; i < 5; i++)
    {
        var thisMsg = msgsViaFetch[i];
        Console.WriteLine($"Message ID:{seqIds.ElementAt(i)} SequenceNumber: {thisMsg.ItemId.SequenceNumber} Subject:{thisMsg.Subject}");
    }
}
```

## **Listado de IDs de Mensajes MIME desde el Servidor**

[ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) proporciona el [MessageId](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/messageid/) MIME para la identificación de mensajes sin extraer el mensaje completo. El siguiente fragmento de código muestra cómo listar el mensaje MIMEId.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.cs" >}}

## **Listado de Mensajes desde el Servidor**

Aspose.Email proporciona una variante sobrecargada de 2 miembros de [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_12) para recuperar un número especificado de mensajes basado en una consulta. El siguiente fragmento de código muestra cómo listar mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ListMessagesWithMaximumNumberOfMessages-ListMessagesWithMaximumNumberOfMessages.cs" >}}

## **Listado de Mensajes desde el Servidor Recursivamente**

El protocolo IMAP soporta el listado de mensajes recursivamente desde una carpeta de buzón. Esto ayuda a listar mensajes de subcarpetas de una carpeta también. El siguiente fragmento de código muestra cómo listar mensajes recursivamente.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.cs" >}}

## **Listado de Mensajes con MultiConexión**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona una propiedad [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) que se puede usar para crear múltiples conexiones para operaciones pesadas. También puedes establecer el número de conexiones que se utilizarán durante el modo de multi-conexión usando [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). El siguiente fragmento de código demuestra el uso del modo de multi-conexión para listar mensajes y compara su rendimiento con el modo de conexión única.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Ten en cuenta que el uso del modo de multi-conexión no garantiza un aumento en el rendimiento.

{{% /alert %}} 

## **Obtener Mensajes en orden descendente**

Aspose.Email proporciona el método [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) que lista mensajes con soporte de paginación. Algunas sobrecargas de [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) aceptan [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) como parámetro. [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) proporciona una propiedad [`AscendingSorting`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) que, cuando se establece en **false**, devuelve correos electrónicos en orden descendente.

El siguiente código de ejemplo demuestra el uso de la propiedad [AscendingSorting](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) de la [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) clase para cambiar el orden de los correos electrónicos.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ChangeOrderOfEmails-1.cs" >}}

## **Recuperar Mensajes del Servidor y Guardar en el disco**

La clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) puede recuperar mensajes de un servidor IMAP y guardar los mensajes en formato EML en un disco local. Los siguientes pasos son necesarios para guardar los mensajes en el disco:

1. Crear una instancia de la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
2. Especificar un nombre de host, puerto, nombre de usuario y contraseña en el [constructor](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor) de ImapClient.
3. Seleccionar la carpeta utilizando el método [SelectFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/selectfolder/#selectfolder/).
4. Llamar al método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) para obtener el objeto [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/).
5. Iterar a través de la colección [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/), llamar al método [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/savemessage/#savemessage/) y proporcionar la ruta de salida y el nombre del archivo.

El siguiente fragmento de código muestra cómo recuperar mensajes de correo electrónico de un servidor y guardarlos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FetchEmailMessagesFromIMAPServer-FetchEmailMessagesFromIMAPServer.cs" >}}

## **Guardando Mensajes en Formato MSG**

[En el ejemplo anterior](#fetch-messages-from-server-and-save-to-disc), los correos electrónicos se guardan en formato EML. Para guardar correos electrónicos en formato MSG, se debe llamar al método [ImapClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessage/#fetchmessage/). Devuelve el mensaje en una instancia de la clase [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). Luego se puede llamar al método [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo guardar mensajes en formato MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SavingMessagesFromIMAPServer-SavingMessagesFromIMAPServer.cs" >}}

## **Grupo de Recuperación de Mensajes**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona un método [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) que acepta una lista de números de secuencia o ID únicos y devuelve una lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El siguiente fragmento de código demuestra el uso del método [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) para recuperar mensajes por números de secuencia y ID únicos.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapFetchGroupMessages-1.cs" >}}

## **Listado de Mensajes con Soporte de Paginación**

En escenarios donde el servidor de correo electrónico contiene una gran cantidad de mensajes en el buzón, a menudo se desea listar o recuperar los mensajes con soporte de paginación. La API Aspose.Email [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) te permite recuperar los mensajes del servidor con soporte de paginación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.cs" >}}

## **Listado de los Adjuntos de Mensajes**

Para obtener información sobre los adjuntos, como nombre y tamaño, sin recuperar los datos del adjunto, prueba las siguientes APIs:

- *Aspose.Email.Clients.Imap.ImapAttachmentInfo* - Representa información sobre un adjunto.
- *Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection* - Representa una colección de la clase [ImapAttachmentInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/).
- *Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)* - Obtiene información para cada adjunto en un mensaje.

El código de ejemplo con los pasos a continuación te mostrará cómo usar las APIs:

1. Llama al método [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/) en el objeto imapClient. Este método devolverá una colección ImapMessageInfoCollection que contiene información sobre los mensajes en el buzón.
2. Itera a través de cada mensaje en la messageInfoCollection utilizando un bucle foreach.
3. Llama al método [ListAttachments()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/#imapclientlistattachments-method) en el objeto imapClient, pasando la propiedad SequenceNumber del objeto mensaje como parámetro. Este método devolverá una ImapAttachmentInfoCollection que contiene información sobre los adjuntos en el mensaje.
4. Itera a través de cada adjunto en la attachmentInfoCollection utilizando un bucle foreach.
5. Dentro del bucle interno, puedes acceder a la información sobre cada adjunto utilizando las propiedades del objeto attachmentInfo. En este ejemplo, el nombre y el tamaño de cada adjunto se registran en la consola utilizando `Console.WriteLine()`.
   
   `Console.WriteLine("Adjunto: {0} (tamaño: {1})", attachmentInfo.Name, attachmentInfo.Size);`
```cs
var messageInfoCollection = imapClient.ListMessages();
    
foreach (var message in messageInfoCollection)
{
    var attachmentInfoCollection = imapClient.ListAttachments(message.SequenceNumber);

    foreach (var attachmentInfo in attachmentInfoCollection)
    {
        Console.WriteLine("Adjunto: {0} (tamaño: {1})", attachmentInfo.Name, attachmentInfo.Size);
    }
}
```

## **Obteniendo Carpetas y Leyendo Mensajes Recursivamente**

En este artículo, se utilizan la mayoría de las características de [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) para crear una aplicación que liste todas las carpetas y subcarpetas recursivamente desde un servidor IMAP. También guarda los mensajes en cada carpeta y subcarpeta en formato MSG en un disco local. En el disco, las carpetas y los mensajes se crean y guardan en la misma estructura jerárquica que en el servidor IMAP. El siguiente fragmento de código muestra cómo obtener la información de los mensajes y subcarpetas de forma recursiva.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ReadMessagesRecursively-ReadMessagesRecursively.cs" >}}

## **Recuperando Parámetros Adicionales como Información Resumida**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrieveExtraParameters-RetrieveExtraParametersAsSummaryInformation.cs" >}}

## **Obteniendo Información de Encabezado List-Unsubscribe**

El encabezado List-Unsubscribe contiene la URL para darse de baja de listas de correo electrónico, por ejemplo, publicidad, boletines, etc. Para obtener el encabezado List-Unsubscribe, utiliza la propiedad [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) de la clase [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/). El siguiente ejemplo muestra el uso de la propiedad [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) para obtener el encabezado List-Unsubscribe.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-GetListUnsubscribeHeader-1.cs" >}}