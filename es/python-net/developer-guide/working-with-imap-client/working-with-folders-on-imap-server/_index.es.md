---
title: "Trabajo con carpetas en un servidor IMAP"
url: /es/python-net/working-with-folders-on-imap-server/
weight: 50
type: docs
---


## **Obtención de información de carpetas**
Obtener información sobre las carpetas de un servidor IMAP es muy fácil con Aspose.Email. Llama al método listFolders () del espacio de nombres Aspose.Email.Imap. Devuelve un objeto del [ImapFolderInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection) tipo. Recorra esta colección y obtenga información sobre las carpetas individuales de un bucle. El método está sobrecargado. Puede pasar un nombre de carpeta como parámetro para obtener una lista de subcarpetas. El siguiente fragmento de código muestra cómo obtener información de carpetas de un servidor IMAP mediante Aspose.Email mediante el método descrito en la información.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}

## **Eliminar carpetas y cambiarles el nombre**

Los siguientes métodos del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) La clase relacionada con la administración de carpetas en un servidor de correo electrónico mediante IMAP se puede implementar fácilmente en su proyecto con Aspose.Email:

- Método delete_folder: elimina permanentemente la carpeta y todos los mensajes que contiene.
- Método rename_folder: cambia el nombre de la carpeta sin alterar su contenido.

El siguiente fragmento de código muestra cómo eliminar o cambiar el nombre de las carpetas del servidor IMAP mediante programación:

```py
# Delete a folder and Rename a folder
client.delete_folder("foldername")
client.rename_folder("foldername", "newfoldername")
```

## **Añadir un mensaje nuevo a una carpeta**
Puede agregar un mensaje nuevo a la carpeta mediante las clases MailMessage e ImapClient. Crear primero un objeto MailMessage proporcionando los valores de asunto, destino y origen. A continuación, suscríbase a una carpeta y añada el mensaje a ella. En el siguiente fragmento de código, se muestra cómo añadir un mensaje nuevo a una carpeta.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}

## **Establecimiento de la conexión múltiple al realizar operaciones por lotes**

Aspose.Email permite configurar el cliente para establecer múltiples conexiones simultáneas con el servidor IMAP. No necesariamente aumenta el rendimiento, pero es una solución fiable para operaciones simultáneas. Esto es particularmente útil si el cliente necesita realizar varias tareas al mismo tiempo, como buscar diferentes carpetas de correo electrónico, sincronizar grandes cantidades de datos o procesar varios mensajes simultáneamente.

El siguiente fragmento de código muestra cómo establecer varias conexiones con el servidor IMAP mientras se carga una colección de mensajes de correo electrónico mediante el método «append_messages» del [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.append_messages(messages)
```

## **Mover los mensajes a otra carpeta del buzón**
Aspose.Email para.NET permite mover mensajes de una carpeta de buzón a otra mediante la API IMAPClient. El método MoveMessage usa el identificador único del mensaje y el nombre de la carpeta de destino para mover un mensaje a la carpeta de destino. En el siguiente fragmento de código, se muestra cómo mover los mensajes a otra carpeta del buzón.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}
## **Copiar mensajes a otra carpeta de buzones**
La API Aspose.Email ofrece la capacidad de copiar mensajes de una carpeta de buzones de correo a otra. Permite copiar uno o varios mensajes utilizando los métodos CopyMessage y CopyMessages. El método CopyMessages ofrece la capacidad de copiar varios mensajes de la carpeta de origen de un buzón a la carpeta de buzones de destino. El siguiente fragmento de código muestra cómo copiar los mensajes a otra carpeta del buzón.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}

## **Trabajar con carpetas de buzones de correo de uso especial**

Los buzones de uso especial son carpetas predesignadas dentro de un sistema de correo electrónico que se utilizan para tipos específicos de mensajes, como enviados, borradores, correo basura, papelera y archivado. La biblioteca Aspose.Email permite el acceso a estos buzones mediante la asignación al cliente de los atributos asociados a sus funciones y propósitos. De este modo, los clientes pueden descubrir y presentar automáticamente estas carpetas en consecuencia sin la intervención del usuario.

En el siguiente fragmento de código se muestra cómo consultar información sobre los buzones importantes de uso especial (bandeja de entrada, borrador, correo basura, enviados y papelera) mediante las propiedades del [ImapMailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmailboxinfo/#imapmailboxinfo-class) clase, e imprima esta información:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

mailboxInfo = client.mailbox_info
print(mailboxInfo.inbox)
print(mailboxInfo.draft_messages)
print(mailboxInfo.junk_messages)
print(mailboxInfo.sent_messages)
print(mailboxInfo.trash)
```