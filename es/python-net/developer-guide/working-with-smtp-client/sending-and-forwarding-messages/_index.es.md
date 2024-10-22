---
title: "Envío y reenvío de mensajes"
url: /es/python-net/sending-and-forwarding-messages/
weight: 20
type: docs
---

La clase SmtpClient permite a las aplicaciones enviar correos electrónicos utilizando el Protocolo Simple de Transferencia de Correo (SMTP).

- La clase SmtpClient es la única entrada principal que los desarrolladores utilizan para enviar mensajes de correo.
- La clase SmtpClient también proporciona otros métodos comunes de entrega de correo electrónico, incluyendo la escritura de mensajes de correo en el sistema de archivos, cola de mensajes, etc.
- La clase SmtpClient admite completamente estos dos modelos de programación:
  - Sincrónico
- La clase SmtpClient también admite el envío de mensajes como TNEF

Para enviar el mensaje de correo electrónico y bloquearse mientras espera que el correo se transmita al servidor SMTP, use uno de los métodos Send sincrónicos. Para permitir que el hilo principal de su programa continúe ejecutándose mientras se transmite el correo electrónico, use uno de los métodos SendAsync asincrónicos.
## **Envío de correos electrónicos de forma sincrónica**
Un mensaje de correo electrónico se puede enviar de forma sincrónica utilizando el método Send de la clase SmtpClient. Envía el mensaje de correo electrónico especificado a través de un servidor SMTP para su entrega. El remitente del mensaje, los destinatarios, el asunto y el cuerpo del mensaje se especifican utilizando objetos String. Para enviar un mensaje de correo electrónico de forma sincrónica, siga los pasos que se indican a continuación:

1. Cree una instancia de la clase MailMessage y establezca sus propiedades.
1. Cree una instancia de la clase SmtpClient y especifique el Host, el puerto, el nombre de usuario y la contraseña.
1. Envíe el mensaje utilizando el método Send de la clase SmtpClient y pase la instancia de MailMessage.

El siguiente fragmento de código le muestra cómo enviar correos electrónicos de forma sincrónica.

{{% alert color="primary" %}} 

El envío de correos electrónicos de forma asincrónica no es compatible con la API.

{{% /alert %}} 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendEmailsSynchronously-SendEmailsSynchronously.py" >}}

## **Envío de mensajes almacenados desde el disco**

Si necesita enviar programáticamente un mensaje de correo electrónico precompuesto almacenado en formato EML, utilice la clase [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) para cargar el archivo existente y mantenerlo antes de enviarlo. Luego, envíelo utilizando la clase [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) especificando el nombre de host del servidor SMTP, el nombre de usuario y la contraseña para la autenticación. El método 'send' de la clase [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) se utiliza para enviar el mensaje de correo electrónico. Todo el proceso se muestra en el siguiente ejemplo de código.

```py
import aspose.email as ae

message = ae.MailMessage.load("test.eml")

# Enviar este mensaje usando SmtpClient
client = ae.clients.SmtpClient("host", "username", "password")
client.send(message)
```

## **Envío de correo electrónico en texto plano**
Los ejemplos de programación a continuación muestran cómo enviar un mensaje de correo electrónico en texto plano. La propiedad Body, una propiedad de la clase MailMessage, se utiliza para especificar el contenido de texto plano del cuerpo del mensaje. Para enviar un mensaje de correo electrónico en texto plano, siga estos pasos:

- Cree una instancia de la clase MailMessage.
- Especifique las direcciones de correo electrónico del remitente y del receptor en la instancia de MailMessage.
- Especifique el contenido de TextBody, utilizado para el mensaje en texto plano.
- Cree una instancia de la clase SmtpClient y envíe el correo electrónico.

El siguiente fragmento de código le muestra cómo enviar correos electrónicos en texto plano.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingPlainTextMessage-SendingPlainTextMessage.py" >}}
## **Envío de correo electrónico con cuerpo HTML**
Los ejemplos de programación a continuación muestran cómo puede enviar un simple mensaje de correo electrónico en HTML. La propiedad HtmlBody, una propiedad de la clase MailMessage, se utiliza para especificar el contenido HTML del cuerpo del mensaje. Para enviar un correo electrónico simple en HTML, siga estos pasos:

- Cree una instancia de la clase MailMessage.
- Especifique la dirección de correo electrónico del remitente y del receptor en la instancia de MailMessage.
- Especifique el contenido de HtmlBody.
- Cree una instancia de la clase SmtpClient y envíe el correo electrónico utilizando el método Send.

Para los propósitos de este artículo, el contenido HTML del correo electrónico es rudimentario: <html><body>Este es el cuerpo HTML</body></html> La mayoría de los correos electrónicos HTML serán más complejos. El siguiente fragmento de código le muestra cómo enviar correos electrónicos con cuerpo HTML.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SettingHTMLBody-SettingHTMLBody.py" >}}
## **Envío de correo electrónico con texto alternativo**
Los ejemplos de programación a continuación muestran cómo enviar un simple mensaje de correo electrónico en HTML con contenido alternativo. Utilice la clase AlternateView para especificar copias de un mensaje de correo electrónico en diferentes formatos. Por ejemplo, si envía un mensaje en HTML, también puede desear proporcionar una versión en texto plano para los destinatarios que utilizan lectores de correo electrónico que no pueden mostrar contenido HTML. O, si está enviando un boletín, puede querer proporcionar una copia en texto plano del texto para aquellos destinatarios que han elegido recibir una versión en texto plano. Para enviar un correo electrónico con texto alternativo, siga estos pasos:

1. Cree una instancia de la clase MailMessage.
1. Especifique las direcciones de correo electrónico del remitente y del receptor en la instancia de MailMessage.
1. Cree una instancia de la clase AlternateView.

Esto crea una vista alternativa para un mensaje de correo electrónico utilizando el contenido especificado en la cadena.

1. Agregue la instancia de la clase AlternateView al objeto MailMessage.
1. Cree una instancia de la clase SmtpClient y envíe el correo electrónico utilizando el método Send.

El siguiente fragmento de código le muestra cómo enviar correos electrónicos con texto alternativo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SetAlternateText-SetAlternateText.py" >}}
## **Envío de correos electrónicos masivos**
Enviar correos electrónicos en masa significa enviar un lote de correos electrónicos en un solo mensaje. Podemos enviar un lote de correos electrónicos utilizando el método BulkSend de la clase SmtpClient:

1. Cree una instancia de la clase SmtpClient.
1. Especifique las propiedades de la clase SmtpClient.
1. Cree una instancia de la clase MailMessage.
1. Especifique el remitente, el receptor, el asunto del correo y el mensaje en la instancia de la clase MailMessage.
1. Repita los dos pasos anteriores nuevamente, si desea enviar un correo electrónico a otra persona.
1. Cree una instancia de la clase MailMessageCollection.
1. Agregue la instancia de la clase MailMessage al objeto de la clase MailMessageCollection.
1. Ahora envíe su correo electrónico usando el método BulkSend de la clase SmtpClient pasando la instancia de la clase MailMessageCollection en él.

El siguiente fragmento de código le muestra cómo enviar correos electrónicos masivos.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingBulkEmails-SendingBulkEmails.py" >}}

## **Envío de correos electrónicos con MultiConnection**

Las siguientes propiedades de la clase [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) permiten a un cliente utilizar múltiples conexiones al servidor para enviar correos electrónicos. Esto puede ser beneficioso en escenarios donde el cliente necesita enviar un gran volumen de correos electrónicos y desea distribuir la carga de trabajo a través de múltiples conexiones.

- La propiedad 'use_multi_connection' obtiene o establece un valor que indica si el cliente debe utilizar múltiples conexiones para operaciones con carga pesada.
- La propiedad 'connections_quantity' obtiene o establece la cantidad de conexiones en modo de múltiples conexiones.
```
Tenga en cuenta que el uso de este modo no conducirá necesariamente a un aumento del rendimiento.
```
El siguiente ejemplo de código muestra cómo implementar esta característica en un proyecto:
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

## **Envío de mensajes como TNEF**
Los correos electrónicos TNEF tienen un formato especial que puede perderse si se envían utilizando la API estándar. Aspose.Email proporciona la capacidad de enviar correos electrónicos como TNEF, preservando así el formato. La propiedad UseTnef de la clase SmtpClient se puede establecer para enviar el correo electrónico como TNEF. El siguiente fragmento de código muestra cómo enviar un mensaje como TNEF.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendMsgAsTNEF-SendMsgAsTNEF.py" >}}
## **Envío de solicitudes de reuniones**
Microsoft Outlook ofrece funciones de calendario así como gestión de correos electrónicos. Cuando un usuario abre un correo electrónico con una invitación a un evento, Outlook le solicita que acepte o rechace la invitación. Aspose.Email permite a los desarrolladores agregar funciones de calendario a sus correos electrónicos.
### **Envío de solicitudes por correo electrónico**
Para enviar solicitudes de reuniones por correo electrónico, siga estos pasos:

- Cree una instancia de la clase MailMessage.
- Especifique las direcciones del remitente y del destinatario utilizando una instancia de la clase MailMessage.
- Inicialice una instancia de la clase Appointment y pásela valores.
- Especifique resumen y descripción en la instancia del Calendario.
- Agregue el Calendario a la instancia de MailMessage y pásale la instancia de Appointment.

|**Solicitud de reunión iCalendar enviada por correo electrónico**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
El siguiente fragmento de código le muestra cómo enviar solicitudes por correo electrónico.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingMeetingRequestsViaEmail-SendingMeetingRequestsViaEmail.py" >}}
### **Compatibilidad con iCalendar para IBM Lotus Notes**
La función de calendario de Aspose.Email.Mail se basa en el estándar iCalendar, un estándar para el intercambio de datos de calendario (Referencia de Sintaxis RFC 2445 o RFC2445). Por lo tanto, admite no solo Microsoft Outlook, sino también IBM Lotus Notes. Para enviar una solicitud de reunión en Lotus Notes, siga los mismos pasos mencionados anteriormente.
## **Reenviar un correo electrónico utilizando el cliente SMTP**
### **Reenviando correo electrónico con el cliente SMTP**
Reenviar un correo electrónico es una práctica común en la comunicación digital diaria. Un correo electrónico recibido puede ser reenviado a destinatarios específicos sin compartirlo con los remitentes originales. El SmtpClient de la API de Aspose.Email proporciona la capacidad de reenviar un correo electrónico a destinatarios específicos. Su método Forward se puede usar para reenviar un correo electrónico recibido o guardado a los destinatarios deseados, como se muestra en este artículo. El siguiente fragmento de código le muestra cómo reenviar un correo electrónico utilizando el cliente SMTP.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-ForwardEmail-ForwardEmail.py" >}}

### **Reenvío de correo electrónico sin usar MailMessage**

La API también admite el reenvío de mensajes EML sin primero cargarlos en [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class). Esto es útil en casos donde hay recursos limitados en términos de memoria del sistema.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient(host, smtp_port, username, password, ae.clients.SecurityOptions.AUTO)
file = open("test.eml", "rb")
client.forward(sender, recipients, file)
```