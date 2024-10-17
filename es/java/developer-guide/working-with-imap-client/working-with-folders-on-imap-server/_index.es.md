---
title: "Trabajando con Carpetas en Servidor IMAP"
url: /es/java/working-with-folders-on-imap-server/
weight: 60
type: docs
---


## **Obteniendo Información sobre Carpetas**

Obtener información sobre carpetas de un servidor IMAP es muy fácil con Aspose.Email. Llama al [método listFolders()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listFolders--) de la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Devuelve un objeto del tipo [ImapFolderInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapfolderinfocollection/). Itera a través de esta colección y obtiene información sobre carpetas individuales en un bucle. El método está sobrecargado. Puedes pasar el nombre de una carpeta como parámetro para obtener una lista de subcarpetas. El siguiente fragmento de código muestra cómo obtener información de carpetas de un servidor IMAP utilizando el método descrito de Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get all folders in the currently subscribed folder
ImapFolderInfoCollection folderInfoColl = client.listFolders();

// Iterate through the collection to get folder info one by one
for (ImapFolderInfo folderInfo : (Iterable<ImapFolderInfo>) folderInfoColl) {
    // Folder name and get New messages in the folder
    System.out.println("Folder name is " + folderInfo.getName());
    ImapFolderInfo folderExtInfo = client.getFolderInfo(folderInfo.getName());
    System.out.println("New message count: " + folderExtInfo.getNewMessageCount());
    System.out.println("Is it readonly? " + folderExtInfo.getReadOnly());
    System.out.println("Total number of messages " + folderExtInfo.getTotalMessageCount());
}
~~~


## **Eliminando y Renombrando Carpetas**

Una carpeta en un servidor IMAP puede ser eliminada o renombrada en una sola línea con Aspose.Email:

- El método [deleteFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteFolder-java.lang.String-) acepta el nombre de la carpeta como parámetro.
- Para el método [renameFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#renameFolder-java.lang.String-java.lang.String-), necesitas pasar el nombre actual de la carpeta y el nuevo nombre de la carpeta.

El siguiente fragmento de código muestra cómo eliminar una carpeta de un servidor IMAP y cómo renombrar una carpeta. Cada operación se realiza con una línea de código.

```java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Delete a folder and Rename a folder
client.deleteFolder("foldername");
client.renameFolder("foldername", "newfoldername");
```


## **Agregando un Nuevo Mensaje en una Carpeta**

Puedes agregar un nuevo mensaje a la carpeta utilizando las clases [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Primero, crea un objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) proporcionando los valores de sujeto, para y de. Luego, suscríbete a una carpeta y añade el mensaje a ella. El siguiente fragmento de código muestra cómo agregar un nuevo mensaje a una carpeta.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create a message
MailMessage msg = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Subscribe to the Inbox folder and Append the newly created message
client.selectFolder(ImapFolderInfo.IN_BOX);
client.subscribeFolder(client.getCurrentFolder().getName());
client.appendMessage(client.getCurrentFolder().getName(), msg);
~~~


## **Agregar Múltiples Mensajes con Soporte MultiConexión**

Puedes agregar múltiples mensajes utilizando el método [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) proporcionado por la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). El método [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) acepta una lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y la añade a la carpeta actual si la carpeta no se proporciona como parámetro. ImapClient también soporta el modo MultiConexión para operaciones de carga pesada. El siguiente fragmento de código muestra cómo agregar múltiples mensajes utilizando el modo MultiConexión.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Test Message - " + UUID.randomUUID().toString(), "IMAP Group Append with MultiConnection");
    messages.add(message);
}

imapClient.setConnectionsQuantity(5);
imapClient.setUseMultiConnection(MultiConnectionMode.Enable);
imapClient.appendMessages(messages);
~~~


{{% alert color="primary" %}} 

Por favor, ten en cuenta que el uso del modo multi-conexión no garantiza un aumento del rendimiento.

{{% /alert %}} 


## **Mover Mensajes a Otra Carpeta de Correo**

Aspose.Email para Java permite mover un mensaje de una carpeta de correo a otra utilizando la API de [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). El método [moveMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#moveMessage-int-java.lang.String-) utiliza el id único del mensaje y el nombre de la carpeta de destino para mover un mensaje a la carpeta de destino. El siguiente fragmento de código muestra cómo mover mensajes a otra carpeta de correo.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// This example shows how to move a message from one folder of a mailbox to another one using the ImapClient API of Aspose.Email for Java
// Available from Aspose.Email for Java onwards
// -------------- Available API Overload Members --------------
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(int sequenceNumber, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(String uniqueId, String folderName, boolean commitDeletions)
// void ImapClient.moveMessage(IConnection iConnection, int sequenceNumber, String folderName)
// void ImapClient.moveMessage(IConnection iConnection, String uniqueId, String folderName)
// void ImapClient.moveMessage(int sequenceNumber, String folderName)
// void ImapClient.moveMessage(String uniqueId, String folderName)

final ImapClient client = new ImapClient("host.domain.com", 993, "username", "password");
try {
    String folderName = "EMAILNET-35151";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        MailMessage message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35151 - " + UUID.randomUUID(),
                "EMAILNET-35151 ImapClient: Provide option to Move Message");
        client.selectFolder(ImapFolderInfo.IN_BOX);
        // Append the new message to Inbox folder
        String uniqueId = client.appendMessage(ImapFolderInfo.IN_BOX, message);
        ImapMessageInfoCollection messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Now move the message to the folder EMAILNET-35151
        client.moveMessage(uniqueId, folderName);
        client.commitDeletes();
        // Verify that the message was moved to the new folder
        client.selectFolder(folderName);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
        // Verify that the message was moved from the Inbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        messageInfoCol1 = client.listMessages();
        System.out.println(messageInfoCol1.size());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~


## **Copiar Mensajes a Otra Carpeta de Correo**

La API de Aspose.Email proporciona la capacidad de copiar un mensaje de una carpeta de correo a otra. Permite copiar tanto un solo mensaje como múltiples mensajes utilizando los métodos [copyMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessage-com.aspose.email.IConnection-int-java.lang.String-) y [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-). El método [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) proporciona la capacidad de copiar múltiples mensajes desde la carpeta fuente de un buzón a la carpeta de buzón de destino. El siguiente fragmento de código muestra cómo copiar mensajes a otra carpeta de correo.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
final ImapClient client = new ImapClient("exchange.aspose.com", "username", "password");
try {
    // Create the destination folder
    String folderName = "EMAILNET-35242";
    if (!client.existFolder(folderName))
        client.createFolder(folderName);
    try {
        // Append a couple of messages to the server
        MailMessage message1 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Improvement of copy method.Add ability to 'copy' multiple messages per invocation.");
        String uniqueId1 = client.appendMessage(message1);

        MailMessage message2 = new MailMessage("asposeemail.test3@aspose.com", "asposeemail.test3@aspose.com", "EMAILNET-35242 - " + UUID.randomUUID(),
                "EMAILNET-35242 Improvement of copy method.Add ability to 'copy' multiple messages per invocation.");
        String uniqueId2 = client.appendMessage(message2);

        // Verify that the messages have been added to the mailbox
        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());

        // Copy multiple messages using the CopyMessages command and Verify that messages are copied to the destination folder
        client.copyMessagesByUids(Arrays.asList(uniqueId1, uniqueId2), folderName);

        client.selectFolder(folderName);
        msgsColl = client.listMessages();
        for (ImapMessageInfo msgInfo : msgsColl)
            System.out.println(msgInfo.getSubject());
    } finally {
        try {
            client.deleteFolder(folderName);
        } catch (java.lang.RuntimeException e) {
        }
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~


## **Trabajando con Carpetas de Correo de Uso Especial**

Algunos almacenes de mensajes IMAP incluyen buzones de uso especial, como aquellos utilizados para almacenar mensajes de borrador o mensajes enviados. Muchos clientes de correo permiten a los usuarios especificar dónde deben colocarse los mensajes de borrador o enviados, pero configurarlos requiere que el usuario sepa qué buzones ha reservado el servidor para estos propósitos. Aspose.Email puede identificar estos buzones de uso especial utilizando la clase [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) para facilitar el trabajo con ellos. El siguiente ejemplo de código demuestra cómo acceder a estos buzones de uso especial utilizando la clase [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/).

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapMailboxInfo mailboxInfo = imapClient.getMailboxInfo();
System.out.println(mailboxInfo.getInbox());
System.out.println(mailboxInfo.getDraftMessages());
System.out.println(mailboxInfo.getJunkMessages());
System.out.println(mailboxInfo.getSentMessages());
System.out.println(mailboxInfo.getTrash());
~~~