---
title: "Creación y configuración del contenido de los correos electrónicos"
url: /es/java/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---

## **Crear nuevo mensaje de correo electrónico**

Aspose.Email para Java permite a los desarrolladores crear mensajes MIME (extensiones de correo de Internet multipropósito) desde cero. La clase principal para este propósito en la API Aspose.Email para Java es la [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase.
En este tema se explican los pasos necesarios para crear mensajes de correo electrónico en formatos de archivo EML, MSG y MTH con Aspose.Email para Java.

Para crear un mensaje de correo electrónico desde cero:

1. Crea una instancia de la clase MailMessage.
2. Establezca el asunto del mensaje mediante el [setSubject()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setSubject-java.lang.String-) method.
3. Configure el cuerpo del mensaje mediante el [setHtmlBody()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) method.
4. Configure el remitente del correo electrónico mediante el [setFrom()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setFrom-com.aspose.email.MailAddress-) method.
5. Defina el destinatario en **TO** campo mediante el uso del [getTo().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) method.
6. Defina el destinatario en **CC** campo mediante el uso del [getCC().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) method.
7. Llame al [Save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.io.OutputStream-) método para guardar el archivo del mensaje en un disco en formatos MSG, EML y MHT.
 
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-CreateNewEmail-.java" >}}

## **Especificación de varios destinatarios**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para crear mensajes de correo electrónico que se transmiten a un servidor SMTP mediante el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase. En este tema se muestra cómo especificar más de una dirección de correo electrónico. Las direcciones de correo electrónico se pueden especificar mediante la clase MailMessage. Las direcciones de correo electrónico utilizadas en la clase MailMessage son:

- **To** - Las direcciones de los destinatarios se pueden especificar en el campo «Para». Los destinatarios del campo «Para» son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario
- **Cc** - CC son las siglas de «copia exacta» o «copia de cortesía» y permiten añadir destinatarios de correo electrónico que necesitan ver el correo electrónico, pero no necesariamente se espera que actúen en consecuencia. Los gerentes, por ejemplo, o los miembros de tu equipo que necesitan estar al tanto de una conversación. Con Aspose.Email, puedes especificar las direcciones CC en tu código. De esta forma, los correos electrónicos automatizados, o todos los correos electrónicos a una dirección específica, se pueden copiar al personal correspondiente.
- **Bcc** - Bcc, copia ciega, te permite enviar un correo electrónico a un destinatario que está oculto para otros destinatarios. Si aparece un CC en la información del correo electrónico que ven los destinatarios principales, no aparece un Bcc. Está diseñado para enviar notificaciones ocultas. 

Para especificar varias direcciones de correo electrónico en un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
2. Especifique las direcciones de origen y varias direcciones de destino, CC y Bcc mediante la instancia de MailMessage.
3. Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El ejemplo de código que aparece a continuación muestra cómo se pueden especificar varias direcciones To, CC y BCC.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyRecipientAddresses-SpecifyRecipientAddresses.java" >}}

## **Cambiar las direcciones de correo electrónico por un nombre descriptivo**

Los siguientes ejemplos de programación muestran cómo cambiar las direcciones de correo electrónico por nombres descriptivos en un mensaje de correo electrónico. Un nombre descriptivo es un nombre que es más fácil de entender para los humanos que la dirección de correo electrónico, por ejemplo, John Smith en lugar de js346@domain.com. Al enviar un correo electrónico, podemos asociar un nombre descriptivo a una dirección de correo electrónico en el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) constructor de clases.

Para cambiar las direcciones de correo electrónico por nombres descriptivos en un mensaje de correo electrónico, sigue estos pasos:

- Cree una instancia de la clase MailMessage y especifique las direcciones de correo electrónico en **To** and **From** campos junto con nombres descriptivos.
- Especifique las direcciones de correo electrónico Cc y Bcc junto con nombres descriptivos llamando al constructor de la clase MailMessage en la instancia de MailMessage.
- Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El siguiente fragmento de código muestra cómo mostrar los nombres de las direcciones de correo electrónico.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ChangeEmailAddress-ChangeEmailAddress.java" >}}

## **Establecer el cuerpo del correo**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) la clase representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para crear mensajes de correo electrónico que se transmiten a un servidor SMTP para su entrega mediante el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase. El cuerpo de un correo se puede especificar mediante la clase MailMessage. El cuerpo de un correo electrónico se puede especificar mediante [setHtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) método en MailMessage.

Además de [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), Aspose.Email tiene otro método relacionado con el cuerpo del correo:

- [isBodyHtml](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isBodyHtml--): indica al usuario si el cuerpo es HTML o texto sin formato.

En este tema se muestra cómo definir el cuerpo del texto HTML y establecer texto alternativo.

### **Configuración del cuerpo HTML**

[HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) se usa para especificar el contenido HTML del cuerpo de un mensaje. HTMLBody debe estar entre <html> </html> etiquetas. El siguiente fragmento de código muestra cómo configurar el cuerpo del HTML.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetHTMLBody-SetHTMLBody.java" >}}

### **Configuración de texto alternativo**

Usa el [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) clase para especificar copias de un mensaje de correo electrónico en un formato diferente. Por ejemplo, si envía un mensaje en HTML, es posible que también desee proporcionar una versión de texto sin formato en caso de que algunos de los destinatarios utilicen lectores de correo electrónico que no puedan mostrar contenido HTML. Esta clase tiene dos propiedades: [LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getLinkedResources--) and [BaseUri](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getBaseUri--), que se utilizan para resolver las URL incluidas en el contenido del correo electrónico.

- LinkedResources es una colección de objetos LinkedResources. Cuando se representan, las URL del contenido del correo electrónico se comparan primero con las URL del enlace de contenido de cada objeto de LinkedResources de la colección LinkedResources y se resuelven.
- El lector de correo utiliza BaseURI para resolver las URL relativas dentro del cuerpo y también para resolver las URL de enlaces de contenido relativas de la colección LinkedResources.

El siguiente fragmento de código muestra cómo configurar texto alternativo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetAlternateText-SetAlternateText.java" >}}

## **Especificación de la codificación del cuerpo del correo**

El tipo de contenido define el formato del contenido del correo electrónico: el conjunto de caracteres. Por ejemplo, algunos conjuntos de caracteres comunes que se proporcionan en java.nio.Charset son:

- US-ASCII: ASCII de siete bits, también conocido como ISO646-US, también conocido como el bloque latino básico del conjunto de caracteres Unicode
- ISO-8859-1 - Alfabeto latino ISO n.º 1, también conocido como ISO-LATIN-1
- UTF-8: formato de transformación UCS de ocho bits
- UTF-16BE: formato de transformación UCS de dieciséis bits, orden de bytes de gran endiano
- UTF-16LE: formato de transformación UCS de dieciséis bits, orden de bytes mendiano
- UTF-16: formato de transformación UCS de dieciséis bits, orden de bytes identificado mediante una marca de orden de bytes opcional

Aspose.Email usa el [BodyEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBodyEncoding--) propiedad de la clase MailMessage para especificar la codificación del cuerpo del correo electrónico. Para codificar el cuerpo de un mensaje de correo electrónico, siga los pasos que se indican a continuación:

1. Crea una instancia de la clase MailMessage.
1. Especifique el remitente, el destinatario y el cuerpo del correo electrónico HTML en la instancia de MailMessage.
1. Especifique el valor de la propiedad BodyEncoding.
1. Crea una instancia del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y envía el correo electrónico mediante el método Send.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyMailBodyEncoding-SpecifyMailBodyEncoding.java" >}}

## **Características de MailMessage**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) La clase representa el contenido de un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para crear un mensaje de correo electrónico que se transmite a un servidor SMTP para su entrega mediante el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase. En este artículo se muestra cómo utilizar las funciones de la utilidad de la clase MailMessage para controlar las siguientes funciones del correo electrónico:

- **Fecha y hora** - A través de la clase MailMessage [setDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setDate-java.util.Date-) método en el que configuramos la fecha y la hora de un correo electrónico.
- **Prioridad de mensajes** - El [MailPriority](https://reference.aspose.com/email/java/com.aspose.email/mailpriority/) La clase especifica los niveles de prioridad para enviar un mensaje de correo electrónico. Puede ser bajo, normal o alto. La prioridad influye en la velocidad de transmisión y en la entrega.
- **Sensibilidad de los mensajes** - El [MailSensitivity](https://reference.aspose.com/email/java/com.aspose.email/mailsensitivity/) La clase especifica cinco niveles de sensibilidad.
- **Notificación de entrega** - Las notificaciones de entrega permiten a los remitentes saber que el correo electrónico que han enviado ha llegado a la bandeja de entrada del destinatario.

De forma predeterminada, la fecha es la fecha real en la que se envió el mensaje y la hora es la hora en que se envió, tal y como muestra Microsoft Outlook. Sin embargo, el tiempo real de entrega del correo electrónico lo añade el propio servidor SMTP en el encabezado del correo. Por ejemplo, a continuación se muestra un encabezado de correo común, en el que el campo Fecha se estableció mediante MailMessage.setDate.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-DateAndTime-DateAndTime.cs" >}}

El siguiente fragmento de código ilustra cómo se puede usar cada una de las funciones descritas anteriormente.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-UseMailMessageFeatures-MailMessageFeatures.java" >}}

## **Solicitud de un acuse de recibo de lectura**

Los ejemplos de programación que aparecen a continuación muestran cómo puede solicitar un acuse de recibo de lectura. La clase MailMessage [DeliveryNotificationOptions](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDeliveryNotificationOptions--) La propiedad de enumeración describe la [opciones de notificación de entrega](https://reference.aspose.com/email/java/com.aspose.email/deliverynotificationoptions/) para un correo electrónico. Para solicitar un acuse de recibo de lectura después de enviar un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Especifique el remitente, el destinatario y el cuerpo HTML del correo electrónico en la instancia de MailMessage.
1. Especifique las opciones de notificación de entrega en otras instancias de MailMessage.
2. Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

Es posible que las solicitudes de acuse de recibo de lectura no siempre se cumplan porque:

- Es posible que un cliente de correo no implemente esa funcionalidad.
- Es posible que el usuario final tenga desactivada esa funcionalidad.
- El usuario final puede optar por no enviar uno.

El siguiente fragmento de código muestra cómo solicitar un acuse de recibo de lectura.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-RequestReadReceipt-RequestReadReceipt.java" >}}

## **Establecer encabezados de correo electrónico**

Los encabezados de correo electrónico representan un estándar de Internet y el RFC define los campos de encabezado que se incluyen en los mensajes de correo electrónico de Internet. Se puede especificar un encabezado de correo electrónico mediante el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase. Los tipos de encabezados más comunes se definen en [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/) clase. Es una clase sellada que funciona como una enumeración normal.

Normalmente, el encabezado de un correo electrónico contiene los siguientes campos:

- Para: Las direcciones de los destinatarios se pueden especificar en el **To** campo. El **To** los destinatarios de los campos son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
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

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Especifique To, From, CC, Bcc, ReplyTo, Subject, Date y XMailer mediante una instancia de la clase MailMessage.
- Crea una instancia del [MimeHeader](https://reference.aspose.com/email/java/com.aspose.email/mimeheader/) clase y especifique el encabezado secreto.
- Añade el encabezado secreto a la instancia de MailMessage.

En el código que se muestra a continuación, hemos personalizado un encabezado de correo electrónico.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-SetEmailHeaders.java" >}}

El fragmento de código anterior produce un encabezado de correo electrónico en el siguiente formato. Esto se puede observar abriendo el archivo msgHeaders.msg en Microsoft Outlook y, a continuación, viendo sus propiedades.

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

The [Add](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#add-com.aspose.email.HeaderCollection-) El método de HeadersCollection inserta el encabezado al final de la colección. Sin embargo, a veces puede ser necesario insertar un encabezado en una ubicación específica. En tal caso, el método Add no será de ayuda. Para lograr esto, usa el [Insert](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#insert-java.lang.String-java.lang.String-) método de HeadersCollection. Si la colección contiene encabezados con el mismo nombre, este encabezado se insertará antes que otros encabezados con el mismo nombre. A continuación se muestra la firma del método Insert y el código de ejemplo para su uso.

``` java

 Method Signature

HeaderCollection.insert(String name, String value)

```

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-InsertHeaderAtSpecificLocation.java" >}}

### **Agregar encabezados personalizados al correo electrónico**

Los siguientes ejemplos de programación muestran cómo especificar un encabezado personalizado en un mensaje de correo electrónico. Se puede especificar un encabezado de correo electrónico mediante la clase MailMessage. Para especificar un encabezado personalizado en un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Especifique los valores de destino, origen y asunto mediante la instancia de MailMessage.
1. Añade el encabezado secreto a la instancia de MailMessage.
1. Cree una instancia de la clase SmtpClient y envíe el correo electrónico mediante el método Send.

El siguiente fragmento de código muestra cómo agregar encabezados personalizados al correo electrónico.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyCustomHeader-SpecifyCustomHeader.java" >}}

## **Firma correos electrónicos con DKIM**

Aspose.Email permite firmar correos electrónicos con DKIM (DomainKeys Identified Mail). Esto permite a una organización asumir la responsabilidad de un mensaje que está en tránsito ([acerca de DKIM](https://www.dkim.org/)). DKIM añade una firma digital a los encabezados de los mensajes de correo electrónico que los destinatarios pueden validar. La clave pública del remitente permite al receptor verificar que la firma coincide con el contenido del mensaje. La clase MailMessage [dKIMSign](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#dKIMSign-com.aspose.ms.System.Security.Cryptography.RSACryptoServiceProvider-com.aspose.email.DKIMSignatureInfo-) El método se utiliza para establecer la información criptográfica y de firma para firmar el mensaje. El siguiente fragmento de código muestra cómo firmar correos electrónicos con DKIM.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SignEmailsWithDKIM-SignEmailsWithDKIM.java" >}}

## **Realizar una combinación de correspondencia**

Las combinaciones de correspondencia le ayudan a crear y enviar un lote de mensajes de correo electrónico similares. El núcleo de los correos electrónicos es el mismo, pero el contenido se puede personalizar. Por lo general, los datos de contacto del destinatario (nombre, segundo nombre, empresa, etc.) se utilizan para personalizar el correo electrónico.

|![todo:image_alt_text](https://i.imgur.com/D7WSp90.png)|
|: - |
|**Figura: Ilustración de cómo funciona una combinación de correspondencia**|

Para realizar una combinación de correspondencia con Aspose.Email, siga estos pasos:

1. Crear una función con firma de nombre
1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Especifique el remitente, el destinatario, el asunto y el cuerpo.
1. Crea una firma para el final del correo electrónico.
1. Crea una instancia del [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) clase y apruebalo el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Firme en el [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) instance.
1. Crea una instancia del [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) class.
1. Agregue las columnas Receipt, FirstName y LastName como fuentes de datos en la clase DataTable
1. Crea una instancia del [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) class
1. Especifique la dirección de recepción, el nombre y los apellidos en el objeto DataRow
1. Crea una instancia del [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) class
1. Especifique el [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) e instancias de DataTable en [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) instance.
2. Crea una instancia del [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase y especifique el servidor, el puerto, el nombre de usuario y la contraseña
3. Envía correos electrónicos mediante el [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) método class bulkSendAsync

El siguiente código envía un correo electrónico a una persona de otras tres personas.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-PerformMailMerge-.java" >}}
