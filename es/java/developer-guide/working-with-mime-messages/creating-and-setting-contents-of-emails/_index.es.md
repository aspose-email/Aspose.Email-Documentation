---
title: "Creación y Configuración del Contenido de Correos Electrónicos"
url: /es/java/creating-and-setting-contents-of-emails/
weight: 10
type: docs
---

## **Crear Nuevo Mensaje de Correo Electrónico**

Aspose.Email para Java permite a los desarrolladores crear mensajes MIME (Extensiones de Correo de Internet Multipropósito) desde cero. La clase principal para este propósito en la API de Aspose.Email para Java es la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
Este tema explica los pasos necesarios para crear mensajes de correo electrónico en formatos de archivo EML, MSG y MTH utilizando Aspose.Email para Java.

Para crear un mensaje de correo electrónico desde cero:

1. Crea una instancia de la clase MailMessage.
2. Establece el asunto del mensaje usando el método [setSubject()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setSubject-java.lang.String-) .
3. Establece el cuerpo del mensaje usando el método [setHtmlBody()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) .
4. Establece el remitente del correo electrónico usando el método [setFrom()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setFrom-com.aspose.email.MailAddress-) .
5. Establece el destinatario en el campo **TO** utilizando el método [getTo().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) .
6. Establece el destinatario en el campo **CC** utilizando el método [getCC().add()](https://reference.aspose.com/email/java/com.aspose.email/mailaddresscollection/#add-java.lang.String-) .
7. Llama al método [Save()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.io.OutputStream-) para guardar el archivo del mensaje en un disco en formatos MSG, EML y MHT.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-CreateNewEmail-.java" >}}

## **Especificando Múltiples Destinatarios**

La [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para construir mensajes de correo electrónico que se transmiten a un servidor SMTP usando la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Este tema demuestra cómo especificar más de una dirección de correo electrónico. Las direcciones de correo electrónico se pueden especificar utilizando la clase MailMessage. Las direcciones de correo electrónico utilizadas en la clase MailMessage son:

- **To** - Las direcciones de destinatarios se pueden especificar en el campo 'To'. Los destinatarios del campo 'To' son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
- **Cc** - CC significa "copia de carbón", o "copia de cortesía", y te permite agregar destinatarios de correo electrónico que necesitan ver el correo electrónico, pero no se espera necesariamente que actúen al respecto. Gerentes, por ejemplo, o miembros de tu equipo que deben estar al tanto de una conversación. Con Aspose.Email, las direcciones CC se pueden especificar en tu código. De esta manera, los correos electrónicos automatizados o todos los correos electrónicos a una dirección específica se pueden copiar al personal relevante.
- **Bcc** - Bcc, copia de carbón oculta, te permite enviar un correo electrónico a un destinatario que está oculto de otros destinatarios. Mientras que un CC aparece en la información del correo electrónico que ven los destinatarios principales, un Bcc no. Está destinado a notificaciones ocultas.

Para especificar múltiples direcciones de correo electrónico en un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
2. Especifica el From y múltiples direcciones To, Cc y Bcc utilizando la instancia de MailMessage.
3. Crea una instancia de la clase SmtpClient y envía el correo electrónico utilizando el método Send.

El siguiente ejemplo de código muestra cómo se pueden especificar múltiples direcciones To, CC y BCC.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyRecipientAddresses-SpecifyRecipientAddresses.java" >}}

## **Cambio de direcciones de correo electrónico a un nombre amigable**

Los ejemplos de programación a continuación demuestran cómo cambiar direcciones de correo electrónico a nombres amigables en un mensaje de correo electrónico. Un nombre amigable es un nombre que es más amigable para los humanos que la dirección de correo electrónico, por ejemplo, John Smith en lugar de js346@domain.com. Al enviar un correo electrónico, podemos asociar un nombre amigable con una dirección de correo electrónico en el constructor de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

Para cambiar direcciones de correo electrónico a nombres amigables en un mensaje de correo electrónico, sigue estos pasos:

- Crea una instancia de la clase MailMessage y especifica direcciones de correo electrónico en los campos **To** y **From** junto con nombres amigables.
- Especifica las direcciones de correo electrónico Cc y Bcc junto con nombres amigables llamando al constructor de la clase MailMessage en la instancia de MailMessage.
- Crea una instancia de la clase SmtpClient y envía el correo electrónico utilizando el método Send.

El siguiente fragmento de código te muestra cómo mostrar nombres para direcciones de correo electrónico.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ChangeEmailAddress-ChangeEmailAddress.java" >}}

## **Establecer Cuerpo del Correo**

La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) representa un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para construir mensajes de correo electrónico que se transmiten a un servidor SMTP para entrega utilizando la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Se puede especificar un cuerpo de correo utilizando la clase MailMessage. Un cuerpo de correo puede ser especificado utilizando el método [setHtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-) en MailMessage.

Además de [HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--), Aspose.Email tiene otro método relacionado con el cuerpo del correo:

- [isBodyHtml](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isBodyHtml--): indica al usuario si el cuerpo es HTML o texto sin formato.

Este tema muestra cómo definir texto del cuerpo HTML y establecer texto alternativo.

### **Estableciendo Cuerpo HTML**

[HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBody--) se utiliza para especificar el contenido HTML de un cuerpo de mensaje. HtmlBody debe estar encerrado entre etiquetas <html> </html>. El siguiente fragmento de código te muestra cómo establecer el cuerpo HTML.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetHTMLBody-SetHTMLBody.java" >}}

### **Estableciendo Texto Alternativo**

Utiliza la clase [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) para especificar copias de un mensaje de correo electrónico en diferentes formatos. Por ejemplo, si envías un mensaje en HTML, también podrías querer proporcionar una versión en texto sin formato en caso de que algunos de los destinatarios usen lectores de correo electrónico que no puedan mostrar contenido HTML. Esta clase tiene dos propiedades, [LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getLinkedResources--) y [BaseUri](https://reference.aspose.com/email/java/com.aspose.email/alternateview/#getBaseUri--), que se utilizan para resolver URLs dentro del contenido del correo.

- LinkedResources es una colección de objetos LinkedResources. Cuando se renderiza, las URLs dentro del contenido del correo se comparan primero con las URLs en el Enlace de Contenido de cada objeto LinkedResources en la colección LinkedResources y se resuelven.
- BaseUri es utilizado por el lector de correo para resolver URLs relativas dentro del cuerpo, y también para resolver URLs de Enlace de Contenido relativas, en la colección LinkedResources.

El siguiente fragmento de código muestra cómo establecer texto alternativo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SetAlternateText-SetAlternateText.java" >}}

## **Especificando la Codificación del Cuerpo del Correo**

El tipo de contenido define el formato de contenido del correo electrónico: el conjunto de caracteres. Por ejemplo, algunos conjuntos de caracteres comunes proporcionados en java.nio.Charset son:

- US-ASCII - ASCII de siete bits, también conocido como ISO646-US, también conocido como el bloque Latino Básico del conjunto de caracteres Unicode
- ISO-8859-1 - ISO Latin Alphabet No. 1, también conocido como ISO-LATIN-1
- UTF-8 - Formato de Transformación de UCS de ocho bits
- UTF-16BE - Formato de Transformación de UCS de dieciséis bits, orden de bytes big-endian
- UTF-16LE - Formato de Transformación de UCS de dieciséis bits, orden de bytes little-endian
- UTF-16 - Formato de Transformación de UCS de dieciséis bits, orden de bytes identificado por una marca de orden de bytes opcional

Aspose.Email utiliza la propiedad [BodyEncoding](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getBodyEncoding--) de la clase MailMessage para especificar la codificación del cuerpo del correo. Para codificar el cuerpo de un mensaje de correo electrónico, sigue los pasos dados a continuación:

1. Crea una instancia de la clase MailMessage.
2. Especifica el remitente, receptor y cuerpo HTML en la instancia de MailMessage.
3. Especifica el valor de la propiedad BodyEncoding.
4. Crea una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y envía el correo electrónico utilizando el método Send.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyMailBodyEncoding-SpecifyMailBodyEncoding.java" >}}

## **Características de MailMessage**

La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) representa el contenido de un mensaje de correo electrónico. Las instancias de la clase MailMessage se utilizan para construir un mensaje de correo electrónico que se transmite a un servidor SMTP para su entrega utilizando la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Este artículo muestra cómo utilizar las características utilitarias de la clase MailMessage para controlar las siguientes características del correo electrónico:

- **Fecha y hora** - A través del método [setDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setDate-java.util.Date-) de la clase MailMessage establecemos la fecha y la hora de un correo electrónico.
- **Prioridad del mensaje** - La clase [MailPriority](https://reference.aspose.com/email/java/com.aspose.email/mailpriority/) especifica niveles de prioridad para el envío de un mensaje de correo electrónico. Puede ser baja, normal o alta. La prioridad influye en la velocidad de transmisión y entrega.
- **Sensibilidad del mensaje** - La clase [MailSensitivity](https://reference.aspose.com/email/java/com.aspose.email/mailsensitivity/) especifica cinco niveles de sensibilidad.
- **Notificación de entrega** - Las notificaciones de entrega permiten a los remitentes saber que el correo electrónico que enviaron ha sido entregado en la bandeja de entrada del destinatario.

Por defecto, la fecha es la fecha real en que se envió el mensaje, y la hora es la hora en que se envió, como la muestra Microsoft Outlook. Sin embargo, el tiempo real de entrega del correo es añadido por el servidor SMTP en el encabezado del correo. Por ejemplo, a continuación se muestra un encabezado de correo común, donde el campo Fecha fue establecido usando MailMessage.setDate.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-DateAndTime-DateAndTime.cs" >}}

El siguiente fragmento de código ilustra cómo se puede utilizar cada una de las características discutidas anteriormente.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-UseMailMessageFeatures-MailMessageFeatures.java" >}}

## **Solicitando una Confirmación de Lectura**

Los ejemplos de programación a continuación muestran cómo puedes solicitar una confirmación de lectura. La propiedad de enumeración [DeliveryNotificationOptions](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDeliveryNotificationOptions--) de la clase MailMessage describe las [opciones de notificación de entrega](https://reference.aspose.com/email/java/com.aspose.email/deliverynotificationoptions/) para un correo electrónico. Para solicitar una confirmación de lectura después de enviar un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
2. Especifica el remitente, receptor y cuerpo HTML para el correo electrónico en la instancia de MailMessage.
3. Especifica las DeliveryNotificationOptions en otras instancias de MailMessage.
4. Crea una instancia de la clase SmtpClient y envía el correo electrónico utilizando el método Send.

Las solicitudes de confirmación de lectura pueden no ser siempre honradas debido a:

- Un cliente de correo puede no implementar esa funcionalidad.
- El usuario final puede tener esa funcionalidad desactivada.
- El usuario final puede elegir no enviar una.

El siguiente fragmento de código te muestra cómo solicitar una confirmación de lectura.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-RequestReadReceipt-RequestReadReceipt.java" >}}

## **Establecer Encabezados del Correo Electrónico**

Los encabezados de correo electrónico representan un estándar de Internet y el RFC define los campos de encabezado que se incluyen en los mensajes de correo electrónico de Internet. Un encabezado de correo electrónico puede especificarse utilizando la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Los tipos de encabezados comunes se definen en la clase [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/). Es una clase sellada que funciona como una enumeración normal.

Normalmente, un encabezado de correo electrónico contiene estos campos:

- To: Las direcciones de destinatarios se pueden especificar en el campo **To**. Los destinatarios del campo **To** son la audiencia principal del mensaje. Puede haber más de una dirección de destinatario.
- From: Este campo presenta la dirección de correo electrónico del remitente del mensaje.
- Cc: Permite a los usuarios enviar un mensaje como "Copia de Carbón" o "Copia de Cortesía". Es decir, no se espera que el receptor responda o actúe. Normalmente, el personal de supervisión es notificado con CC.
- Bcc: Se refiere a la práctica de enviar un mensaje a múltiples destinatarios de tal manera que lo que reciben no contiene la lista completa de destinatarios. Está destinado a notificaciones ocultas.
- ReplyTo: Este campo de encabezado está destinado a indicar dónde quiere el remitente que se envíen las respuestas.
- Subject: Título, encabezado, asunto. A menudo se utiliza como indicador de hilo para mensajes que responden o comentan sobre otros mensajes.
- Date: Este encabezado especifica una fecha (y hora). Normalmente esta es la fecha en la que se compuso y envió el mensaje.
- XMailer: Información sobre el software cliente del originador. Ejemplo: X-Mailer: Aspose.Email. XMailer es utilizado por clientes de correo. Diferentes clientes de correo tendrán diferentes valores de XMailer. El valor de XMailer de MS Outlook es Microsoft Office Outlook, Build 11.0.5510. Es ignorado por el receptor del correo electrónico o el lector de correo electrónico.

Normalmente, un encabezado de correo electrónico se ve algo así:

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: guangzhou@guangzhoo.com

Subject: correo de prueba

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

```

Para personalizar un encabezado de correo electrónico, sigue estos pasos:

- Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Especifica To, From, CC, Bcc, ReplyTo, Subject, Date y XMailer usando una instancia de la clase MailMessage.
- Crea una instancia de la clase [MimeHeader](https://reference.aspose.com/email/java/com.aspose.email/mimeheader/) y especifica el encabezado secreto.
- Agrega el encabezado secreto a la instancia de MailMessage.

En el código dado a continuación, hemos personalizado un encabezado de correo electrónico.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-SetEmailHeaders.java" >}}

El fragmento de código anterior produce un encabezado de correo electrónico en el siguiente formato. Esto se puede observar abriendo el archivo MsgHeaders.msg en Microsoft Outlook y luego viendo sus propiedades.

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: receiver1@receiver.com

CC: receiver2@receiver.com

BCC: receiver3@receiver.com

Subject: correo de prueba

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

secret-header: misterio

```

### **Insertar Encabezado en una Ubicación Específica**

El método [Add](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#add-com.aspose.email.HeaderCollection-) de HeadersCollection inserta el encabezado al final de la colección. Sin embargo, a veces puede ser necesario insertar un encabezado en una ubicación específica. En tal caso, el método Add no te ayudará. Para lograr esto, utiliza el método [Insert](https://reference.aspose.com/email/java/com.aspose.email/headercollection/#insert-java.lang.String-java.lang.String-) de HeadersCollection. Si la colección contiene encabezados con el mismo nombre, este encabezado se insertará antes de otros encabezados con el mismo nombre. A continuación se muestra la firma del método Insert y un código de ejemplo de uso.

``` java

 Firma del Método

HeaderCollection.insert(String name, String value)

```

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-InsertHeaderAtSpecificLocation.java" >}}

### **Agregar Encabezados Personalizados al Correo Electrónico**

Los ejemplos de programación a continuación demuestran cómo especificar un encabezado personalizado en un mensaje de correo electrónico. Un encabezado de correo electrónico puede especificarse utilizando la clase MailMessage. Para especificar un encabezado personalizado en un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
2. Especifica los valores de To, From y Subject usando la instancia de MailMessage.
3. Agrega el encabezado secreto a la instancia de MailMessage.
4. Crea una instancia de la clase SmtpClient y envía el correo electrónico utilizando el método Send.

El siguiente fragmento de código te muestra cómo agregar encabezados personalizados al correo electrónico.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SpecifyCustomHeader-SpecifyCustomHeader.java" >}}

## **Firmar Correos Electrónicos con DKIM**

Aspose.Email permite firmar correos electrónicos con DKIM (DomainKeys Identified Mail). Esto permite a una organización asumir la responsabilidad de un mensaje que está en tránsito ([acerca de DKIM](https://www.dkim.org/)). DKIM agrega una firma digital a los encabezados del mensaje de correo electrónico que puede ser validada por los receptores. La clave pública del remitente permite al receptor verificar que la firma coincide con el contenido del mensaje. El método [dKIMSign](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#dKIMSign-com.aspose.ms.System.Security.Cryptography.RSACryptoServiceProvider-com.aspose.email.DKIMSignatureInfo-) de la clase MailMessage se utiliza para establecer la información criptográfica y de firma para firmar el mensaje. El siguiente fragmento de código te muestra cómo firmar correos electrónicos con DKIM.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-SignEmailsWithDKIM-SignEmailsWithDKIM.java" >}}

## **Realizando una Combinación de Correos**

Las combinaciones de correos te ayudan a crear y enviar un lote de mensajes de correo electrónico similares. El núcleo de los correos electrónicos es el mismo, pero el contenido puede ser personalizado. Típicamente, los detalles de contacto de un destinatario (nombre, segundo nombre, empresa, etc.) se utilizan para personalizar el correo.

|![todo:image_alt_text](https://i.imgur.com/D7WSp90.png)|
| :- |
|**Figura: Ilustración de cómo funciona una combinación de correos**|

Para realizar una combinación de correos con Aspose.Email, sigue los siguientes pasos:

1. Crea una función con nombre de firma
2. Crea una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
3. Especifica el remitente, receptor, asunto y cuerpo.
4. Crea una firma para el final del correo electrónico.
5. Crea una instancia de la clase [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) y pásale la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) .
6. Toma la firma en la instancia de [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) .
7. Crea una instancia de la clase [DataTable](https://reference.aspose.com/email/java/com.aspose.email/datatable/) .
8. Agrega las columnas Receipt, FirstName y LastName como fuentes de datos en la clase DataTable.
9. Crea una instancia de la clase [DataRow](https://reference.aspose.com/email/java/com.aspose.email/datarow/) .
10. Especifica la dirección de recepción, el nombre y el apellido en el objeto DataRow.
11. Crea una instancia de la clase [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
12. Especifica las instancias de [TemplateRoutine](https://reference.aspose.com/email/java/com.aspose.email/templateroutine/) y DataTable en la instancia de [MailMessageCollection](https://reference.aspose.com/email/java/com.aspose.email/mailmessagecollection/) .
13. Crea una instancia de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) y especifica el servidor, puerto, nombre de usuario y contraseña.
14. Envía los correos electrónicos utilizando el método BulkSendAsync de la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) .

El siguiente código envía un correo electrónico a una persona desde tres otras.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-PerformMailMerge-.java" >}}