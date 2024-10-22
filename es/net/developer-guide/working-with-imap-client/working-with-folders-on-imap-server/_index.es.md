---
title: "Trabajando con Carpetas en el Servidor IMAP"
url: /es/net/working-with-folders-on-imap-server/
weight: 60
type: docs
---


## **Obteniendo Información de Carpetas**

Obtener información sobre carpetas de un servidor IMAP es muy fácil con Aspose.Email. Llama al [método ListFolders()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listfolders/#listfolders/) de la clase [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Devuelve un objeto del tipo [ImapFolderInfoCollection](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection/). Itera a través de esta colección y obtén información sobre carpetas individuales en un bucle. El método está sobrecargado. Puedes pasar un nombre de carpeta como parámetro para obtener una lista de subcarpetas. El siguiente fragmento de código muestra cómo obtener información de carpeta de un servidor IMAP utilizando Aspose.Email con el método descrito en la información.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-GettingFoldersInformation-GettingFoldersInformation.cs" >}}

## **Eliminando y Renombrando Carpetas**

Una carpeta en un servidor IMAP se puede eliminar o renombrar en una sola línea con Aspose.Email:

- El método [`DeleteFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/deletefolder/#deletefolder/) acepta el nombre de la carpeta como parámetro.
- Para el método [`RenameFolder()`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/renamefolder/#renamefolder/), necesitas pasar el nombre actual de la carpeta y el nuevo nombre de la carpeta.

El siguiente fragmento de código muestra cómo eliminar una carpeta de un servidor IMAP y cómo renombrar una carpeta. Cada operación se realiza con una sola línea de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-DeletingAndRenamingFolders-DeletingAndRenamingFolders.cs" >}}

## **Agregando un Nuevo Mensaje en una Carpeta**

Puedes agregar un nuevo mensaje a la carpeta utilizando las clases [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). Primero crea un objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) proporcionando los valores de asunto, para y de. Luego suscríbete a una carpeta y agrega el mensaje a ella. El siguiente fragmento de código muestra cómo agregar un nuevo mensaje en una carpeta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-AddingNewMessage-AddingNewMessageToFolder.cs" >}}

## **Agregar Múltiples Mensajes con Soporte de MultiConexión**

Puedes agregar múltiples mensajes utilizando el método [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) proporcionado por las clases [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). El método [AppendMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/appendmessages/#appendmessages/) acepta una lista de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) y la agrega a la carpeta actual si la carpeta no se proporciona como parámetro. ImapClient también admite el modo de MultiConexión para operaciones de carga pesada. El siguiente fragmento de código muestra cómo agregar múltiples mensajes utilizando el modo de MultiConexión.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapGroupAppendWithMultiConnection-1.cs" >}}

{{% alert color="primary" %}} 

Ten en cuenta que el uso del modo de multiconexión no garantiza un aumento en el rendimiento.

{{% /alert %}} 

## **Mover Mensajes a Otra Carpeta de Correo**

Aspose.Email para .NET permite mover mensajes de una carpeta de correo a otra utilizando la API [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/). El método [MoveMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/movemessage/#movemessage/) utiliza el ID único del mensaje y el nombre de la carpeta de destino para mover un mensaje a la carpeta de destino. El siguiente fragmento de código muestra cómo mover mensajes a otra carpeta de correo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-MoveMessage-MoveMessage.cs" >}}

## **Copiar Mensajes a Otra Carpeta de Correo**

La API de Aspose.Email proporciona la capacidad de copiar mensajes de una carpeta de correo a otra. Permite copiar un solo mensaje así como múltiples mensajes utilizando los métodos [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessage/#copymessage/) y [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/). El método [CopyMessages](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/copymessages/#copymessages/) proporciona la capacidad de copiar múltiples mensajes de la carpeta de origen de un buzón a la carpeta de destino. El siguiente fragmento de código muestra cómo copiar mensajes a otra carpeta de correo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-CopyMultipleMessagesFromOneFoldertoAnother-CopyMultipleMessagesFromOneFoldertoAnother.cs" >}}

## **Trabajando con Carpetas de Buzón de Uso Especial**

Algunos almacenes de mensajes IMAP incluyen buzones de uso especial, como aquellos utilizados para mantener borradores o mensajes enviados. Muchos clientes de correo permiten a los usuarios especificar dónde deberían colocarse los mensajes borradores o enviados, pero configurarlos requiere que el usuario sepa qué buzones ha reservado el servidor para estos fines. Aspose.Email puede identificar estos buzones de uso especial utilizando la clase [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/) para facilitar su trabajo. El siguiente ejemplo de código demuestra cómo acceder a estos buzones de uso especial utilizando la clase [ImapMailboxInfo](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmailboxinfo/).

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-IMAP-ImapSpecialUseMailboxes-1.cs" >}}