---
title: "Eliminando Mensajes del Servidor POP3"
url: /es/java/eliminando-mensajes-del-servidor-pop3/
weight: 20
type: docs
---


Aspose.Email es un componente robusto que permite realizar operaciones personalizadas después de ciertas acciones. Aspose.Email genera muchos eventos sobre los cuales los usuarios pueden realizar operaciones. Esta función proporciona a los usuarios más control sobre su aplicación. Por ejemplo, los usuarios pueden realizar sus acciones deseadas cuando:

- Todos los correos electrónicos masivos han sido enviados.
- Un mensaje está a punto de ser enviado.
- Un correo electrónico ha sido completamente enviado.
- Cuando un destinatario es rechazado por el servidor SMTP.

Las bandejas de entrada POP3 residen en un servidor POP3. Los correos en estas bandejas de entrada pueden ser recuperados a su PC mediante [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). La clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) utiliza el protocolo POP3 para copiar los mensajes de correo de su bandeja de entrada POP3 a su PC. Una vez que el correo ha sido recuperado, no necesita estar conectado a internet mientras se lee, ya que puede leer el correo recuperado en su PC. Si no necesita o quiere que se conserve una copia de algunos mensajes de correo en el servidor POP3, entonces los elimina. Esta sección muestra cómo eliminar correos electrónicos utilizando la clase [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

## **Eliminar un Correo por Índice**

El siguiente fragmento de código elimina todos los mensajes de correo de una bandeja de entrada uno por uno, basado en su índice. El índice nunca debe ser <=0 en [Pop3Client.deleteMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#deleteMessage-int-).

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java

// Crear un cliente POP3
Pop3Client client = new Pop3Client("mail.aspose.com", 110, "nombredeusuario", "contraseña");
try {
    // Eliminar todos los mensajes uno por uno
    int messageCount = client.getMessageCount();
    for (int i = 1; i <= messageCount; i++) {
        client.deleteMessage(i);
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Eliminar Todos los Correos Electrónicos**

También podemos llamar a [Pop3Client.deleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) para eliminar todos los mensajes. El siguiente fragmento de código le muestra cómo eliminar todos los correos electrónicos.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java

// Eliminar todos los mensajes
client.deleteMessages();
~~~

Si la conexión al servidor POP3 se interrumpe inmediatamente después de las operaciones de eliminación, ya no puede llamar a [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).cancelDeletes() para hacer lo que desea.

## **Cancelar Eliminaciones**

[Pop3Client.undeleteMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#undeleteMessages--) puede usarse para cancelar la eliminación de mensajes de correo electrónico. El siguiente fragmento de código le muestra cómo cancelar eliminaciones.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java

// Cancelar eliminaciones
client.undeleteMessages();
~~~