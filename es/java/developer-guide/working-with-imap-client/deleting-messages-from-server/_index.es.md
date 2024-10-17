---
title: "Eliminando Mensajes del Servidor"
url: /es/java/deleting-messages-from-server/
weight: 50
type: docs
---


## **Eliminando Mensajes**

La clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) puede eliminar mensajes de un servidor IMAP. La función [deleteMessage()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) de la clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) se utiliza para eliminar mensajes. Toma el número de secuencia del mensaje o el ID único como parámetro. La clase [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) proporciona los métodos [deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessage-int-) y [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) para eliminar mensajes uno por uno o de múltiples. El siguiente fragmento de código muestra cómo eliminar un mensaje de correo electrónico con el ID del mensaje 1 de un servidor IMAP.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.setSecurityOptions(SecurityOptions.SSLImplicit);

    // Agregar mensaje de prueba
    client.selectFolder(ImapFolderInfo.IN_BOX);

    MailMessage eml = new MailMessage("from@from.com", "to@to.com");
    eml.setSubject("Mensaje a eliminar");
    eml.setBody("¡Hola! Este mensaje será eliminado!");
    String emlId = client.appendMessage(eml);

    // Eliminar el mensaje agregado
    client.deleteMessage(emlId);
    client.commitDeletes();
}
~~~

## **Eliminando Múltiples Mensajes**

Se pueden eliminar múltiples correos electrónicos de la bandeja de entrada utilizando el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) de la API Aspose.Email. El método [deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#deleteMessages-com.aspose.email.IConnection-java.lang.Iterable-com.aspose.email.ImapMessageInfo--) proporciona varias opciones para eliminar múltiples mensajes del servidor utilizando IDs únicos, números de secuencia o elementos de [ImapMessageInfoCollection](https://reference.aspose.com/email/java/com.aspose.email/imapmessageinfocollection/). El siguiente fragmento de código muestra cómo eliminar múltiples mensajes.

~~~Java
try (ImapClient client = new ImapClient("host", "username", "password")) {
    client.selectFolder(ImapFolderInfo.IN_BOX);

    // Agregar mensajes de prueba
    List<MailMessage> emlList = new ArrayList<>();
    for (int i = 0; i < 3; i++) {
        MailMessage eml = new MailMessage("from@from.com", "to@to.com");
        eml.setSubject("Mensaje a eliminar " + i);
        eml.setBody("¡Hola! Este mensaje será eliminado!");

        emlList.add(eml);
    }

    AppendMessagesResult appendMessagesResult = client.appendMessages(emlList);
    List<String> uidList = new ArrayList<>();
    for (String uid : appendMessagesResult.getSucceeded().getValues()) {
        uidList.add(uid);
    }

    // Eliminación masiva de mensajes agregados
    client.deleteMessagesByUids(uidList, true);
    client.commitDeletes();
}
~~~