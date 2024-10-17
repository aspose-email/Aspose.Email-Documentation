---
title: "Creando y estableciendo el contenido de los correos electrónicos"
url: /es/python-net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---

## **Crear nuevo mensaje de correo electrónico**
La clase MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores crear nuevos mensajes de correo electrónico. Las propiedades básicas del correo electrónico, como De, Para, Asunto y cuerpo, se pueden adjuntar fácilmente al mensaje de correo electrónico recién creado. De manera similar, podemos guardar el mensaje de correo en diferentes formatos como EML, MSG y MHTML.

- Crear una instancia de la clase MailMessage.
- Establecer propiedades del mensaje de correo.
- Guardar el mensaje de correo en diferentes formatos.

El siguiente fragmento de código muestra cómo crear un nuevo correo electrónico con diferentes propiedades.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-CreateNewMailMesssage-CreateNewMailMesssage.py" >}}
## **Especificando múltiples destinatarios**
El MailMessage representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para construir mensajes de correo electrónico que se transmiten a un servidor SMTP utilizando la clase SmtpClient. Este tema demuestra cómo especificar más de una dirección de correo electrónico. Las direcciones de correo electrónico se pueden especificar utilizando la clase MailMessage. Las direcciones de correo electrónico utilizadas en la clase MailMessage son:

- **Para** - Las direcciones de los destinatarios se pueden especificar en el campo 'Para'. Los destinatarios del campo 'Para' son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
- **Cc** - CC significa "copia carbón" o "copia de cortesía", y permite agregar destinatarios de correo electrónico que necesitan ver el correo electrónico, pero que no se espera que actúen sobre él. Por ejemplo, gerentes o miembros de su equipo que necesitan estar al tanto de una conversación. Con Aspose.Email, las direcciones CC se pueden especificar en su código. De esta manera, los correos electrónicos automatizados o todos los correos electrónicos a una dirección específica se pueden copiar al personal relevante.
- **Bcc** - Bcc, copia carbón oculta, le permite enviar un correo electrónico a un destinatario que está oculto para otros destinatarios. Donde un CC aparece en la información del correo electrónico que ven los destinatarios principales, un Bcc no lo hace. Está destinado a la notificación oculta.

Para especificar múltiples direcciones de correo electrónico en un mensaje de correo, siga estos pasos:

1. Crear una instancia de la clase MailMessage.
1. Especificar las direcciones De y múltiples Para, Cc y Bcc utilizando la instancia MailMessage.
1. Crear una instancia de la clase SmtpClient y enviar el correo utilizando el método Send.

El siguiente fragmento de código muestra cómo se pueden especificar múltiples direcciones Para, CC y BCC.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SpecifyRecipientAddresses-SpecifyRecipientAddresses.py" >}}
## **Cambiar direcciones de correo electrónico a un nombre amigable**
Los ejemplos de programación a continuación demuestran cómo cambiar direcciones de correo electrónico a nombres amigables en un mensaje de correo electrónico. Un nombre amigable es un nombre que es más accesible para los humanos que la dirección de correo electrónico, por ejemplo, Juan Pérez en lugar de js346@domain.com. Al enviar un correo electrónico, podemos asociar un nombre amigable con una dirección de correo electrónico en el constructor de la clase MailMessage.

Para cambiar direcciones de correo electrónico a nombres amigables en un mensaje de correo, siga estos pasos:

- Crear una instancia de la clase MailMessage y especificar direcciones de correo electrónico en los campos **Para** y **De** junto con nombres amigables.
- Especificar las direcciones de correo electrónico Cc y Bcc junto con nombres amigables llamando al constructor de la clase MailMessage en la instancia MailMessage.
- Crear una instancia de la clase SmtpClient y enviar el correo utilizando el método Send.

El siguiente fragmento de código muestra cómo mostrar nombres para las direcciones de correo electrónico.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ChangeEmailAddress-ChangeEmailAddress.py" >}}
## **Establecer cuerpo del correo**
La clase MailMessage representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para construir mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega utilizando la clase SmtpClient. Se puede especificar un cuerpo de correo utilizando la clase MailMessage. Un correo electrónico puede tener múltiples cuerpos. Hay dos tipos de cuerpos de correo en la clase MailMessage:

- Cuerpo HTML
- Cuerpo de texto

Además de HtmlBody y TextBody, Aspose.Email tiene otras dos propiedades de solo lectura relacionadas con el cuerpo del correo:

- IsBodyText: le dice al usuario si el cuerpo es texto.
- IsBodyHtml: le dice al usuario si el cuerpo es HTML o texto plano.

Este artículo muestra cómo definir texto de cuerpo en texto plano o HTML, establecer texto alternativo y codificar el cuerpo del correo.
### **Estableciendo el cuerpo HTML**
HtmlBody se utiliza para especificar el contenido HTML de un cuerpo de mensaje. HtmlBody debe estar encerrado entre etiquetas <html> </html>. El siguiente fragmento de código muestra cómo establecer el cuerpo HTML.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SetHTMLBody-SetHTMLBody.py" >}}
### **Estableciendo texto alternativo**
Utilice la clase AlternateView para especificar copias de un mensaje de correo electrónico en diferente formato. Por ejemplo, si envía un mensaje en HTML, también podría querer proporcionar una versión en texto plano en caso de que algunos de los destinatarios utilicen lectores de correo electrónico que no pueden mostrar contenido HTML. Esta clase tiene dos propiedades, LinkedResources y BaseUri, que se utilizan para resolver URLs dentro del contenido del correo electrónico.

- LinkedResources es una colección de objetos LinkedResources. Cuando se renderiza, las URLs dentro del contenido del correo electrónico se comparan primero con las URLs en el Enlace de Contenido de cada objeto LinkedResources en la colección LinkedResources y se resuelven.
- BaseUri es utilizado por el lector de correo para resolver URLs relativas dentro del cuerpo, y también para resolver URLs relativas de Enlace de Contenido, en la colección LinkedResources.

El siguiente fragmento de código muestra cómo establecer texto alternativo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AlternateText-AlternateText.py" >}}
## **Características de MailMessage**
La clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) representa el contenido de un mensaje de correo electrónico. Las instancias de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) se utilizan para construir un mensaje de correo electrónico que se transmite a un servidor SMTP para su entrega utilizando la clase [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient). Este artículo muestra cómo utilizar las características de utilidad de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) para controlar las siguientes características del correo electrónico:

- **Fecha y hora** - A través de la propiedad Date de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) obtenemos o establecemos la fecha y hora de un correo electrónico.
- **Prioridad del mensaje** - La clase [MailPriority](https://apireference.aspose.com/email/net/aspose.email/mailpriority) especifica niveles de prioridad para el envío de un mensaje de correo electrónico. Puede ser baja, normal o alta. La prioridad influye en la velocidad de transmisión y entrega.
- **Sensibilidad del mensaje** - La clase [MailSensitivity](https://apireference.aspose.com/email/net/aspose.email/mailsensitivity) especifica cinco niveles de sensibilidad.
- **Notificación de entrega** - Las notificaciones de entrega permiten a los remitentes saber que el correo electrónico que enviaron ha sido entregado a la bandeja de entrada del destinatario.

Por defecto, la fecha es la fecha real en que se envió el mensaje, y la hora es el momento en que se envió, tal como lo muestra Microsoft Outlook. Sin embargo, el tiempo real de entrega del correo es agregado por el servidor SMTP en el encabezado del correo. Por ejemplo, a continuación se muestra un encabezado de correo común, donde Date establece el campo Date.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-DateAndTime-DateAndTime.py" >}}

El siguiente fragmento de código ilustra cómo se puede utilizar cada una de las características mencionadas anteriormente.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-MailMessageFeatures-MailMessageFeatures.py" >}}
## **Solicitando un acuse de recibo**
Los ejemplos de programación a continuación muestran cómo puede solicitar un acuse de recibo. La propiedad [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) describe las opciones de notificación de entrega para un correo electrónico. Para solicitar un acuse de recibo después de enviar un correo electrónico, siga estos pasos:

1. Crear una instancia de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Especificar el remitente, el receptor y el cuerpo HTML para el correo en la instancia [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Especificar los [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) en otras instancias [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Crear una instancia de la clase [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) y enviar el correo utilizando el método Send.

Las solicitudes de acuse de recibo pueden no ser siempre atendidas porque:

- Un cliente de correo puede no implementar esa funcionalidad.
- El usuario final puede tener desactivada esa funcionalidad.
- El usuario final puede optar por no enviar uno.

El siguiente fragmento de código muestra cómo solicitar un acuse de recibo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-RequestReadReceipt-RequestReadReceipt.py" >}}
## **Establecer encabezados de correo electrónico**
Los encabezados de correo electrónico representan un estándar de Internet y la RFC define los campos de encabezado que se incluyen en los mensajes de correo electrónico de Internet. Un encabezado de correo electrónico se puede especificar utilizando la clase MailMessage. Los tipos de encabezados comunes se definen en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal.

Normalmente un encabezado de correo electrónico contiene estos campos:

- Para: Las direcciones de los destinatarios se pueden especificar en el campo **Para**. Los destinatarios del campo **Para** son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
- De: Este campo presenta la dirección de correo electrónico del remitente del mensaje.
- Cc: Permite a los usuarios enviar un mensaje como "Copia Carbón" o "Copia de Cortesía". Es decir, se espera que el receptor no responda ni actúe. Típicamente, el personal de supervisión es notificado con CC.
- Bcc: Significa Copia Carbón Oculta, se refiere a la práctica de enviar un mensaje a múltiples destinatarios de manera que lo que reciben no contenga la lista completa de destinatarios. Está destinado a la notificación oculta.
- Responder a: Este campo de encabezado está destinado a indicar a dónde el remitente quiere que vayan las respuestas.
- Asunto: Título, encabezamiento, asunto. A menudo se utiliza como indicador de hilo para mensajes que responden o comentan sobre otros mensajes.
- Fecha: Este encabezado especifica una fecha (y hora). Normalmente esta es la fecha en la que se compuso y envió el mensaje.
- XMailer: Información sobre el software cliente del originador. Ejemplo: X-Mailer: Aspose.Email. XMailer es utilizado por clientes de correo. Diferentes clientes de correo tendrán diferentes valores de XMailer. El valor de XMailer de MS Outlook es Microsoft Office Outlook, Build 11.0.5510. Es ignorado por el receptor de correo o el lector de correo.

Normalmente, un encabezado de correo electrónico se ve algo así:

``` cs
 Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: correo de prueba
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

Para personalizar un encabezado de correo electrónico, siga estos pasos:

- Crear una instancia de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
- Especificar Para, De, CC, Bcc, Responder a, Asunto, Fecha y XMailer utilizando una instancia de la [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
- Crear una instancia de la clase [MimeHeader](https://apireference.aspose.com/email/net/aspose.email.mime/mimeheader) y especificar un encabezado secreto.
- Agregar el encabezado secreto a la instancia [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).

El siguiente fragmento de código muestra cómo establecer encabezados de correo electrónico.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SetEmailHeaders-SetEmailHeaders.py" >}}

El fragmento de código anterior produce un encabezado de correo electrónico en el siguiente formato. Esto se puede observar al abrir el archivo resultante "MsgHeaders.msg" en Microsoft Outlook y luego ver las Propiedades.

``` cs
 Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: correo de prueba
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
secret-header: mystery
```
### **Insertar encabezado en una ubicación específica**
El método [Add](https://apireference.aspose.com/email/net/aspose.email.mime.headercollection/add/methods/1) de la clase [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection) inserta el encabezado al final de la colección. Sin embargo, a veces puede ser necesario insertar un encabezado en una ubicación específica. En tal caso, el método [Add](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection/add/methods/1) no será de ayuda. Para lograr esto, use el método [Insert](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection/methods/insert) de la clase [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection). Si la colección contiene encabezados con el mismo nombre, este encabezado se insertará antes de otros encabezados con el mismo nombre. El siguiente fragmento de código muestra cómo insertar un encabezado en una ubicación específica.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-InsertHeaderAtSpecificLocation-InsertHeaderAtSpecificLocation.py" >}}
### **Agregar encabezados personalizados al correo**
Los ejemplos de programación a continuación demuestran cómo especificar un encabezado personalizado en un mensaje de correo electrónico. Un encabezado de correo electrónico se puede especificar utilizando la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage). Para especificar un encabezado personalizado en un mensaje de correo electrónico, siga estos pasos:

1. Crear una instancia de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Especificar los valores de para, de y asunto usando la instancia MailMessage.
1. Agregar el encabezado secreto a la instancia [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
1. Crear una instancia de la clase SmtpClient y enviar el correo utilizando el método Send.

El siguiente fragmento de código muestra cómo agregar encabezados personalizados al correo.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SpecifyCustomHeader-SpecifyCustomHeader.py" >}}