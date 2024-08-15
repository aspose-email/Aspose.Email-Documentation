---
title: "Trabajando con marcas de mensajes en el servidor"
url: /es/java/working-with-message-flags-on-server/
weight: 30
type: docs
---


## **Cambiar las banderas de los mensajes**

Puede cambiar las marcas de los mensajes mediante el [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) método. Este método toma dos parámetros.

1. El número de secuencia del mensaje o el identificador único.
1. [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/).

Se pueden configurar los siguientes indicadores:

- [Answered](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getAnswered--)
- [Deleted](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDeleted--)
- [Draft](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDraft--)
- [Empty](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getEmpty--)
- [Flagged](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getFlagged--)
- [isRead](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#isRead--)
- [Recent](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getRecent--)
 
### **Configuración de banderas de mensajes**

El siguiente fragmento de código muestra cómo cambiar las marcas de mensajes en un servidor IMAP con Aspose.Email.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Mark the message as read
client.changeMessageFlags(1, ImapMessageFlags.isRead());
~~~

### **Eliminar marcas de mensajes**

Las marcas de mensajes también se pueden eliminar con la [removeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#removeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) método. El uso es similar al del [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) método. Toma un número de secuencia o un identificador de mensaje único y [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/). En el siguiente fragmento de código, se muestra cómo eliminar las marcas de mensajes.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Remove the message flag
client.removeMessageFlags(1, ImapMessageFlags.isRead());
~~~

## **Configuración de banderas personalizadas**

También puedes configurar marcas personalizadas para un mensaje mediante el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) de la API. El iMapClient [AddMessageFlags](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#addMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) ofrece la posibilidad de establecer marcas personalizadas en los mensajes.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create a message
MailMessage message = new MailMessage("user@domain1.com", "user@domain2.com", "subject", "message");

// Append the message to mailbox
String uid = client.appendMessage(ImapFolderInfo.IN_BOX, message);

// Add custom flags to the added messge
client.addMessageFlags(uid, com.aspose.email.ImapMessageFlags.op_BitwiseOr(ImapMessageFlags.keyword("custom1"), ImapMessageFlags.keyword("custom1_0")));

// Retreive the messages for checking the presence of custom flag
client.selectFolder(ImapFolderInfo.IN_BOX);

ImapMessageInfoCollection messageInfos = client.listMessages();
for (ImapMessageInfo inf : messageInfos) {
    ImapMessageFlags[] flags = inf.getFlags().split();

    if (inf.containsKeyword("custom1"))
        System.out.println("Keyword found");
}
~~~
