---
title: "Trabajo con carpetas en un servidor IMAP"
url: /es/java/working-with-folders-on-imap-server/
weight: 60
type: docs
---


## **Obtención de información de carpetas**

Obtener información sobre las carpetas de un servidor IMAP es muy fácil con Aspose.Email. Llame al [listFolders()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#listFolders--) método del [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) clase. Devuelve un objeto de [ImapFolderInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapfolderinfocollection/) tipo. Recorra esta colección y obtenga información sobre las carpetas individuales de un bucle. El método está sobrecargado. Puede pasar un nombre de carpeta como parámetro para obtener una lista de subcarpetas. El siguiente fragmento de código muestra cómo obtener información de carpetas de un servidor IMAP mediante el método Aspose.Email descrito.

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

## **Eliminar carpetas y cambiarles el nombre**

Una carpeta de un servidor IMAP se puede eliminar o renombrar en una sola línea con Aspose.Correo electrónico:

- The [deleteFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteFolder-java.lang.String-) el método acepta el nombre de la carpeta como parámetro.
- Para el [renameFolder()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#renameFolder-java.lang.String-java.lang.String-) método, debe pasar el nombre de la carpeta actual y el nombre de la nueva carpeta.

El siguiente fragmento de código muestra cómo eliminar una carpeta de un servidor IMAP y cómo cambiar el nombre de una carpeta. Cada operación se realiza con una línea de código.

```java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Delete a folder and Rename a folder
client.deleteFolder("foldername");
client.renameFolder("foldername", "newfoldername");
```

## **Añadir un mensaje nuevo a una carpeta**

Puede añadir un mensaje nuevo a la carpeta mediante el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) and [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) clases. Primero, crea un [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) objeta proporcionando al sujeto valores de ida y vuelta. A continuación, suscríbase a una carpeta y añada el mensaje a ella. En el siguiente fragmento de código, se muestra cómo añadir un mensaje nuevo a una carpeta.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create a message
MailMessage msg = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Subscribe to the Inbox folder and Append the newly created message
client.selectFolder(ImapFolderInfo.IN_BOX);
client.subscribeFolder(client.getCurrentFolder().getName());
client.appendMessage(client.getCurrentFolder().getName(), msg);
~~~

## **Agregue varios mensajes con soporte para conexiones múltiples**

Puede añadir varios mensajes mediante el [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) método proporcionado por el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) clase. El [appendMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#appendMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.MailMessage--) el método acepta una lista de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y la agrega a la carpeta actual si la carpeta no se proporciona como parámetro. iMapClient también admite el modo multiconexión para operaciones con cargas pesadas. El siguiente fragmento de código muestra cómo agregar varios mensajes mediante el modo MultiConnection.

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

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Mover los mensajes a otra carpeta del buzón**

Aspose.Email para Java permite mover un mensaje de una carpeta de buzón a otra mediante el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) API. El [moveMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#moveMessage-int-java.lang.String-) El método utiliza el identificador único del mensaje y el nombre de la carpeta de destino para mover un mensaje a la carpeta de destino. El siguiente fragmento de código muestra cómo mover los mensajes a otra carpeta del buzón.

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

## **Copiar mensajes a otra carpeta de buzones**

La API Aspose.Email ofrece la capacidad de copiar un mensaje de una carpeta de buzones de correo a otra. Permite copiar un solo mensaje o varios mensajes mediante el [copyMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessage-com.aspose.email.IConnection-int-java.lang.String-) and [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) métodos. El [copyMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#copyMessages-int-int-java.lang.String-) El método proporciona la capacidad de copiar varios mensajes de la carpeta de origen de un buzón a la carpeta de buzones de destino. El siguiente fragmento de código muestra cómo copiar los mensajes a otra carpeta del buzón.

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

## **Trabajar con carpetas de buzones de correo de uso especial**

Algunos almacenes de mensajes IMAP incluyen buzones de correo de uso especial, como los que se utilizan para guardar borradores de mensajes o mensajes enviados. Muchos clientes de correo permiten a los usuarios especificar dónde deben colocarse los borradores de los mensajes enviados, pero para configurarlos es necesario que el usuario sepa qué buzones ha reservado el servidor para estos fines. Aspose.Email puede identificar estos buzones de uso especial mediante el [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) clase para que sea más fácil trabajar con ellos. En el siguiente ejemplo de código se muestra cómo acceder a estos buzones de uso especial mediante el [ImapMailboxInfo](https://reference.aspose.com/email/java/com.aspose.email/imapmailboxinfo/) class.

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
