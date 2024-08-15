---
title: "Trabajando con mensajes del servidor IMAP"
url: /es/net/working-with-messages-from-imap-server/
weight: 20
type: docs
---

## **Obtener la información de identificación de los mensajes recibidos de un buzón**

Al recuperar y procesar mensajes de correo electrónico, puede obtener los detalles de esos mensajes utilizando sus números de secuencia.
Las siguientes funciones se utilizan para interactuar con un buzón IMAP:

- `Aspose.Email.MailboxInfo` clase: representa la información de identificación sobre el mensaje de un buzón.

    - `Aspose.Email.MailboxInfo.SequenceNumber` propiedad: el número de secuencia de un mensaje.

    - `Aspose.Email.MailboxInfo.UniqueId` propiedad: el identificador único de un mensaje.

- `Aspose.Email.MailMessage.ItemId` propiedad: representa la información de identificación sobre el mensaje de un buzón.

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

## **Listado de identificadores de mensajes MIME del servidor**

[ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) proporciona el MIME [MessageId](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/messageid/) para identificar el mensaje sin extraer el mensaje completo. En el siguiente fragmento de código, se muestra cómo incluir MIME MessageID.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMIMEMessageIdInImapMessageInfo-ListingMIMEMessageIdInImapMessageInfo.cs" >}}

## **Listado de mensajes del servidor**

Aspose.Email ofrece una variante sobrecargada para 2 miembros de [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages_12) para recuperar un número específico de mensajes en función de una consulta. En el siguiente fragmento de código, se muestra cómo enumerar los mensajes.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ListMessagesWithMaximumNumberOfMessages-ListMessagesWithMaximumNumberOfMessages.cs" >}}

## **Listar los mensajes del servidor de forma recursiva**

El protocolo IMAP admite la enumeración recursiva de los mensajes de una carpeta de buzones de correo. Esto también ayuda a enumerar los mensajes de las subcarpetas de una carpeta. En el siguiente fragmento de código, se muestra cómo enumerar los mensajes de forma recursiva.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesRecursively-ListingMessagesRecursively.cs" >}}

## **Listar mensajes con MultiConnection**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona un [UseMultiConnection](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usemulticonnection/) propiedad que se puede usar para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se usarán durante el modo multiconexión utilizando [ImapClient.ConnectionsQuantity](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/connectionsquantity/). El siguiente fragmento de código muestra el uso del modo multiconexión para enumerar los mensajes y compara su rendimiento con el modo de conexión única.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapListMessagesWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Recibe los mensajes en orden descendente**

Aspose.Email proporciona [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) método que enumera los mensajes con soporte de paginación. Algunas sobrecargas de [`ImapClient.ListMessagesByPage`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessagesbypage/#listmessagesbypage/) accept [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) como parámetro. [`PageSettings`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) proporciona un [`AscendingSorting`](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) propiedad que, cuando se establece en **false**, devuelve los correos electrónicos en orden descendente.

El siguiente código de ejemplo demuestra el uso de [AscendingSorting](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/ascendingsorting/) propiedad del [PageSettings](https://reference.aspose.com/email/net/aspose.email.clients.imap/pagesettings/) clase para cambiar el orden de los correos electrónicos.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ChangeOrderOfEmails-1.cs" >}}

## **Recuperar mensajes del servidor y guardarlos en el disco**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) La clase puede obtener mensajes de un servidor IMAP y guardar los mensajes en formato EML en un disco local. Se requieren los siguientes pasos para guardar los mensajes en el disco:

1. Crea una instancia del [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Especifique un nombre de host, un puerto, un nombre de usuario y una contraseña en IMAPClient [constructor](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor).
1. Seleccione la carpeta mediante [SelectFolder()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/selectfolder/#selectfolder/) method.
1. Llame al [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/#listmessages) método para obtener el [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) object.
1. Recorra en iteración el [ImapMessageInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfocollection/) colección, llame al [SaveMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/savemessage/#savemessage/) método y proporcione la ruta de salida y el nombre del archivo.

El siguiente fragmento de código muestra cómo obtener mensajes de correo electrónico de un servidor y guardarlos.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-FetchEmailMessagesFromIMAPServer-FetchEmailMessagesFromIMAPServer.cs" >}}

## **Guardar mensajes en formato MSG**

[En el ejemplo anterior](#fetch-messages-from-server-and-save-to-disc), los correos electrónicos se guardan en formato EML. Para guardar los correos electrónicos en formato MSG, el [ImapClient.FetchMessage()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessage/#fetchmessage/) es necesario llamar al método. Devuelve el mensaje en una instancia del [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) clase. El [MailMessage.Save()](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save/) Luego se puede llamar al método para guardar el mensaje en MSG. El siguiente fragmento de código muestra cómo guardar mensajes en formato MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SavingMessagesFromIMAPServer-SavingMessagesFromIMAPServer.cs" >}}

## **Mensajes de búsqueda grupales**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) proporciona un [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) método que acepta números de secuencia iterables o ID únicos y devuelve una lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). El siguiente fragmento de código demuestra el uso del [FetchMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/fetchmessages/#fetchmessages/) método para buscar mensajes por números de secuencia e ID único.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapFetchGroupMessages-1.cs" >}}


## **Listar mensajes con soporte de paginación**

En situaciones en las que el servidor de correo electrónico contiene una gran cantidad de mensajes en el buzón, a menudo se desea enumerar o recuperar los mensajes con soporte de paginación. Aspose.Email API [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) le permite recuperar los mensajes del servidor con soporte de paginación.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ListingMessagesWithPagingSupport-ListingMessagesWithPagingSupport.cs" >}}

## **Listar los archivos adjuntos de los mensajes**

Para obtener información sobre los archivos adjuntos, como el nombre y el tamaño, sin obtener los datos de los archivos adjuntos, prueba las siguientes API:

- *Aspose.Email.Clients.Imap.ImapAttachmentInfo* - Representa la información de un adjunto.
- *Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection* - Representa una colección de [ImapAttachmentInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) class.
- *Aspose.Email.Clients.IMAP.ListAttachments (int SequenceNumber)* - Obtiene la información de cada adjunto de un mensaje.

El ejemplo de código con los pasos que se indican a continuación le mostrará cómo usar las API:

1. Llame al [ListMessages()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listmessages/) método en el objeto ImapClient. Este método devolverá una colección IMAPMessageInfoCollection que contiene información sobre los mensajes del buzón.
2. Revisa en iteración cada mensaje de la colección MessageInfo mediante un bucle foreach.
3. Llame al [ListAttachments()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/#imapclientlistattachments-method) método en el objeto ImapClient, pasando la propiedad SequenceNumber del objeto de mensaje como parámetro. Este método devolverá una colección IMAPAttachmentInfoCollection que contiene información sobre los archivos adjuntos del mensaje.
4. Revisa todos los datos adjuntos de la colección AttachmentInfo mediante un bucle foreach.
5. Dentro del bucle interno, puede acceder a la información sobre cada adjunto mediante las propiedades del objeto AttachmentInfo. En este ejemplo, el nombre y el tamaño de cada archivo adjunto se registran en la consola mediante `Console.WriteLine()`.
  
   `Console.WriteLine("Attachment: {0} (size: {1})", attachmentInfo.Name, attachmentInfo.Size);`
```cs
var messageInfoCollection = imapClient.ListMessages();
   
foreach (var message in messageInfoCollection)
{
    var attachmentInfoCollection = imapClient.ListAttachments(message.SequenceNumber);

    foreach (var attachmentInfo in attachmentInfoCollection)
    {
        Console.WriteLine("Attachment: {0} (size: {1})", attachmentInfo.Name, attachmentInfo.Size);
    }
}
```

## **Obtener carpetas y leer mensajes de forma recursiva**

En este artículo, la mayoría de los [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) las funciones se utilizan para crear una aplicación que lista todas las carpetas y subcarpetas de forma recursiva de un servidor IMAP. También guarda los mensajes de cada carpeta y subcarpeta en formato MSG en un disco local. En el disco, las carpetas y los mensajes se crean y guardan en la misma estructura jerárquica que en el servidor IMAP. El siguiente fragmento de código muestra cómo obtener la información de los mensajes y las subcarpetas de forma recursiva.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ReadMessagesRecursively-ReadMessagesRecursively.cs" >}}

## **Recuperación de parámetros adicionales como información resumida**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetrieveExtraParameters-RetrieveExtraParametersAsSummaryInformation.cs" >}}

## **Obtener información sobre el encabezado de la lista para cancelar la suscripción**

El encabezado List-Unsubscribe contiene la URL para cancelar la suscripción a las listas de correo electrónico, por ejemplo, anuncios, boletines informativos, etc. Para obtener el encabezado List-Unsubscribe, utilice el [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) propiedad del [ImapMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageinfo/) clase. El siguiente ejemplo muestra el uso de [ListUnsubscribe](https://reference.aspose.com/email/net/aspose.email.clients/messageinfobase/listunsubscribe/) propiedad para obtener el encabezado List-Unsubscribe.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-GetListUnsubscribeHeader-1.cs" >}}
