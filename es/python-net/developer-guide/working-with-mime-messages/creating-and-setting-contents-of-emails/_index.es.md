---
title: "Creación y configuración del contenido de los correos electrónicos"
url: /es/python-net/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---


## **Crear nuevo mensaje de correo electrónico**
La clase MailMessage representa un mensaje de correo electrónico y permite a los desarrolladores crear un nuevo mensaje de correo electrónico. Las propiedades básicas del correo electrónico, como De, Para, Asunto y cuerpo, se pueden adjuntar fácilmente al mensaje de correo recién creado. Del mismo modo, podemos guardar el mensaje de correo en diferentes formatos, como EML, MSG y MHTML.

- Crea una instancia de la clase MailMessage.
- Establezca las propiedades de los mensajes de correo.
- Guarda el mensaje de correo en diferentes formatos.

El siguiente fragmento de código muestra cómo crear un nuevo correo electrónico con diferentes propiedades.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-CreateNewMailMesssage-CreateNewMailMesssage.py" >}}
## **Especificación de varios destinatarios**
El MailMessage representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para crear mensajes de correo electrónico que se transmiten a un servidor SMTP mediante la clase SmtpClient. En este tema se muestra cómo especificar más de una dirección de correo electrónico. Las direcciones de correo electrónico se pueden especificar mediante la clase MailMessage. Las direcciones de correo electrónico utilizadas en la clase MailMessage son:

- **To** - Las direcciones de los destinatarios se pueden especificar en el campo «Para». Los destinatarios del campo «Para» son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario
- **Cc** - CC son las siglas de «copia exacta» o «copia de cortesía» y permiten añadir destinatarios de correo electrónico que necesitan ver el correo electrónico, pero no necesariamente se espera que actúen en consecuencia. Los gerentes, por ejemplo, o los miembros de tu equipo que necesitan estar al tanto de una conversación. Con Aspose.Email, puedes especificar las direcciones CC en tu código. De esta forma, los correos electrónicos automatizados, o todos los correos electrónicos a una dirección específica, se pueden copiar al personal correspondiente.
- **Bcc** - Bcc, copia ciega, te permite enviar un correo electrónico a un destinatario que está oculto para otros destinatarios. Si aparece un CC en la información del correo electrónico que ven los destinatarios principales, no aparece un Bcc. Está diseñado para enviar notificaciones ocultas. 

Para especificar varias direcciones de correo electrónico en un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Especifique las direcciones de origen y varias direcciones de destino, CC y Bcc mediante la instancia de MailMessage.
1. Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El ejemplo de código que aparece a continuación muestra cómo se pueden especificar varias direcciones To, CC y BCC.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SpecifyRecipientAddresses-SpecifyRecipientAddresses.py" >}}
## **Cambiar las direcciones de correo electrónico por un nombre descriptivo**
Los siguientes ejemplos de programación muestran cómo cambiar las direcciones de correo electrónico por nombres descriptivos en un mensaje de correo electrónico. Un nombre descriptivo es un nombre que es más fácil de entender para los humanos que la dirección de correo electrónico, por ejemplo, John Smith en lugar de js346@domain.com. Al enviar un correo electrónico, podemos asociar un nombre descriptivo a una dirección de correo electrónico en el constructor de la clase MailMessage.

Para cambiar las direcciones de correo electrónico por nombres descriptivos en un mensaje de correo electrónico, sigue estos pasos:

- Cree una instancia de la clase MailMessage y especifique las direcciones de correo electrónico en **To** and **From** campos junto con nombres descriptivos.
- Especifique las direcciones de correo electrónico Cc y Bcc junto con nombres descriptivos llamando al constructor de la clase MailMessage en la instancia de MailMessage.
- Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El siguiente fragmento de código muestra cómo mostrar los nombres de las direcciones de correo electrónico.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ChangeEmailAddress-ChangeEmailAddress.py" >}}
## **Establecer el cuerpo del correo**
La clase MailMessage representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para crear mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega mediante la clase SmtpClient. El cuerpo de un correo se puede especificar mediante la clase MailMessage. Un correo electrónico puede tener varios cuerpos. Hay dos tipos de cuerpos de correo en la clase MailMessage:

- Cuerpo HTML
- Cuerpo del texto

Además de HTMLBody y TextBody, Aspose.Email tiene otras dos propiedades de solo lectura relacionadas con el cuerpo del correo:

- isBodyText: indica al usuario si el cuerpo es texto.
- isBodyHtml: indica al usuario si el cuerpo es HTML o texto sin formato.

En este artículo se muestra cómo definir texto sin formato o texto principal HTML, establecer texto alternativo y codificar el cuerpo del correo electrónico.
### **Configuración del cuerpo HTML**
HtmlBody se usa para especificar el contenido HTML del cuerpo de un mensaje. HtmlBody debe estar entre <html> </html> etiquetas. El siguiente fragmento de código muestra cómo configurar el cuerpo del HTML.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SetHTMLBody-SetHTMLBody.py" >}}
### **Configuración de texto alternativo**
Utilice la clase AlternateView para especificar copias de un mensaje de correo electrónico en un formato diferente. Por ejemplo, si envía un mensaje en HTML, es posible que también desee proporcionar una versión de texto sin formato en caso de que algunos de los destinatarios utilicen lectores de correo electrónico que no puedan mostrar contenido HTML. Esta clase tiene dos propiedades, linkedResources y baseURI, que se utilizan para resolver las URL incluidas en el contenido del correo electrónico.

- LinkedResources es una colección de objetos LinkedResources. Cuando se representan, las URL del contenido del correo electrónico se comparan primero con las URL del enlace de contenido de cada objeto de LinkedResources de la colección LinkedResources y se resuelven.
- El lector de correo utiliza BaseURI para resolver las URL relativas dentro del cuerpo y también para resolver las URL de enlaces de contenido relativas de la colección LinkedResources.

El siguiente fragmento de código muestra cómo configurar texto alternativo.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AlternateText-AlternateText.py" >}}
## **Características de MailMessage**
The [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) La clase representa el contenido de un mensaje de correo electrónico. Instancias del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) la clase se usa para crear un mensaje de correo electrónico que se transmite a un servidor SMTP para su entrega mediante el [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) clase. Este artículo muestra cómo usar [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) funciones de utilidad de clase para controlar las siguientes funciones de correo electrónico:

- **Fecha y hora** - A través del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) propiedad de fecha de clase: obtenemos o establecemos la fecha y hora de un correo electrónico.
- **Prioridad de mensajes** - El [MailPriority](https://apireference.aspose.com/email/net/aspose.email/mailpriority) La clase especifica los niveles de prioridad para enviar un mensaje de correo electrónico. Puede ser bajo, normal o alto. La prioridad influye en la velocidad de transmisión y en la entrega.
- **Sensibilidad de los mensajes** - El [MailSensitivity](https://apireference.aspose.com/email/net/aspose.email/mailsensitivity) La clase especifica cinco niveles de sensibilidad.
- **Notificación de entrega** - Las notificaciones de entrega permiten a los remitentes saber que el correo electrónico que han enviado ha llegado a la bandeja de entrada del destinatario.

De forma predeterminada, la fecha es la fecha real en la que se envió el mensaje y la hora es la hora en que se envió, tal y como muestra Microsoft Outlook. Sin embargo, el tiempo real de entrega del correo electrónico lo añade el propio servidor SMTP en el encabezado del correo. Por ejemplo, a continuación se muestra un encabezado de correo común, donde Date establece el campo Date.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-DateAndTime-DateAndTime.py" >}}



El siguiente fragmento de código ilustra cómo se puede usar cada una de las funciones descritas anteriormente.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-MailMessageFeatures-MailMessageFeatures.py" >}}
## **Solicitud de un acuse de recibo de lectura**
Los ejemplos de programación que aparecen a continuación muestran cómo puede solicitar un acuse de recibo de lectura. El [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) La propiedad de enumeración describe las opciones de notificación de entrega de un correo electrónico. Para solicitar una confirmación de lectura después de enviar un correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class.
1. Especifique el remitente, el destinatario y el cuerpo HTML del correo electrónico en el [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instance.
1. Especifique el [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) en otros [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instances.
1. Crea una instancia del [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) clase y envía el correo electrónico mediante el método Send.

Es posible que las solicitudes de acuse de recibo de lectura no siempre se cumplan porque:

- Es posible que un cliente de correo no implemente esa funcionalidad.
- Es posible que el usuario final tenga desactivada esa funcionalidad.
- El usuario final puede optar por no enviar uno.

El siguiente fragmento de código muestra cómo solicitar un acuse de recibo de lectura.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-RequestReadReceipt-RequestReadReceipt.py" >}}
## **Establecer encabezados de correo electrónico**
Los encabezados de correo electrónico representan un estándar de Internet y el RFC define los campos de encabezado que se incluyen en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante la clase MailMessage. Los tipos de encabezados comunes se definen en la clase HeaderType. Es una clase sellada que funciona como una enumeración normal.

Normalmente, el encabezado de un correo electrónico contiene los siguientes campos:

- Para: Las direcciones de los destinatarios se pueden especificar en el **To** campo. El **To** los destinatarios de los campos son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
- De: este campo presenta la dirección de correo electrónico del remitente del mensaje.
- Cc: Permite a los usuarios enviar un mensaje como «copia exacta» o «copia de cortesía». Es decir, no se espera que el receptor responda o actúe. Por lo general, el personal de supervisión recibe una notificación mediante un CC.
- Bcc: Son las siglas de Blind Carbon Copy, se refiere a la práctica de enviar un mensaje a varios destinatarios de tal manera que lo que reciben no contenga la lista completa de destinatarios. Está diseñado para enviar notificaciones ocultas.
- Responder a: este campo de encabezado está destinado a indicar a dónde quiere que vayan las respuestas el remitente.
- Asunto: Título, encabezamiento, asunto. Se utiliza a menudo como indicador de hilo para los mensajes que responden o comentan otros mensajes.
- Fecha: este encabezado especifica una fecha (y una hora). Normalmente es la fecha en la que se redactó y envió el mensaje.
- XMailer: información sobre el software cliente del creador. Ejemplo: X-Mailer: Aspose.Email. Los clientes de correo utilizan XMailer. Los distintos clientes de correo tendrán diferentes valores de XMailer. El valor de XMailer de MS Outlook es Microsoft Office Outlook, versión 11.0.5510. El receptor o el lector de correo electrónico lo ignoran.

Normalmente, el encabezado de un correo electrónico tiene un aspecto similar al siguiente:

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: guangzhou@guangzhoo.com

Subject: test mail

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

```

Para personalizar el encabezado de un correo electrónico, sigue estos pasos:

- Crea una instancia del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class.
- Especifique To, From, CC, Bcc, Reply To, Subject, Date y XMailer mediante una instancia del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
- Crea una instancia del [MimeHeader](https://apireference.aspose.com/email/net/aspose.email.mime/mimeheader) clase y especifique el encabezado secreto.
- Añada el encabezado secreto a [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instance.

El siguiente fragmento de código muestra cómo configurar los encabezados de los correos electrónicos.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SetEmailHeaders-SetEmailHeaders.py" >}}



El fragmento de código anterior produce un encabezado de correo electrónico en el siguiente formato. Esto se puede observar abriendo el archivo resultante «msgHeaders.msg» en Microsoft Outlook y, a continuación, consultando las propiedades.

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: receiver1@receiver.com

CC: receiver2@receiver.com

BCC: receiver3@receiver.com

Subject: test mail

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

secret-header: mystery

```
### **Insertar encabezado en una ubicación específica**
The [Add](https://apireference.aspose.com/email/net/aspose.email.mime.headercollection/add/methods/1) método de [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection) class inserta el encabezado al final de la colección. Sin embargo, a veces puede ser necesario insertar un encabezado en una ubicación específica. En tal caso, el [Add](https://apireference.aspose.com/email/net/aspose.email.mime.headercollection/add/methods/1) el método no será de ayuda. Para lograr esto, usa el [Insert](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection/methods/insert) método del [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection). Si la colección contiene encabezados con el mismo nombre, este encabezado se insertará antes que otros encabezados con el mismo nombre. El siguiente fragmento de código muestra cómo insertar un encabezado en una ubicación específica.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-InsertHeaderAtSpecificLocation-InsertHeaderAtSpecificLocation.py" >}}
### **Agregar encabezados personalizados al correo electrónico**
Los siguientes ejemplos de programación muestran cómo especificar un encabezado personalizado en un mensaje de correo electrónico. Se puede especificar un encabezado de correo electrónico mediante el [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) clase. Para especificar un encabezado personalizado en un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class.
1. Especifique los valores de destino, origen y asunto mediante la instancia de MailMessage.
1. Añada el encabezado secreto al [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instance.
1. Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El siguiente fragmento de código muestra cómo agregar encabezados personalizados al correo electrónico.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SpecifyCustomHeader-SpecifyCustomHeader.py" >}}
