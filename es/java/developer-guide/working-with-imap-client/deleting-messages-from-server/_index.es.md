---
title: "Eliminar mensajes del servidor"
url: /es/java/deleting-messages-from-server/
weight: 50
type: docs
---


## **Eliminar mensajes**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) la clase puede eliminar mensajes de un servidor IMAP. El [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class [deleteMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) la función se usa para borrar mensajes. Toma el número de secuencia del mensaje o el identificador único como parámetro. El [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) provides [deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) and [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) métodos para eliminar mensajes uno por uno o varios. El siguiente fragmento de código muestra cómo eliminar un mensaje de correo electrónico con el identificador de mensaje 1 de un servidor IMAP.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.setSecurityOptions(SecurityOptions.SSLImplicit);

    // Append test message
    client.selectFolder(ImapFolderInfo.IN_BOX);

    MailMessage eml = new MailMessage("from@from.com", "to@to.com");
    eml.setSubject("Message to delete");
    eml.setBody("Hey! This Message will be deleted!");
    String emlId = client.appendMessage(eml);

    // Delete appended message
    client.deleteMessage(emlId);
    client.commitDeletes();
}
~~~

## **Eliminar varios mensajes**

Se pueden eliminar varios correos electrónicos del buzón de correo mediante el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) de la API Aspose.Email. El [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) el método proporciona una serie de opciones para eliminar varios mensajes del servidor mediante identificadores únicos, números de secuencia o [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/) elementos. El siguiente fragmento de código muestra cómo eliminar varios mensajes.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder(ImapFolderInfo.IN_BOX);

    // Append test messages
    List<MailMessage> emlList = new ArrayList<>();
    for (int i = 0; i < 3; i++) {
        MailMessage eml = new MailMessage("from@from.com", "to@to.com");
        eml.setSubject("Message to delete " + i);
        eml.setBody("Hey! This Message will be deleted!");

        emlList.add(eml);
    }

    AppendMessagesResult appendMessagesResult = client.appendMessages(emlList);
    List<String> uidList = new ArrayList<>();
    for (String uid : appendMessagesResult.getSucceeded().getValues()) {
        uidList.add(uid);
    }

    // Bulk Delete appended Messages
    client.deleteMessagesByUids(uidList, true);
    client.commitDeletes();
}
~~~
