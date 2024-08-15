---
title: "Envío y reenvío de mensajes: envíe mensajes de correo electrónico de Outlook mediante el programa Java"
url: /es/java/sending-and-forwarding-messages/
weight: 20
type: docs
linktitle: "Envío y reenvío de mensajes"
---


The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) La clase permite a las aplicaciones enviar correos electrónicos mediante el Protocolo simple de transferencia de correo (SMTP).

- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class es la única entrada importante que utilizan los desarrolladores para enviar mensajes de correo.
- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) La clase también proporciona otros métodos comunes de entrega de correo electrónico, incluida la escritura de mensajes de correo electrónico en el sistema de archivos, la cola de mensajes, etc.
- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class es totalmente compatible con estos dos modelos de programación:
  - [Synchronous](#sending-emails-synchronously)
  - [Asynchronous](#sending-emails-asynchronously)
- The [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) la clase también admite [enviar mensajes como TNEF](#sending-message-as-tnef)

Para enviar el mensaje de correo electrónico y bloquearlo mientras espera a que el correo electrónico se transmita al servidor SMTP, utilice uno de los métodos de envío sincrónico. Para permitir que el subproceso principal del programa continúe ejecutándose mientras se transmite el correo electrónico, utilice el [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) method.

## **Envío sincrónico de correos electrónicos**

Se puede enviar un mensaje de correo electrónico de forma sincrónica mediante el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) método. Envía el mensaje de correo electrónico especificado a través de un servidor SMTP para su entrega. El remitente, los destinatarios, el asunto y el cuerpo del mensaje se especifican mediante objetos String. Para enviar un mensaje de correo electrónico de forma sincrónica, siga los pasos que se indican a continuación:

1. Crea una instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase y establece sus propiedades.
1. Crea una instancia de [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y especifique el host, el puerto, el nombre de usuario y la contraseña.
1. Envía el mensaje usando el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.IConnection-com.aspose.email.MailMessage-) método y pase el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.

El siguiente fragmento de código Java muestra cómo enviar correos electrónicos de Outlook de forma sincrónica.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Declare msg as MailMessage instance
MailMessage msg = new MailMessage();

// Crea una instancia de SmtpClient class
SmtpClient client = new SmtpClient();

// Specify your mailing host server, Username, Password, Port # and Security option
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);

try {
    // Client.Send will send this message
    client.send(msg);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Envío de correos electrónicos de forma asincrónica**

En ocasiones, es posible que desee enviar correo de forma asincrónica. Por ejemplo, si envía mucho correo a través de la aplicación, es posible que el enfoque sincrónico no funcione. En tal escenario, puede usar [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-). El [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) método del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) la clase envía un mensaje de correo electrónico a un servidor SMTP para su entrega. Este método no bloquea el hilo de llamada y permite a la persona que llama pasar un objeto al método que se invoca cuando se completa la operación. Para enviar un mensaje de correo electrónico de Outlook de forma asincrónica en Java, sigue estos pasos:

1. Crea una instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase y usa sus diferentes propiedades.
1. Crea una instancia de [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y especifique el host, el puerto, el nombre de usuario y la contraseña.
1. Cree una instancia definida por el usuario que se pasará al método y se invocará cuando finalice la operación asincrónica.
1. Enviar el mensaje usando [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) método de [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y aprobar el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia e instancia definida por el usuario en ella junto con una función de devolución de llamada que se llamará cuando se complete la operación.

Para recibir una notificación cuando se haya enviado el correo electrónico o se haya cancelado la operación, la función de devolución de llamada pasó al [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) se llama método. Después de llamar al [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) método, no es necesario esperar a que un mensaje de correo electrónico se envíe por completo. Podemos llamar a otro método [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) al mismo tiempo. Cuando se ha enviado un correo electrónico mediante el [beginSend](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#beginSend-com.aspose.email.IConnection-com.aspose.email.MailMessage-) método, el fragmento de código imprime un mensaje («Mensaje enviado»). El siguiente programa o fragmento de código de Java muestra cómo enviar correos electrónicos de forma asincrónica.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

public static void run() {
    sendMail();
}

static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient();
    client.setHost("mail.server.com");
    // Specify your mail Username, Password, Port # and security option
    client.setUsername("username");
    client.setPassword("password");
    client.setPort(587);
    client.setSecurityOptions(SecurityOptions.SSLExplicit);
    return client;
}

static void sendMail() {
    try {

        // Declare msg as MailMessage instance
        MailMessage msg = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Test subject", "Test body");
        SmtpClient client = getSmtpClient();
        Object state = new Object();
        IAsyncResult ar = client.beginSend(msg, callback, state);
        // If the user canceled the send, and mail hasn't been sent yet,
        client.cancelAsyncOperation(ar);

        msg.dispose();
        System.out.println("Goodbye.");
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
            System.out.println("Send canceled.");
        }

        if (task != null && task.getErrorInfo() != null) {
            System.out.println(task.getErrorInfo());
        } else {
            System.out.println("Message Sent.");
        }
    }
};
~~~

## **Envío de mensajes almacenados desde un disco**

Los archivos EML (archivos de correo electrónico de Outlook Express) contienen un encabezado de correo electrónico, el cuerpo del mensaje y cualquier archivo adjunto. Aspose.Email permite a los desarrolladores trabajar con archivos EML de diferentes maneras. Este artículo muestra cómo cargar archivos EML desde el disco y enviarlos como correos electrónicos con SMTP. Puede cargar archivos.eml desde el disco o transmitirlos al [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase y enviar el mensaje de correo electrónico mediante [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase. El [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class es la clase principal para crear nuevos mensajes de correo electrónico, cargar archivos de mensajes de correo electrónico desde un disco o transmisión y guardar los mensajes. El siguiente fragmento de código Java muestra cómo enviar los mensajes almacenados desde el disco.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Load an EML file in MailMessage class
MailMessage message = MailMessage.load(dataDir + "test.eml");

// Send this message using SmtpClient
SmtpClient client = new SmtpClient("host", "username", "password");

try {
    client.send(message);
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Envío de correo electrónico de texto sin formato**

Los siguientes ejemplos de programación muestran cómo enviar un mensaje de correo electrónico de texto sin formato. El [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) propiedad, una propiedad del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class, se usa para especificar el contenido de texto sin formato del cuerpo del mensaje. Para enviar un mensaje de correo electrónico de texto sin formato, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Especifique las direcciones de correo electrónico del remitente y del destinatario en el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
- Especifique el [Body](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBody--) contenido, usado para el mensaje de texto sin formato.
- Crea una instancia del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y envía el correo electrónico.

El siguiente fragmento de código muestra cómo enviar un correo electrónico de texto sin formato.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Crea una instancia del MailMessage class
MailMessage message = new MailMessage();

// Set From field, To field and Plain text body
message.setFrom(MailAddress.to_MailAddress("sender@sender.com"));
message.getTo().add("receiver@receiver.com");
message.setBody("This is Plain Text Body");

// Crea una instancia del SmtpClient class
SmtpClient client = new SmtpClient();

// And Specify your mailing host server, Username, Password and Port
client.setHost("smtp.server.com");
client.setUsername("Username");
client.setPassword("Password");
client.setPort(25);

try {
    // Client.Send will send this message
    client.send(message);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

## **Envío de correo electrónico con cuerpo HTML**

Los ejemplos de programación que aparecen a continuación muestran cómo puede enviar un mensaje de correo electrónico HTML sencillo. El [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), propiedad del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class, se usa para especificar el contenido HTML del cuerpo del mensaje. Para enviar un correo electrónico HTML sencillo, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Especifique la dirección de correo electrónico del remitente y del destinatario en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
- Especifique el [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) content.
- Crea una instancia del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y envía el correo electrónico usando el [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) method.

Para los fines de este artículo, el contenido HTML del correo electrónico es rudimentario: <html><body>Este es el cuerpo HTML</body></html> La mayoría de los correos electrónicos HTML serán más complejos. El siguiente fragmento del programa Java muestra cómo enviar un correo electrónico con un cuerpo HTML.

~~~Java
public static void run() {
    // Declare msg as MailMessage instance
    MailMessage msg = new MailMessage();

    // Use MailMessage properties like specify sender, recipient, message and HtmlBody
    msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
    msg.setTo(MailAddressCollection.to_MailAddressCollection("asposetest123@gmail.com"));
    msg.setSubject("Test subject");
    msg.setHtmlBody("<html><body>Este es el cuerpo HTML</body></html>");
    SmtpClient client = getSmtpClient();
    try {
        // Client will send this message
        client.send(msg);
        System.out.println("Message sent");
    } catch (Exception ex) {
        System.err.println(ex);
    }

    System.out.println("Email sent with HTML body.");
}

private static SmtpClient getSmtpClient() {
    SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
    client.setSecurityOptions(SecurityOptions.Auto);
    return client;
}
~~~

## **Envío de correo electrónico con texto de mensaje alternativo**

Los siguientes ejemplos de programación muestran cómo enviar un mensaje de correo electrónico HTML sencillo con contenido alternativo. Utilice el [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) clase para especificar copias de un mensaje de correo electrónico en diferentes formatos. Por ejemplo, si envía un mensaje en HTML, es posible que también desee proporcionar una versión de texto sin formato para los destinatarios que utilizan lectores de correo electrónico que no pueden mostrar contenido HTML. O bien, si va a enviar un boletín, puede que desee proporcionar una copia del texto sin formato para los destinatarios que hayan elegido recibir una versión en texto sin formato. Para enviar un correo electrónico con texto alternativo, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Especifique las direcciones de correo electrónico del remitente y del destinatario en el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Crea una instancia del [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) class.

Esto crea una vista alternativa a un mensaje de correo electrónico con el contenido especificado en la cadena.

1. Agregue la instancia del [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) clase a la [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) object.
1. Crea una instancia del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y envía el correo electrónico usando el [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessage-) method.

El siguiente fragmento de código muestra cómo enviar un correo electrónico con texto alternativo.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Declare message as MailMessage instance
MailMessage message = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //String
AlternateView alternate = AlternateView.createAlternateViewFromString("Alternate Text");

// Adding alternate text
message.getAlternateViews().addItem(alternate);
~~~

## **Envío masivo de correos electrónicos**

Enviar correos electrónicos de forma masiva significa enviar un lote de correos electrónicos en un solo mensaje. Podemos enviar un lote de correos electrónicos utilizando el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) sobrecarga de métodos que acepta un [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class:

1. Crea una instancia de [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class.
1. Especifique el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) propiedades de clase.
1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Especifique el remitente, el destinatario, el asunto del correo y el mensaje en la instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Repite los dos pasos anteriores de nuevo si quieres enviar un correo electrónico a otra persona.
1. Crea una instancia de [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class.
1. Añadir una instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase en el objeto del [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class.
1. Ahora envía tu correo electrónico usando el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) método pasando la instancia de [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) clase en él.

El siguiente fragmento de código muestra cómo enviar correos electrónicos masivos.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create SmtpClient as client and specify server, port, user name and password
SmtpClient client = new SmtpClient("mail.server.com", 25, "Username", "Password");

// Create instances of MailMessage class and Specify To, From, Subject and Message
MailMessage message1 = new MailMessage("msg1@from.com", "msg1@to.com", "Subject1", "message1, how are you?");
MailMessage message2 = new MailMessage("msg1@from.com", "msg2@to.com", "Subject2", "message2, how are you?");
MailMessage message3 = new MailMessage("msg1@from.com", "msg3@to.com", "Subject3", "message3, how are you?");

// Crea una instancia de MailMessageCollection class
MailMessageCollection manyMsg = new MailMessageCollection();
manyMsg.addItem(message1);
manyMsg.addItem(message2);
manyMsg.addItem(message3);

// Use client.BulkSend function to complete the bulk send task
try {
    // Send Message using BulkSend method
    client.send(manyMsg);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~
## **Obtenga información sobre los mensajes masivos enviados**

Cuando envías mensajes de forma masiva, puedes obtener información sobre el número de mensajes enviados correctamente y la lista de estos mensajes. El [SucceededSending](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setSucceededSending-com.aspose.ms.System.EventHandler-com.aspose.email.MailMessageEventArgs--) el evento se usa para este propósito.

El ejemplo de código que aparece a continuación muestra cómo obtener información sobre el número de mensajes enviados correctamente:

```java
try (SmtpClient client = new SmtpClient(host, SecurityOptions.Auto)) {
    final AtomicInteger messageCount = new AtomicInteger(0);

    client.setSucceededSending(new EventHandler<MailMessageEventArgs>() {
        public void invoke(Object sender, MailMessageEventArgs eventArgs) {
            System.out.println("The message " + eventArgs.getMessage().getSubject() + " was successfully sent.");
            messageCount.incrementAndGet();
        }
    });

    client.send(messages);

    System.out.println(messageCount + " messages were successfully sent.");
}
```


## **Envío de correos electrónicos con MultiConnection**

[SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) proporciona un [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseMultiConnection-int-) propiedad que se puede usar para crear múltiples conexiones para operaciones pesadas. También puede establecer el número de conexiones que se usarán durante el modo multiconexión utilizando [SmtpClient.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setConnectionsQuantity-int-). El siguiente fragmento de código muestra el uso del modo multiconexión para enviar varios mensajes.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient smtpClient = new SmtpClient();
smtpClient.setHost("<HOST>");
smtpClient.setUsername("<USERNAME>");
smtpClient.setPassword("<PASSWORD>");
smtpClient.setPort(587);
smtpClient.setSupportedEncryption(EncryptionProtocols.Tls);
smtpClient.setSecurityOptions(SecurityOptions.SSLExplicit);

List<MailMessage> messages = new ArrayList<MailMessage>();
for (int i = 0; i < 20; i++) {
    MailMessage message = new MailMessage("<EMAIL ADDRESS>", "<EMAIL ADDRESS>", "Test Message - " + UUID.randomUUID().toString(),
            "SMTP Send Messages with MultiConnection");
    messages.add(message);
}

smtpClient.setConnectionsQuantity(5);
smtpClient.setUseMultiConnection(MultiConnectionMode.Enable);
smtpClient.send(messages);
~~~

{{% alert color="primary" %}}

Tenga en cuenta que el uso del modo multiconexión no garantiza un aumento del rendimiento.

{{% /alert %}}

## **Enviar un mensaje como TNEF**

Los correos electrónicos de TNEF tienen un formato especial que puede perderse si se envían mediante la API estándar. Aspose.Email ofrece la capacidad de enviar correos electrónicos como TNEF, preservando así el formato. El [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [UseTnef](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setUseTnef\(boolean\)) la propiedad se puede configurar para enviar el correo electrónico como TNEF. El siguiente fragmento de código muestra cómo enviar un mensaje como TNEF.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

String emlFileName = dataDir + "Message.eml"; // A TNEF Email

// Load from eml
MailMessage eml1 = MailMessage.load(emlFileName, new EmlLoadOptions());
eml1.setFrom(MailAddress.to_MailAddress("somename@gmail.com"));
eml1.getTo().clear();
eml1.getTo().addItem(new MailAddress("first.last@test.com"));
eml1.setSubject("With PreserveTnef flag during loading");
eml1.setDate(new Date());
SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "somename", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setUseTnef(true); // Use this flag to send as TNEF
client.send(eml1);
~~~

## **Envío de convocatorias de reunión**

Microsoft Outlook ofrece funciones de calendario y administración de correo electrónico. Cuando un usuario abre un correo electrónico con una invitación a un evento, Outlook le pide que acepte o rechace la invitación. Aspose.Email permite a los desarrolladores añadir funciones de calendario a sus correos electrónicos.

### **Envío de solicitudes por correo electrónico**

Para enviar convocatorias de reunión por correo electrónico, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Especifique las direcciones del remitente y del destinatario mediante una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Inicialice una instancia del [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) clasifique y apruebe sus valores.
- Especifique el resumen y la descripción en el [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/) instance.
- Añada el [Calendar](https://reference.aspose.com/email/java/com.aspose.email/calendar/)) a la [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia y pásala al [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) instance.

|**Solicitud de reunión de iCalendar enviada por correo electrónico**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
El siguiente fragmento de código muestra cómo enviar solicitudes por correo electrónico.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Crea una instancia del MailMessage class
MailMessage msg = new MailMessage();

// Set the sender, recipient, who will receive the meeting request. Basically, the recipient is the same as the meeting attendees
msg.setFrom(MailAddress.to_MailAddress("newcustomeronnet@gmail.com"));
msg.setTo(MailAddressCollection.to_MailAddressCollection("person1@domain.com, person2@domain.com, person3@domain.com, asposetest123@gmail.com"));

// Create Appointment instance
Calendar cal = Calendar.getInstance();
cal.set(2015, Calendar.JULY, 17, 13, 0, 0);
Date startDate = cal.getTime();
cal.set(2015, Calendar.JULY, 17, 14, 0, 0);
Date endDate = cal.getTime();
Appointment app = new Appointment("Room 112", startDate, endDate, msg.getFrom(), msg.getTo());
app.setSummary("Release Meetting");
app.setDescription("Discuss for the next release");

// Add appointment to the message and Crea una instancia de SmtpClient class
msg.addAlternateView(app.requestApointment());
SmtpClient client = getSmtpClient();

try {
    // Client.Send will send this message
    client.send(msg);
    System.out.println("Message sent");
} catch (Exception ex) {
    System.err.println(ex);
}
~~~

### **iCalendar es compatible con IBM Lotus Notes**

La función de calendario Aspose.Email se basa en el estándar iCalendar, un estándar para el intercambio de datos de calendario (referencia de sintaxis RFC 2445 o RFC2445). Por lo tanto, no solo es compatible con Microsoft Outlook, sino también con IBM Lotus Notes. Para enviar una convocatoria de reunión en Lotus Notes, siga los mismos pasos que se han mencionado anteriormente.

## **Reenviar un correo electrónico mediante un cliente SMTP**

### **Reenvío de correo electrónico con un cliente SMTP**

Reenviar un correo electrónico es una práctica común en la comunicación digital de la vida diaria. Un correo electrónico recibido se puede reenviar a destinatarios específicos sin compartirlo con los remitentes originales. API Aspose.Email [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) proporciona la capacidad de reenviar un correo electrónico a destinatarios específicos. Es [Forward](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#forward-java.lang.String-com.aspose.email.MailAddressCollection-com.aspose.email.MailMessage-) El método se puede utilizar para reenviar un correo electrónico recibido o guardado a los destinatarios deseados, como se muestra en este artículo. El siguiente fragmento de código muestra cómo reenviar un correo electrónico mediante el cliente SMTP.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Crea una instancia de SmtpClient class
SmtpClient client = new SmtpClient();

// Specify your mailing host server, Username, Password, Port and SecurityOptions
client.setHost("mail.server.com");
client.setUsername("username");
client.setPassword("password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
MailMessage message = MailMessage.load(dataDir + "Message.eml");
client.forward("Recipient1@domain.com", "Recipient2@domain.com", message);
~~~

### **Reenviar correo electrónico sin usar MailMessage**

La API también admite el reenvío de mensajes EML sin cargarlos primero en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Esto es útil en los casos en que hay recursos limitados en términos de memoria del sistema.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

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

## **Realizar una combinación de correspondencia**

Las combinaciones de correspondencia le ayudan a crear y enviar un lote de mensajes de correo electrónico similares. El núcleo de los correos electrónicos es el mismo, pero el contenido se puede personalizar. Por lo general, los datos de contacto del destinatario (nombre, segundo nombre, empresa, etc.) se utilizan para personalizar el correo electrónico.

|**Ilustración de cómo funciona una combinación de correspondencia:**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_2.png)|
Aspose.Email permite a los desarrolladores configurar combinaciones de correspondencia que incluyen datos de una variedad de fuentes de datos.

Para realizar una combinación de correspondencia con Aspose.Email, siga estos pasos:

1. Crea una función con la firma del nombre
1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Especifique el remitente, el destinatario, el asunto y el cuerpo.
1. Crea una firma para el final del correo electrónico.
1. Crea una instancia del [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) clase y apruebalo el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Firme en el [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/) instance.
1. Crea una instancia del [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) class.
1. Agregue las columnas **Receipt**, **FirstName** and **LastName** como fuentes de datos en el [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) class.
1. Crea una instancia del [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) class.
1. Especifique la dirección del recibo, el nombre y los apellidos en el [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) object.
1. Crea una instancia del [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class
1. Especifique el [TemplateEngine](https://reference.aspose.com/email/java/com.aspose.email/templateengine/)  and [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) instancias en el [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) instance.
1. Crea una instancia del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y especifique el servidor, el puerto, el nombre de usuario y la contraseña.
1. Envía correos electrónicos mediante el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class [send](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#send-com.aspose.email.MailMessageCollection-) method.

En el siguiente ejemplo, #FirstName # indica un [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) columna, cuyo valor lo establece el usuario. El siguiente fragmento de código muestra cómo combinar correspondencia.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
public static void run() {
    // The path to the File directory.
    String dstEmail = dataDir + "EmbeddedImage.msg";

    // Create a new MailMessage instance
    MailMessage msg = new MailMessage();

    // Add subject and from address
    msg.setSubject("Hello, #FirstName#");
    msg.setFrom(MailAddress.to_MailAddress("sender@sender.com"));

    // Add email address to send email also Add mesage field to HTML body
    msg.getTo().add("your.email@gmail.com");
    String htmlBody = "Your message here/r/n" + "Thank you for your interest in <STRONG>Aspose.Email</STRONG>.";

    // Use GetSignment as the template routine, which will provide the same signature
    htmlBody += "<br><br>Have fun with it.<br><br>#GetSignature()#";

    msg.setHtmlBody(htmlBody);

    // Create a new TemplateEngine with the MSG message, Register GetSignature routine. It will be used in MSG.
    TemplateEngine engine = new TemplateEngine(msg);
    engine.registerRoutine("GetSignature", new TemplateRoutine() {
        public Object invoke(Object[] args) {
            return getSignature(args);
        }
    });

    // Crea una instancia de DataTable and Fill a DataTable as data source
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
        // Create messages from the message and datasource.
        messages = engine.instantiate(dt);

        // Crea una instancia de SmtpClient and specify server, port, username and password
        SmtpClient client = new SmtpClient("smtp.gmail.com", 587, "your.email@gmail.com", "your.password");
        client.setSecurityOptions(SecurityOptions.Auto);

        // Send messages in bulk
        client.send(messages);
    } catch (MailException ex) {
        System.err.println(ex);
    }

    catch (SmtpException ex) {
        System.err.println(ex);
    }

    System.out.println("Message sent after performing mail merge.");
}

// Template routine to provide signature
static Object getSignature(Object[] args) {
    return "Aspose.Email Team<br>Aspose Ltd.<br>" + new Date().toString();
}
~~~

## **Realización de una combinación de correspondencia por filas**

El usuario también puede combinar una fila de datos individual para obtener una completa y preparada [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) objeto. El [TemplateEngine.merge](https://reference.aspose.com/email/java/com.aspose.email/templateengine/#merge-com.aspose.email.DataRow-) este método se puede utilizar para realizar una combinación de correspondencia por filas.

~~~Java
// Create message from the data in current row.
MailMessage message = engine.merge(currentRow);
~~~
