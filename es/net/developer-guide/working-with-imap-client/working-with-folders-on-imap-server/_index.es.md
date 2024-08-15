---
title: "Trabajo con carpetas en un servidor IMAP"
url: /es/net/working-with-folders-on-imap-server/
weight: 60
type: docs
---


## **Obtención de información de carpetas**

Obtener información sobre las carpetas de un servidor IMAP es muy fácil con Aspose.Email. Llame al [ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listfolders/#listfolders/) método del [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) clase. Devuelve un objeto de [ImapFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection/) tipo. Recorra esta colección y obtenga información sobre las carpetas individuales de un bucle. El método está sobrecargado. Puede pasar un nombre de carpeta como parámetro para obtener una lista de subcarpetas. El siguiente fragmento de código muestra cómo obtener información de carpetas de un servidor IMAP mediante Aspose.Email mediante el método descrito en la información.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GettingFoldersInformation-GettingFoldersInformation.cs" >}}

## **Eliminar carpetas y cambiarles el nombre**

Una carpeta de un servidor IMAP se puede eliminar o renombrar en una sola línea con Aspose.Correo electrónico:

- The [`DeleteFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolder/#deletefolder/) el método acepta el nombre de la carpeta como parámetro.
- Para el [`RenameFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/renamefolder/#renamefolder/) método, debe pasar el nombre de la carpeta actual y el nombre de la nueva carpeta.

El siguiente fragmento de código muestra cómo eliminar una carpeta de un servidor IMAP y cómo cambiar el nombre de una carpeta. Cada operación se realiza con una línea de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-DeletingAndRenamingFolders-DeletingAndRenamingFolders.cs" >}}

## **Añadir un mensaje nuevo a una carpeta**

Puede añadir un mensaje nuevo a la carpeta mediante el [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) and [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) clases. Primero crea un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) objeta proporcionando al sujeto valores de ida y vuelta. A continuación, suscríbase a una carpeta y añada el mensaje a ella. En el siguiente fragmento de código, se muestra cómo añadir un mensaje nuevo a una carpeta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-AddingNewMessage-AddingNewMessageToFolder.cs" >}}

## **Agregue varios mensajes con soporte para conexiones múltiples**

Puede añadir varios mensajes mediante el [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) método proporcionado por el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) clases. El [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) el método acepta una lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y la agrega a la carpeta actual si la carpeta no se proporciona como parámetro. iMapClient también admite el modo multiconexión para operaciones con cargas pesadas. El siguiente fragmento de código muestra cómo agregar varios mensajes mediante el modo MultiConnection.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapGroupAppendWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}}

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Mover los mensajes a otra carpeta del buzón**

Aspose.Email para.NET permite mover mensajes de una carpeta de buzones de correo a otra mediante el [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) API. El [MoveMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/movemessage/#movemessage/) El método utiliza el identificador único del mensaje y el nombre de la carpeta de destino para mover un mensaje a la carpeta de destino. El siguiente fragmento de código muestra cómo mover los mensajes a otra carpeta del buzón.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-MoveMessage-MoveMessage.cs" >}}

## **Copiar mensajes a otra carpeta de buzones**

La API Aspose.Email ofrece la capacidad de copiar mensajes de una carpeta de buzones de correo a otra. Permite copiar un solo mensaje o varios mensajes mediante el [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessage/#copymessage/) and [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) métodos. El [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) El método proporciona la capacidad de copiar varios mensajes de la carpeta de origen de un buzón a la carpeta de buzones de destino. El siguiente fragmento de código muestra cómo copiar los mensajes a otra carpeta del buzón.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CopyMultipleMessagesFromOneFoldertoAnother-CopyMultipleMessagesFromOneFoldertoAnother.cs" >}}

## **Trabajar con carpetas de buzones de correo de uso especial**

Algunos almacenes de mensajes IMAP incluyen buzones de correo de uso especial, como los que se utilizan para guardar borradores de mensajes o mensajes enviados. Muchos clientes de correo permiten a los usuarios especificar dónde deben colocarse los borradores de los mensajes enviados, pero para configurarlos es necesario que el usuario sepa qué buzones ha reservado el servidor para estos fines. Aspose.Email puede identificar estos buzones de uso especial mediante el [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) clase para que sea más fácil trabajar con ellos. En el siguiente ejemplo de código se muestra cómo acceder a estos buzones de uso especial mediante el [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) class.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapSpecialUseMailboxes-1.cs" >}}
