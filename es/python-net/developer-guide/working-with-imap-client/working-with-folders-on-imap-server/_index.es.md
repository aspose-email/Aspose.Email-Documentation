---
title: "Trabajando con carpetas en el servidor IMAP"
url: /es/python-net/working-with-folders-on-imap-server/
weight: 50
type: docs
---


## **Obteniendo Información de Carpetas**
Obtener información sobre carpetas de un servidor IMAP es muy fácil con Aspose.Email. Llama al método ListFolders() del espacio de nombres Aspose.Email.Imap. Devuelve un objeto del tipo [ImapFolderInfoCollection](https://apireference.aspose.com/email/net/aspose.email.clients.imap/imapfolderinfocollection). Itera a través de esta colección y obtén información sobre carpetas individuales en un bucle. El método está sobrecargado. Puedes pasar un nombre de carpeta como parámetro para obtener una lista de subcarpetas. El siguiente fragmento de código te muestra cómo obtener información de carpetas de un servidor IMAP usando Aspose.Email con el método descrito en la información.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-GettingFoldersInformation-GettingFoldersInformation.py" >}}

## **Eliminando y Renombrando Carpetas**

Los siguientes métodos de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) relacionados con la gestión de carpetas en un servidor de correo electrónico usando IMAP se pueden implementar fácilmente en tu proyecto con Aspose.Email:

- método delete_folder - elimina permanentemente la carpeta y todos los mensajes contenidos en ella.
- método rename_folder - cambia el nombre de la carpeta sin alterar el contenido dentro de ella.

El siguiente fragmento de código muestra cómo eliminar o renombrar carpetas en el servidor IMAP programáticamente:

```py
# Eliminar una carpeta y Renombrar una carpeta
client.delete_folder("nombredecarpeta")
client.rename_folder("nombredecarpeta", "nuevonombredecarpeta")
```

## **Agregando un Nuevo Mensaje en una Carpeta**
Puedes agregar un nuevo mensaje a la carpeta usando las clases MailMessage e ImapClient. Primero crea un objeto MailMessage proporcionando el asunto, los valores de para y de. Luego suscríbete a una carpeta y agrega el mensaje a ella. El siguiente fragmento de código te muestra cómo agregar un nuevo mensaje en una carpeta.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-AppendMessageToFolder-AppendMessagetoFolder.py" >}}

## **Estableciendo MultiConexión al Realizar Operaciones por Lotes**

Aspose.Email hace posible configurar el cliente para establecer múltiples conexiones simultáneas al servidor IMAP. No necesariamente aumenta el rendimiento, pero es una solución confiable para operaciones concurrentes. Esto es particularmente útil si el cliente necesita realizar múltiples tareas al mismo tiempo, como recuperar diferentes carpetas de correo electrónico, sincronizar grandes cantidades de datos o procesar múltiples mensajes simultáneamente.

El siguiente fragmento de código muestra cómo establecer múltiples conexiones al servidor IMAP mientras se sube una colección de mensajes de correo electrónico usando el método 'append_messages' de la clase [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class):

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.append_messages(mensajes)
```

## **Mover Mensajes a Otra Carpeta de Mailbox**
Aspose.Email para .NET permite mover mensajes de una carpeta de correo a otra utilizando la API ImapClient. El método MoveMessage usa el id único del mensaje y el nombre de la carpeta de destino para mover un mensaje a la carpeta de destino. El siguiente fragmento de código te muestra cómo mover mensajes a otra carpeta de mailbox.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-MoveMessageToAnotherFolder-MoveMessageToAnotherFolder.py" >}}

## **Copiar Mensajes a Otra Carpeta de Mailbox**
La API de Aspose.Email proporciona la capacidad de copiar mensajes de una carpeta de correo a otra. Permite copiar un solo mensaje, así como múltiples mensajes usando los métodos CopyMessage y CopyMessages. El método CopyMessages proporciona la capacidad de copiar múltiples mensajes desde la carpeta fuente de un mailbox a la carpeta de destino. El siguiente fragmento de código muestra cómo copiar mensajes a otra carpeta de mailbox.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-CopyMessageToAnotherFolder-CopyMessageToAnotherFolder.py" >}}

## **Trabajando con Carpetas de Mailbox de Uso Especial**

Las bandejas de entrada de uso especial son carpetas predesignadas dentro de un sistema de correo electrónico utilizadas para tipos específicos de mensajes, como enviados, borradores, correo no deseado, papelera y archivo. La biblioteca Aspose.Email permite el acceso a estas bandejas de entrada asignando atributos asociados con sus roles y propósitos al cliente. Luego, los clientes pueden descubrir y presentar automáticamente estas carpetas en consecuencia sin intervención del usuario.

El siguiente fragmento de código muestra cómo consultar información sobre las bandejas de entrada de uso especial importantes (bandeja de entrada, borrador, correo no deseado, enviados y papelera) usando las propiedades de la clase [ImapMailBoxInfo](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapmailboxinfo/#imapmailboxinfo-class), y imprimir esta información:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.dominio.com", 993, "usuario@dominio.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

mailboxInfo = client.mailbox_info
print(mailboxInfo.inbox)
print(mailboxInfo.draft_messages)
print(mailboxInfo.junk_messages)
print(mailboxInfo.sent_messages)
print(mailboxInfo.trash)
```