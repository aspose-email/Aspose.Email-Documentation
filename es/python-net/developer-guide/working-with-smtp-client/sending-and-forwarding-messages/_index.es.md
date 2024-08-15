---
title: "Envío y reenvío de mensajes"
url: /es/python-net/sending-and-forwarding-messages/
weight: 20
type: docs
---


La clase SmtpClient permite a las aplicaciones enviar correos electrónicos mediante el Protocolo simple de transferencia de correo (SMTP).

- La clase SmtpClient es la única entrada importante que utilizan los desarrolladores para enviar mensajes de correo.
- La clase SmtpClient también proporciona otros métodos comunes de entrega de correo electrónico, incluida la escritura de mensajes de correo electrónico en el sistema de archivos, la cola de mensajes, etc.
- La clase SmtpClient es totalmente compatible con estos dos modelos de programación:
  - Synchronous
- La clase SmtpClient también admite el envío de mensajes como TNEF.

Para enviar el mensaje de correo electrónico y bloquearlo mientras espera a que el correo electrónico se transmita al servidor SMTP, utilice uno de los métodos de envío sincrónico. Para permitir que el subproceso principal del programa continúe ejecutándose mientras se transmite el correo electrónico, utilice uno de los métodos asincrónicos de SendAsync.
## **Envío sincrónico de correos electrónicos**
Se puede enviar un mensaje de correo electrónico de forma sincrónica mediante el método Send de la clase SmtpClient. Envía el mensaje de correo electrónico especificado a través de un servidor SMTP para su entrega. El remitente, los destinatarios, el asunto y el cuerpo del mensaje se especifican mediante objetos String. Para enviar un mensaje de correo electrónico de forma sincrónica, siga los pasos que se indican a continuación:

1. Crea una instancia de la clase MailMessage y establece sus propiedades.
1. Cree una instancia de la clase SMTPClient y especifique el host, el puerto, el nombre de usuario y la contraseña.
1. Envíe el mensaje mediante el método Send de la clase SmtpClient y pase la instancia de MailMessage.

El siguiente fragmento de código muestra cómo enviar correos electrónicos de forma sincrónica.

{{% alert color="primary" %}}

La API no admite el envío de correos electrónicos de forma asincrónica.

{{% /alert %}}

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendEmailsSynchronously-SendEmailsSynchronously.py" >}}

## **Envío de mensajes almacenados desde un disco**

Si necesita enviar mediante programación un mensaje de correo electrónico previamente redactado y almacenado en formato EML, utilice [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) clase para cargar el archivo existente y guardarlo antes de enviarlo. Luego envíelo usando el [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) clase que especifica el nombre de host, el nombre de usuario y la contraseña del servidor SMTP para la autenticación. El método «enviar» del [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) la clase se usa para enviar el mensaje de correo electrónico. Todo el proceso se muestra en el ejemplo de código siguiente.

```py
import aspose.email as ae

message = ae.MailMessage.load("test.eml")

# Send this message using SmtpClient
client = ae.clients.SmtpClient("host", "username", "password")
client.send(message)
```

## **Envío de correo electrónico de texto sin formato**
Los siguientes ejemplos de programación muestran cómo enviar un mensaje de correo electrónico de texto sin formato. La propiedad Body, una propiedad de la clase MailMessage, se usa para especificar el contenido de texto sin formato del cuerpo del mensaje. Para enviar un mensaje de correo electrónico de texto sin formato, sigue estos pasos:

- Crea una instancia de la clase MailMessage.
- Especifique las direcciones de correo electrónico del remitente y del destinatario en la instancia de MailMessage.
- Especifique el contenido de TextBody, que se utiliza para el mensaje de texto sin formato.
- Crea una instancia de la clase SmtpClient y envía el correo electrónico.

El siguiente fragmento de código muestra cómo enviar correos electrónicos de texto sin formato.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingPlainTextMessage-SendingPlainTextMessage.py" >}}
## **Envío de correo electrónico con cuerpo HTML**
Los ejemplos de programación que aparecen a continuación muestran cómo puede enviar un mensaje de correo electrónico HTML sencillo. El HTMLBody, una propiedad de la clase MailMessage, se usa para especificar el contenido HTML del cuerpo del mensaje. Para enviar un correo electrónico HTML sencillo, sigue estos pasos:

- Crea una instancia de la clase MailMessage.
- Especifique la dirección de correo electrónico del remitente y del destinatario en la instancia de MailMessage.
- Especifique el contenido de HTMLBody.
- Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

Para los fines de este artículo, el contenido HTML del correo electrónico es rudimentario: <html><body>Este es el cuerpo HTML</body></html> La mayoría de los correos electrónicos HTML serán más complejos. El siguiente fragmento de código muestra cómo enviar correos electrónicos con un cuerpo HTML.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SettingHTMLBody-SettingHTMLBody.py" >}}
## **Envío de correo electrónico con texto de mensaje alternativo**
Los siguientes ejemplos de programación muestran cómo enviar un mensaje de correo electrónico HTML sencillo con contenido alternativo. Utilice la clase AlternateView para especificar copias de un mensaje de correo electrónico en diferentes formatos. Por ejemplo, si envía un mensaje en HTML, es posible que también desee proporcionar una versión de texto sin formato para los destinatarios que utilizan lectores de correo electrónico que no pueden mostrar contenido HTML. O bien, si va a enviar un boletín, puede que desee proporcionar una copia del texto sin formato para los destinatarios que hayan elegido recibir una versión en texto sin formato. Para enviar un correo electrónico con texto alternativo, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Especifique las direcciones de correo electrónico del remitente y del destinatario en la instancia de MailMessage.
1. Crea una instancia de la clase AlternateView.

Esto crea una vista alternativa a un mensaje de correo electrónico con el contenido especificado en la cadena.

1. Añade una instancia de la clase AlternateView al objeto MailMessage.
1. Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El siguiente fragmento de código muestra cómo enviar correos electrónicos con texto alternativo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SetAlternateText-SetAlternateText.py" >}}
## **Envío masivo de correos electrónicos**
Enviar correos electrónicos de forma masiva significa enviar un lote de correos electrónicos en un solo mensaje. Podemos enviar lotes de correo electrónico utilizando el método BulkSend de la clase SmtpClient:

1. Crea una instancia de la clase SmtpClient.
1. Especifique las propiedades de la clase SmtpClient.
1. Crea una instancia de la clase MailMessage.
1. Especifique el remitente, el destinatario, el asunto del correo y el mensaje en la instancia de la clase MailMessage.
1. Repite los dos pasos anteriores de nuevo si quieres enviar un correo electrónico a otra persona.
1. Crea una instancia de la clase MailMessageCollection.
1. Añade una instancia de la clase MailMessage en el objeto de la clase MailMessageCollection.
1. Ahora envía tu correo electrónico usando el método BulkSend de la clase SmtpClient pasando la instancia de la clase MailMessageCollection en él.

El siguiente fragmento de código muestra cómo enviar correos electrónicos masivos.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingBulkEmails-SendingBulkEmails.py" >}}

## **Envío de correos electrónicos con MultiConnection**

Las siguientes propiedades del [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) La clase permite a un cliente utilizar múltiples conexiones al servidor para enviar correos electrónicos. Esto puede resultar beneficioso en situaciones en las que el cliente necesita enviar un gran volumen de correos electrónicos y desea distribuir la carga de trabajo entre varias conexiones.

- La propiedad «use_multi_connection» obtiene o establece un valor que indica si el cliente tiene que usar varias conexiones para operaciones de gran carga.
- La propiedad 'connections_quantity' obtiene o establece la cantidad de conexiones en el modo de conexión múltiple.
```
Please note, the use of this mode will not necessarily lead to performance increasing.
```
El siguiente ejemplo de código muestra cómo implementar esta función en un proyecto:
```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.send(messages)
```

## **Enviar mensaje como TNEF**
Los correos electrónicos de TNEF tienen un formato especial que puede perderse si se envían mediante la API estándar. Aspose.Email ofrece la capacidad de enviar correos electrónicos como TNEF, preservando así el formato. La propiedad UseTnef de la clase SMTPClient se puede configurar para enviar el correo electrónico como TNEF. El siguiente fragmento de código muestra cómo enviar un mensaje como TNEF.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendMsgAsTNEF-SendMsgAsTNEF.py" >}}
## **Envío de convocatorias de reunión**
Microsoft Outlook ofrece funciones de calendario y administración de correo electrónico. Cuando un usuario abre un correo electrónico con una invitación a un evento, Outlook le pide que acepte o rechace la invitación. Aspose.Email permite a los desarrolladores añadir funciones de calendario a sus correos electrónicos.
### **Envío de solicitudes por correo electrónico**
Para enviar convocatorias de reunión por correo electrónico, sigue estos pasos:

- Crea una instancia de la clase MailMessage.
- Especifique las direcciones del remitente y del destinatario mediante una instancia de la clase MailMessage.
- Inicialice una instancia de la clase Appointment y pásele valores.
- Especifique el resumen y la descripción en la instancia de Calendario.
- Agregue el calendario a la instancia de MailMessage y páselo a la instancia de Appointment.

|**Solicitud de reunión de iCalendar enviada por correo electrónico**|
|: - |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
El siguiente fragmento de código muestra cómo enviar solicitudes por correo electrónico.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingMeetingRequestsViaEmail-SendingMeetingRequestsViaEmail.py" >}}
### **iCalendar es compatible con IBM Lotus Notes**
La función de calendario de Aspose.Email.Mail se basa en el estándar iCalendar, un estándar para el intercambio de datos de calendario (referencia de sintaxis RFC 2445 o RFC2445). Por lo tanto, no solo es compatible con Microsoft Outlook, sino también con IBM Lotus Notes. Para enviar una convocatoria de reunión en Lotus Notes, siga los mismos pasos que se han mencionado anteriormente.
## **Reenviar un correo electrónico mediante un cliente SMTP**
### **Reenvío de correo electrónico con un cliente SMTP**
Reenviar un correo electrónico es una práctica común en la comunicación digital de la vida diaria. Un correo electrónico recibido se puede reenviar a destinatarios específicos sin compartirlo con los remitentes originales. El SMTPClient de la API Aspose.Email ofrece la capacidad de reenviar un correo electrónico a destinatarios específicos. Su método de reenvío se puede usar para reenviar un correo electrónico recibido o guardado a los destinatarios deseados, como se muestra en este artículo. El siguiente fragmento de código muestra cómo reenviar un correo electrónico mediante un cliente SMTP.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-ForwardEmail-ForwardEmail.py" >}}

### **Reenviar correo electrónico sin usar MailMessage**

La API también admite el reenvío de mensajes EML sin cargarlos primero en [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class). Esto es útil en los casos en que hay recursos limitados en términos de memoria del sistema.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient(host, smtp_port, username, password, ae.clients.SecurityOptions.AUTO)
file = open("test.eml", "rb")
client.forward(sender, recipients, file)
```
