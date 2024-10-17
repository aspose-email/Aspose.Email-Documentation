---
title: "Trabajando con Banderas de Mensaje en el Servidor"
url: /es/java/working-with-message-flags-on-server/
weight: 30
type: docs
---


## **Cambio de las Banderas de Mensaje**

Puedes cambiar las banderas de los mensajes utilizando el método [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Este método toma dos parámetros.

1. El número de secuencia del mensaje o ID único.
1. [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/).

Se pueden establecer las siguientes banderas:

- [Respondido](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getAnswered--)
- [Eliminado](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDeleted--)
- [Borrador](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getDraft--)
- [Vacío](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getEmpty--)
- [Marcado](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getFlagged--)
- [Leído](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#isRead--)
- [Reciente](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/#getRecent--)
  
### **Establecer Banderas de Mensaje**

El siguiente fragmento de código muestra cómo cambiar las banderas de mensajes en un servidor IMAP con Aspose.Email.

~~~Java
// Para ejemplos completos y archivos de datos, visita https://github.com/aspose-email/Aspose.Email-for-Java
// Marcar el mensaje como leído
client.changeMessageFlags(1, ImapMessageFlags.isRead());
~~~

### **Eliminar Banderas de Mensaje**

Las banderas de mensaje también se pueden eliminar con el método [removeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#removeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Su uso es similar al del método [changeMessageFlags()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#changeMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-). Toma un número de secuencia o un ID de mensaje único y [MessageFlag](https://reference.aspose.com/email/java/com.aspose.email/imapmessageflags/). El siguiente fragmento de código muestra cómo eliminar banderas de mensaje.

~~~Java
// Para ejemplos completos y archivos de datos, visita https://github.com/aspose-email/Aspose.Email-for-Java
// Eliminar la bandera del mensaje
client.removeMessageFlags(1, ImapMessageFlags.isRead());
~~~

## **Establecer Banderas Personalizadas**

También puedes establecer banderas personalizadas para un mensaje utilizando el [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) de la API. El ImapClient [AddMessageFlags](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#addMessageFlags-com.aspose.email.IConnection-int-com.aspose.email.ImapMessageFlags-) proporciona la capacidad de establecer banderas personalizadas en los mensajes.

~~~Java
// Para ejemplos completos y archivos de datos, visita https://github.com/aspose-email/Aspose.Email-for-Java
// Crear un mensaje
MailMessage message = new MailMessage("user@domain1.com", "user@domain2.com", "asunto", "mensaje");

// Agregar el mensaje al buzón
String uid = client.appendMessage(ImapFolderInfo.IN_BOX, message);

// Agregar banderas personalizadas al mensaje agregado
client.addMessageFlags(uid, com.aspose.email.ImapMessageFlags.op_BitwiseOr(ImapMessageFlags.keyword("custom1"), ImapMessageFlags.keyword("custom1_0")));

// Recuperar los mensajes para verificar la presencia de la bandera personalizada
client.selectFolder(ImapFolderInfo.IN_BOX);

ImapMessageInfoCollection messageInfos = client.listMessages();
for (ImapMessageInfo inf : messageInfos) {
    ImapMessageFlags[] flags = inf.getFlags().split();

    if (inf.containsKeyword("custom1"))
        System.out.println("Palabra clave encontrada");
}
~~~