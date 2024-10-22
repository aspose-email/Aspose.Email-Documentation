---
title: "Envío y Reenvío de Mensajes - Enviar Mensajes de Correo Electrónico de Outlook usando un Programa Java"
url: /es/java/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Envío y Reenvío de Mensajes"
---

La clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) permite a las aplicaciones enviar correos electrónicos utilizando el Protocolo Simple de Transferencia de Correo (SMTP).

- La clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) es la única entrada principal que los desarrolladores utilizan para enviar mensajes de correo.
- La clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) también proporciona otros métodos comunes de entrega de correo, incluyendo la escritura de mensajes de correo en el sistema de archivos, cola de mensajes, etc.
- La clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) admite completamente estos dos modelos de programación:
  - [Sincrónico](#sending-emails-synchronously)
  - [Asincrónico](#sending-emails-asynchronously)
- La clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) también soporta [el envío de mensajes como TNEF](#sending-message-as-tnef)

Para enviar el mensaje de correo electrónico y bloquear mientras se espera la transmisión al servidor SMTP, utilice uno de los métodos de envío sincrónico. Para permitir que el hilo principal de su programa continúe ejecutándose mientras se transmite el correo electrónico, utilice el método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-).

## **Envío de Correos Electrónicos Sincrónicamente**

Un mensaje de correo electrónico se puede enviar sincrónicamente utilizando el método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Envía el mensaje de correo electrónico especificado a través de un servidor SMTP para su entrega. El remitente del mensaje, los destinatarios, el asunto y el cuerpo del mensaje se especifican utilizando objetos String. Para enviar un mensaje de correo electrónico sincrónicamente, siga los pasos que se indican a continuación:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y establezca sus propiedades.
1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y especifique el Host, puerto, nombre de usuario y contraseña.
1. Envíe el mensaje utilizando el método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y pase la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

El siguiente fragmento de código Java le muestra cómo enviar correos electrónicos de Outlook sincrónicamente.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

// Declarar msg como instancia de MailMessage
MailMessage msg = new MailMessage();

// Crear una instancia de la clase SmtpClient
SmtpClient client = new SmtpClient();

// Especifique su servidor de correo, nombre de usuario, contraseña, número de puerto y opción de seguridad
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);

try {
    // Client.Send enviará este mensaje
    client.send(msg);
    System.out.println("Mensaje enviado");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Envío de Correos Electrónicos Asincrónicamente**

A veces, puede que desee enviar correo de forma asincrónica. Por ejemplo, si está enviando mucho correo a través de su aplicación, el enfoque sincrónico podría no funcionar. En tal escenario, puede usar [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). El método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) envía un mensaje de correo electrónico a un servidor SMTP para su entrega. Este método no bloquea el hilo de llamada y permite al llamador pasar un objeto al método que se invoca cuando la operación se completa. Para enviar un mensaje de correo electrónico de Outlook de forma asincrónica en Java, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y utilice sus diferentes propiedades.
1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y especifique el host, el puerto, el nombre de usuario y la contraseña.
1. Cree una instancia definida por el usuario que se pasará al método e invocará cuando se complete la operación asincrónica.
1. Envíe el mensaje utilizando el método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y pase la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) e instancia definida por el usuario junto con una función de callback que se llamará cuando la operación se haya completado.

Para recibir una notificación cuando el correo electrónico haya sido enviado o la operación haya sido cancelada, se llama a la función de callback pasada al método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). Después de llamar al método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/), no es necesario esperar a que un mensaje de correo electrónico se envíe completamente. Podemos llamar a otro método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) al mismo tiempo. Cuando se ha enviado un correo electrónico utilizando el método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-), el fragmento de código imprime un mensaje ("Mensaje enviado"). El siguiente programa de Java o fragmento de código le muestra cómo enviar correos electrónicos de forma asincrónica.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

public static void run() {
    sendMail();
}

static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient();
    client.setHost("mail.server.com");
    // Especifique su nombre de usuario, contraseña, número de puerto y opción de seguridad
    client.setUsername("username");
    client.setPassword("password");
    client.setPort(587);
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    return client;
}

static void sendMail() {
    try {

        // Declarar msg como instancia de MailMessage
        MailMessage msg = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Asunto de prueba", "Cuerpo de prueba");
        SmtpClient client = getSmtpClient();
        Object state = new Object();
        IAsyncResult ar = client.beginSend(msg, callback, state);
        // Si el usuario canceló el envío, y el correo no ha sido enviado aún,
        client.cancelAsyncOperation(ar);

        msg.dispose();
        System.out.println("Adiós.");
    } catch (Exception ex) {
        System.err.println(ex);
    }
}

static AsyncCallback callback = new AsyncCallback() {
    public void invoke(IAsyncResult ar) {
        IAsyncResultExt task = null;
        if (ar instanceof IAsyncResult)
            task = (IAsyncResultExt) ar;

        if (task != null && task.isCanceled()) {
            System.out.println("Envío cancelado.");
        }

        if (task != null && task.getErrorInfo() != null) {
            System.out.println(task.getErrorInfo());
        } else {
            System.out.println("Mensaje enviado.");
        }
    }
};
~~~

## **Envío de Mensajes Almacenados desde el Disco**

Los archivos EML (archivos de correo electrónico de Outlook Express) contienen un encabezado de correo electrónico, cuerpo del mensaje y cualquier adjunto. Aspose.Email permite a los desarrolladores trabajar con archivos EML de diferentes maneras. Este artículo muestra cómo cargar archivos EML desde el disco y enviarlos como correos electrónicos con SMTP. Puede cargar archivos .eml desde el disco o desde un flujo en la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y enviar el mensaje de correo electrónico utilizando la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) es la clase principal para crear nuevos mensajes de correo electrónico, cargar archivos de mensajes de correo desde el disco o flujo y guardar los mensajes. El siguiente fragmento de código Java muestra cómo enviar mensajes almacenados desde el disco.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

// Cargar un archivo EML en la clase MailMessage
MailMessage message = MailMessage.load(dataDir + "test.eml");

// Enviar este mensaje usando SmtpClient
SmtpClient client = new SmtpClient("host", "username", "password");

try {
    client.send(message);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Envío de Correo Electrónico de Texto Sin Formato**

Los ejemplos de programación a continuación muestran cómo enviar un mensaje de correo electrónico de texto sin formato. La propiedad [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) se utiliza para especificar el contenido de texto sin formato del cuerpo del mensaje. Para enviar un mensaje de correo electrónico de texto sin formato, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique las direcciones de correo electrónico del remitente y del receptor en la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique el contenido de la propiedad [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) para el mensaje de texto sin formato.
- Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y envíe el correo electrónico.

El siguiente fragmento de código le muestra cómo enviar un correo electrónico de texto sin formato.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

// Crear una instancia de la clase MailMessage
MailMessage message = new MailMessage();

// Establecer el campo De, campo Para y cuerpo de texto sin formato
message.setFrom(MailAddress.to_MailAddress("sender@sender.com"));
message.getTo().add("receiver@receiver.com");
message.setBody("Este es un cuerpo de texto sin formato");

// Crear una instancia de la clase SmtpClient
SmtpClient client = new SmtpClient();

// Y especifique su servidor de correo, nombre de usuario, contraseña y puerto
client.setHost("smtp.server.com");
client.setUsername("Username");
client.setPassword("Password");
client.setPort(25);

try {
    // Client.Send enviará este mensaje
    client.send(message);
    System.out.println("Mensaje enviado");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Envío de Correo Electrónico con Cuerpo HTML**

Los ejemplos de programación a continuación muestran cómo puede enviar un mensaje de correo electrónico simple en HTML. La propiedad [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), una propiedad de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), se utiliza para especificar el contenido HTML del cuerpo del mensaje. Para enviar un correo electrónico simple en HTML, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique la dirección de correo electrónico del remitente y del receptor en la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifique el contenido de [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) .
- Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y envíe el correo electrónico utilizando el método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) .

Con fines de este artículo, el contenido HTML del correo electrónico es rudimentario: <html><body>Este es el cuerpo HTML</body></html> La mayoría de los correos electrónicos en HTML serán más complejos. El siguiente fragmento de programa Java le muestra cómo enviar un correo electrónico con un cuerpo HTML.

~~~Java
public static void run() {
    // Declarar msg como instancia de MailMessage
    MailMessage msg = new MailMessage();

    // Usar propiedades de MailMessage como especificar remitente, destinatario, mensaje y HtmlBody
    msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("asposetest123@gmail.com"));
    msg.setSubject("Asunto de prueba");
    msg.setHtmlBody("<html><body>Este es el cuerpo HTML</body></html>");
    SmtpClient client = getSmtpClient();
    try {
        // Client enviará este mensaje
        client.send(msg);
        System.out.println("Mensaje enviado");
    } catch (Exception ex) {
        System.err.println(ex);
    }

    System.out.println("Correo electrónico enviado con cuerpo HTML.");
}

private static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.setSecurityOptions(SecurityOptions.Auto);
    return client;
}
~~~

## **Envío de Correo Electrónico con Texto Alternativo del Mensaje**

Los ejemplos de programación a continuación muestran cómo enviar un mensaje de correo electrónico simple en HTML con contenido alternativo. Use la clase [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) para especificar copias de un mensaje de correo electrónico en diferentes formatos. Por ejemplo, si envía un mensaje en HTML, también querrá proporcionar una versión en texto sin formato para los destinatarios que utilizan lectores de correo electrónico que no pueden mostrar contenido HTML. O, si está enviando un boletín, puede querer proporcionar una copia en texto sin formato para aquellos destinatarios que han elegido recibir una versión en texto sin formato. Para enviar un correo electrónico con texto alternativo, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Especifique las direcciones de correo electrónico del remitente y del receptor en la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Cree una instancia de la clase [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) .

Esto crea una vista alternativa de un mensaje de correo electrónico utilizando el contenido especificado en la cadena.

1. Agregue la instancia de la clase [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) al objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y envíe el correo electrónico utilizando el método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) .

El siguiente fragmento de código le muestra cómo enviar un correo electrónico con texto alternativo.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

// Declarar mensaje como instancia de MailMessage
MailMessage message = new MailMessage();

// Crear AlternateView para ver un mensaje de correo electrónico utilizando el contenido especificado en la //String
AlternateView alternate = AlternateView.createAlternateViewFromString("Texto Alternativo");

// Agregar texto alternativo
message.getAlternateViews().addItem(alternate);
~~~

## **Envío de Correos Electrónicos Masivos**

Enviar correos electrónicos en masa significa enviar un lote de correos electrónicos en un solo mensaje. Podemos enviar un lote de correos electrónicos usando la sobrecarga del método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) que acepta una clase [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/):

1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .
1. Especifique las propiedades de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .
1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Especifique el remitente, el receptor, el asunto del correo y el mensaje en la instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Repita los dos pasos anteriores si desea enviar correos electrónicos a otra persona.
1. Cree una instancia de la clase [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Agregue una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) en el objeto de la clase [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Ahora envíe su correo electrónico usando el método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) pasando la instancia de la clase [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) en ella.

El siguiente fragmento de código le muestra cómo enviar correos electrónicos masivos.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

// Crear SmtpClient como cliente y especificar servidor, puerto, nombre de usuario y contraseña
SmtpClient client = new SmtpClient("mail.server.com", 25, "Usuario", "Contraseña");

// Crear instancias de la clase MailMessage y especificar Para, De, Asunto y Mensaje
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Asunto1", "mensaje1, ¿cómo estás?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Asunto2", "mensaje2, ¿cómo estás?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Asunto3", "mensaje3, ¿cómo estás?");

// Crear una instancia de la clase MailMessageCollection
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.addItem(message1);
manyMsg.addItem(message2);
manyMsg.addItem(message3);

// Usar la función client.BulkSend para completar la tarea de envío masivo
try {
    // Enviar mensaje usando el método BulkSend
    client.send(manyMsg);
    System.out.println("Mensaje enviado");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~
## **Obtener Información sobre Mensajes Masivos Enviados**

Cuando envía mensajes en masa, puede obtener información sobre la cantidad de mensajes enviados con éxito y la lista de esos mensajes. El evento [SucceededSending](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setSucceededSending-com.aspose.ms.System.EventHandler-com.aspose.email.MailMessageEventArgs--) se utiliza para este propósito.

El siguiente ejemplo de código muestra cómo obtener información sobre la cantidad de mensajes enviados con éxito:

```java
try (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto)) {
    final AtomicInteger messageCount = new AtomicInteger(0);

    client.setSucceededSending(new EventHandler<MailMessageEventArgs>() {
        public void invoke(Object sender, MailMessageEventArgs eventArgs) {
            System.out.println("El mensaje " + eventArgs.getMessage().getSubject() + " fue enviado con éxito.");
            messageCount.incrementAndGet();
        }
    });

    client.send(messages);

    System.out.println(messageCount + " mensajes fueron enviados con éxito.");
}
```

## **Envío de Correos Electrónicos con MultiConexión**

[SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) proporciona una propiedad [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseMultiConnection-int-) que puede ser utilizada para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se utilizarán durante el modo de multiconexión utilizando [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setConnectionsQuantity-int-). El siguiente fragmento de código demuestra el uso del modo de multiconexión para enviar múltiples mensajes.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient smtpClient = new SmtpClient();
smtpClient.setHost("<HOST>");
smtpClient.setUsername("<USERNAME>");
smtpClient.setPassword("<PASSWORD>");
smtpClient.setPort(587);
smtpClient.setSupportedEncryption(EncryptionProtocols.Tls);
smtpClient.setSecurityOptions(SecurityOptions.SSLExplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<DIRECCIÓN DE CORREO>", "<DIRECCIÓN DE CORREO>", "Mensaje de Prueba - " + UUID.randomUUID().toString(),
            "Enviar Mensajes SMTP con MultiConexión");
    messages.add(message);
}

smtpClient.setConnectionsQuantity(5);
smtpClient.setUseMultiConnection(MultiConnectionMode.Enable);
smtpClient.send(messages);
~~~

{{% alert color="primary" %}} 

Tenga en cuenta que el uso del modo de multiconexión no garantiza un aumento en el rendimiento.

{{% /alert %}} 

## **Envío de un Mensaje como TNEF**

Los correos electrónicos TNEF tienen un formato especial que puede perderse si se envían utilizando la API estándar. Aspose.Email proporciona la capacidad de enviar correos electrónicos como TNEF, preservando así el formato. La propiedad [UseTnef](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseTnef\(boolean\)) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) se puede establecer para enviar el correo electrónico como TNEF. El siguiente fragmento de código le muestra cómo enviar un mensaje como TNEF.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

String emlFileName = dataDir + "Message.eml"; // Un correo electrónico TNEF

// Cargar desde eml
MailMessage eml1 = MailMessage.load(emlFileName, new EmlLoadOptions());
eml1.setFrom(MailAddress.to_MailAddress("somename@gmail.com"));
eml1.getTo().clear();
eml1.getTo().addItem(new MailAddress("first.last@test.com"));
eml1.setSubject("Con la bandera PreserveTnef durante la carga");
eml1.setDate(new Date());
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setUseTnef(true); // Use esta bandera para enviar como TNEF
client.send(eml1);
~~~

## **Envío de Solicitudes de Reunión**

Microsoft Outlook ofrece funciones de calendario, así como gestión de correos electrónicos. Cuando un usuario abre un correo electrónico con una invitación a un evento, Outlook le solicita que acepte o rechace la invitación. Aspose.Email permite a los desarrolladores añadir funciones de calendario a sus correos electrónicos.

### **Envío de Solicitudes por Correo Electrónico**

Para enviar solicitudes de reunión por correo electrónico, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
- Especifique las direcciones del remitente y el destinatario utilizando una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
- Inicialice una instancia de la clase [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) y pase sus valores.
- Especifique el resumen y la descripción en la instancia de [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/) .
- Agregue el [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/) a la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y páselo a la instancia de [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) .

|**Solicitud de reunión iCalendar enviada por correo electrónico**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
El siguiente fragmento de código le muestra cómo enviar solicitudes por correo electrónico.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

// Crear una instancia de la clase MailMessage
MailMessage msg = new MailMessage();

// Establecer el remitente, el destinatario, quien recibirá la solicitud de reunión. Básicamente, el destinatario es el mismo que los asistentes a la reunión
msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com"));

// Crear instancia de Appointment
Calendar cal = Calendar.getInstance();
cal.set(2015, Calendar.JULY, 17, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2015, Calendar.JULY, 17, 14, 0, 0);
Date endDate = cal.getTime();
Appointment app = new Appointment("Room 112", startDate, endDate, msg.getFrom(), msg.getTo());
app.setSummary("Reunión de lanzamiento");
app.setDescription("Discutir sobre el próximo lanzamiento");

// Agregar cita al mensaje y crear una instancia de la clase SmtpClient
msg.addAlternateView(app.requestApointment());
SmtpClient client = getSmtpClient();

try {
    // Client.Send enviará este mensaje
    client.send(msg);
    System.out.println("Mensaje enviado");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~ 

### **Compatibilidad de iCalendar para IBM Lotus Notes**

La función de calendario de Aspose.Email se basa en el estándar iCalendar, un estándar para el intercambio de datos de calendario (Referencia de Sintaxis RFC 2445 o RFC2445). Por lo tanto, admite no solo Microsoft Outlook, sino también IBM Lotus Notes. Para enviar una solicitud de reunión en Lotus Notes, siga los mismos pasos mencionados anteriormente.

## **Reenviar un Correo Electrónico usando el Cliente SMTP**

### **Reenviando un Correo Electrónico con el Cliente SMTP**

Reenviar un correo electrónico es una práctica común en la comunicación digital de la vida cotidiana. Un correo electrónico recibido puede ser reenviado a destinatarios específicos sin compartirlo con los remitentes originales. La API de Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) proporciona la capacidad de reenviar un correo electrónico a destinatarios específicos. Su método [Forward](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#forward-java.lang.String-com.aspose.email.MailAddressCollection-com.aspose.email.MailMessage-) se puede utilizar para reenviar un correo electrónico recibido o guardado a los destinatarios deseados, como se muestra en este artículo. El siguiente fragmento de código le muestra cómo reenviar un correo electrónico usando el Cliente SMTP.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

// Crear una instancia de la clase SmtpClient
SmtpClient client = new SmtpClient();

// Especifique su servidor de correo, nombre de usuario, contraseña, puerto y opciones de seguridad
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
MailMessage message = MailMessage.load(dataDir + "Message.eml");
client.forward("Recipient1@domain.com", "Recipient2@domain.com", message);
~~~ 

### **Reenviando un Correo Electrónico sin usar MailMessage**

La API también admite el reenvío de mensajes EML sin cargarlos primero en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Esto es útil en casos donde hay recursos limitados en términos de memoria del sistema.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java

String host = "mail.server.com";
String username = "username";
String password = "password";
int smtpPort = 587;
String sender = "Sender@domain.com";
MailAddressCollection recipients = new MailAddressCollection();
recipients.add("recepient1@domain.com, recepient2@domain.com");

try (SmtpClient client = new SmtpClient(host, smtpPort, username, password, SecurityOptions.Auto)) {
    String fileName = "test.eml";
    try (FileInputStream fs = new FileInputStream(new File(dataDir + fileName))) {
        client.forward(sender, recipients, fs);
    }
}
~~~ 

## **Realizando Combinar Correspondencia**

Las combinaciones de correspondencia le ayudan a crear y enviar un lote de mensajes de correo electrónico similares. El núcleo de los correos electrónicos es el mismo, pero el contenido se puede personalizar. Típicamente, los detalles de contacto de un destinatario (nombre, apellido, empresa, etc.) se utilizan para personalizar el correo electrónico.

|**Ilustración de cómo funciona una combinación de correspondencia:**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email permite a los desarrolladores configurar combinaciones de correspondencia que incluyen datos de una variedad de fuentes de datos.

Para realizar una combinación de correspondencia con Aspose.Email, siga los siguientes pasos:

1. Cree una función con la firma del nombre
1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Especifique el remitente, el receptor, el asunto y el cuerpo.
1. Cree una firma para el final del correo electrónico.
1. Cree una instancia de la clase [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) y pásale la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
1. Tome la firma en la instancia de [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) .
1. Cree una instancia de la clase [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Agregue las columnas **Receipt**, **FirstName** y **LastName** como fuentes de datos en la clase [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
1. Cree una instancia de la clase [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Especifique la dirección del recibo, el primer y el segundo nombre en el objeto [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
1. Cree una instancia de la clase [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Especifique las instancias de [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/)  y [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) en la instancia de [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
1. Cree una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y especifique el servidor, puerto, nombre de usuario y contraseña.
1. Envíe correos electrónicos utilizando el método [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .

En el ejemplo a continuación, #FirstName# indica una columna de [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) cuya valor es establecido por el usuario. El siguiente fragmento de código muestra cómo realizar la combinación de correspondencia.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visite https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // La ruta al directorio de archivos.
    String dstEmail = dataDir + "EmbeddedImage.msg";

    // Crear una nueva instancia de MailMessage
    MailMessage msg = new MailMessage();

    // Agregar asunto y dirección de envío
    msg.setSubject("Hola, #FirstName#");
    msg.setFrom(MailAddress.to_MailAddress("sender@sender.com"));

    // Agregar dirección de correo electrónico para también enviar el correo y agregar campo de mensaje al cuerpo HTML
    msg.getTo().add("your.email@gmail.com");
    String htmlBody = "Su mensaje aquí/r/n" + "Gracias por su interés en <STRONG>Aspose.Email</STRONG>.";

    // Usar GetSignment como rutina de plantilla, que proporcionará la misma firma
    htmlBody += "<br><br>Diviértete con esto.<br><br>#GetSignature()#";

    msg.setHtmlBody(htmlBody);

    // Crear un nuevo TemplateEngine con el mensaje MSG, registrar la rutina GetSignature. Se utilizará en MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.registerRoutine("GetSignature", new TemplateRoutine() {
        public Object invoke(Object[] args) {
            return getSignature(args);
        }
    });

    // Crear una nueva instancia de DataTable y completar una DataTable como fuente de datos
    DataTable dt = new DataTable();
    dt.getColumns().add("Receipt");
    dt.getColumns().add("FirstName");
    dt.getColumns().add("LastName");

    DataRow dr;
    dr = dt.newRow();
    dr.set("Receipt", "Nancy&lt;Nancy@somedomain.com&gt;");
    dr.set("FirstName", "Nancy");
    dr.set("LastName", "Doe");
    dt.getRows().add(dr);
    dr = dt.newRow();
    dr.set("Receipt", "Andrew&lt;Andrew@somedomain.com&gt;");
    dr.set("FirstName", "Andrew");
    dr.set("LastName", "Doe");
    dt.getRows().add(dr);
    dr = dt.newRow();
    dr.set("Receipt", "Janet&lt;Janet@somedomain.com&gt;");
    dr.set("FirstName", "Janet");
    dr.set("LastName", "Doe");
    dt.getRows().add(dr);

    MailMessageCollection messages;
    try {
        // Crear mensajes desde el mensaje y la fuente de datos.
        messages = engine.instantiate(dt);

        // Crear una instancia de SmtpClient y especificar servidor, puerto, nombre de usuario y contraseña
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.setSecurityOptions(SecurityOptions.Auto);

        // Enviar mensajes en masa
        client.send(messages);
    } catch (MailException ex) {
        System.err.println(ex);
    }

    catch (SmtpException ex) {
        System.err.println(ex);
    }

    System.out.println("Mensaje enviado después de realizar la combinación de correspondencia.");
}

// Rutina de plantilla para proporcionar firma
static Object getSignature(Object[] args) {
    return "Equipo de Aspose.Email<br>Aspose Ltd.<br>" + new Date().toString();
}
~~~ 

## **Realizando Combinación de Correspondencia Fila por Fila**

El usuario también puede combinar cada fila de datos de manera individual para obtener un objeto [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) preparado y completo. El método [TemplateEngine.merge](https://reference.aspose.com/email/java/com.aspose.email/templateengine/#merge-com.aspose.email.DataRow-) se puede utilizar para realizar una combinación de correspondencia fila por fila.

~~~Java
// Crear mensaje a partir de los datos en la fila actual.
MailMessage message = engine.merge(currentRow);
~~~