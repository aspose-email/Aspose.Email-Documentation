---
title: "Administración de archivos de mensajes con Aspose.Email.Outlook"
url: /es/java/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---


## **Conversión de MSG a mensaje MIME**

La API Aspose.Email ofrece la capacidad de convertir archivos MSG en mensajes MIME mediante el [toMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMailMessage-com.aspose.email.MailConversionOptions-) method.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
MapiMessage msg = new MapiMessage(
                            "sender@test.com",
                            "recipient1@test.com; recipient2@test.com",
                            "Test Subject",
                            "This is a body of message.");
MailConversionOptions options = new MailConversionOptions();
options.setConvertAsTnef(true);
MailMessage mail = msg.toMailMessage(options);
~~~

## **Conversión de MSG en EML preservando el cuerpo RTF**

La API proporciona los siguientes métodos para conservar el cuerpo RTF al convertir MSG en EML:

- [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-) - Obtiene o establece un valor que indica si se debe mantener el cuerpo rtf en MailMessage.
- [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-) - Obtiene o establece un valor que indica si se debe mantener el cuerpo rtf en MailMessage.

Los siguientes ejemplos de código muestran cómo mantener el cuerpo rtf en MailMessage:

- using [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-)

```java
MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveRtfContent(true);
MailMessage message = MailMessage.load("fileName", options);
```
- using [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-)

```java
MapiMessage mapi = MapiMessage.load("fileName");
MailConversionOptions options = new MailConversionOptions();
options.setPreserveRtfContent(true);
MailMessage message = mapi.toMailMessage(options);
```
## **Conversión de MSG a MHTML conservando el encabezado de la categoría**

La API Aspose.Email ofrece la posibilidad de agregar un encabezado de categoría al convertir el mensaje a MHTML. Esta función está especificada por la [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) clase como una opción adicional al guardar MailMessage en formato Mhtml.

El siguiente ejemplo de código muestra cómo crear un archivo MHT (MHTML) a partir de un objeto MapiMessage, personalizar el formato y los encabezados del archivo MHT mediante MHTSaveOptions, establecer categorías para el mensaje de correo electrónico y, a continuación, modificar las plantillas de formato y los encabezados de representación del archivo MHT antes de guardarlo.

```java
 MapiMessage msg = new MapiMessage("from@aaa.com", "to@aaa.com", "subj", "body");

msg.setCategories(new String[] { "Urgently", "Important" });

MhtSaveOptions saveOptions = new MhtSaveOptions();

saveOptions.getFormatTemplates().set_Item(MhtTemplateName.CATEGORIES,

    saveOptions.getFormatTemplates().get_Item(MhtTemplateName.CATEGORIES).replace("Categories", "Les catégories"));

saveOptions.getRenderingHeaders().add(MhtTemplateName.CATEGORIES);

msg.save("fileName.mhtml", saveOptions);
```

## **Archivo de plantilla de Outlook para lectura y escritura (.OFT)**

Las plantillas de Outlook son muy útiles cuando quieres enviar un mensaje de correo similar una y otra vez. En lugar de preparar el mensaje desde cero cada vez, primero prepare el mensaje en Outlook y guárdelo como plantilla de Outlook (OFT). Después de eso, siempre que necesite enviar el mensaje, puede crearlo a partir de la plantilla, ahorrando tiempo al escribir el mismo texto en el cuerpo o en la línea de asunto, configurar el formato, etc. Aspose.Correo electrónico [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) La clase se puede usar para cargar y leer un archivo de plantilla de Outlook (OFT). Una vez cargada la plantilla de Outlook en una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase, puede actualizar el remitente, el destinatario, el cuerpo, el asunto y otras propiedades. Tras actualizar las propiedades:

- Envía el correo electrónico mediante [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) clase o
- Guarde el mensaje como MSG y realice más actualizaciones/validaciones con Microsoft Outlook.

En los ejemplos de código que aparecen a continuación, nosotros:

1. Cargue la plantilla mediante el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Actualice algunas de las propiedades.
1. Guarda el mensaje en formato MSG.

El siguiente fragmento de código muestra cómo cargar el archivo OFT, actualizar el mensaje y guardarlo en formato MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Load the Outlook template (OFT) file in MailMessage's instance
MailMessage message = MailMessage.load(dataDir + "sample.oft", new MsgLoadOptions());

// Set the sender and recipients information
String senderDisplayName = "John";
String senderEmailAddress = "john@abc.com";
String recipientDisplayName = "William";
String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));
message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));
message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Set the name, location and time in email body
String meetingLocation = "<u>" + "Hall 1, Convention Center, New York, USA" + "</u>";
String meetingTime = "<u>" + "Monday, June 28, 2010" + "</u>";
message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));
message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Save the message in MSG format and open in Office Outlook
MapiMessage mapimessage = MapiMessage.fromMailMessage(message);
mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapimessage.save(dataDir + "ReadAndWritingOutlookTemplateFile_out.msg");
~~~

### **Guardar el archivo MSG de Outlook como plantilla**

El siguiente fragmento de código muestra cómo guardar el archivo MSG de Outlook como plantilla.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

try (MapiMessage mapi = new MapiMessage("test@from.to", "test@to.to", "template subject", "Template body")) {
    mapi.saveAsTemplate(dataDir + "mapiToOft.msg");
}
~~~

## **Configuración de la categoría de color para los archivos MSG de Outlook**

Una categoría de color marca un mensaje de correo electrónico con algún tipo de importancia o categoría. Microsoft Outlook permite a los usuarios asignar categorías de colores para diferenciar los correos electrónicos. Para gestionar la categoría de color, utilice el [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/). Contiene funciones como [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-), [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-), [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) and [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-).

- [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-) takes [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) y la cadena de categoría de color, por ejemplo, «Categoría púrpura» o «Categoría roja» como argumentos.
- [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-) takes [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) y la cadena de categoría de color que se va a eliminar del mensaje.
- [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) se usa para eliminar todas las categorías de colores del mensaje.
- [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-) se usa para recuperar todas las categorías de colores de un mensaje en particular.

El siguiente ejemplo realiza las tareas que se indican a continuación:

1. Añade una categoría de color.
2. Añade otra categoría de color.
3. Recupera la lista de todas las categorías.
4. Eliminar todas las categorías.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Add Two category
FollowUpManager.addCategory(msg, "Purple Category");
FollowUpManager.addCategory(msg, "Red Category");

// Retrieve the list of available categories
IList categories = FollowUpManager.getCategories(msg);

// Remove the specified category and then Clear all categories
FollowUpManager.removeCategory(msg, "Red Category");
FollowUpManager.clearCategories(msg);
~~~

## **Acceso a la información de seguimiento desde el archivo MSG**

La API Aspose.Email ofrece la capacidad de acceder a la información de seguimiento de un mensaje enviado o recibido. Puede recuperar la información sobre la lectura, la entrega, la lectura, el recibo y los resultados de la votación de un archivo de mensajes.

### **Recuperación de la información de lectura y recibo de entrega**

El siguiente fragmento de código muestra cómo recuperar la información de los recibos de entrega y lectura.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Recipient: " + recipient.getDisplayName());

    // Get the PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY property
    System.out.println("Delivery time: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY).getDateTime());

    // Get the PR_RECIPIENT_TRACKSTATUS_TIME_READ property
    System.out.println("Read time" + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ).getDateTime());
}
~~~

## **Creación de mensajes de reenvío y respuesta**

La API Aspose.Email ofrece la capacidad de crear y formatear mensajes de reenvío y respuesta. La [ReplyMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/replymessagebuilder/) and [ForwardMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/forwardmessagebuilder/) las clases de la API se utilizan para crear los mensajes de respuesta y reenviar, respectivamente. Se puede especificar la creación de un mensaje de respuesta o reenvío mediante cualquiera de los modos de [OriginalMessageAdditionMode](https://reference.aspose.com/email/java/com.aspose.email/originalmessageadditionmode/) enumeración. Esta enumeración tiene los valores siguientes:

- **OriginalMessageAdditionMode.None** - El mensaje original no se incluye en el mensaje de respuesta.
- **OriginalMessageAdditionMode.Attachment** - El mensaje original se incluye como adjunto en el mensaje de respuesta
- **OriginalMessageAdditionMode.Textpart** - El mensaje original se incluye como texto en el cuerpo del mensaje de respuesta

### **Creación de un mensaje de respuesta**

El siguiente fragmento de código muestra cómo crear un mensaje de respuesta.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ReplyMessageBuilder builder = new ReplyMessageBuilder();

// Set ReplyMessageBuilder Properties
builder.setReplyAll(true);
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
builder.setResponseText(
        "<p><b>Dear Friend,</b></p> I want to do is introduce my co-author and co-teacher. <p><a href=\"www.google.com\">This is a first link</a></p><p><a href=\"www.google.com\">This is a second link</a></p>");

MapiMessage replyMsg = builder.buildResponse(originalMsg);
replyMsg.save(dataDir + "reply_out.msg");
~~~

### **Creación de un mensaje de reenvío**

El siguiente fragmento de código muestra cómo crear un mensaje de reenvío.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ForwardMessageBuilder builder = new ForwardMessageBuilder();
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
MapiMessage forwardMsg = builder.buildResponse(originalMsg);
forwardMsg.save(dataDir + "forward_out.msg");
~~~

## **Conservar fechas vacías al convertir un mensaje**

[MapiConversionOptions.setPreserveEmptyDates(boolean)](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmptyDates-boolean-) propiedad que indica si es necesario mantener las fechas vacías al convertir un mensaje. Esta API aparece en Aspose.Email 21.5
El siguiente fragmento de código muestra cómo conservar las fechas vacías.

~~~java
MailMessage mailMessage = MailMessage.load("message.eml");
System.out.println(mailMessage.getDate()); // zero date
MapiConversionOptions mco = MapiConversionOptions.getUnicodeFormat();
// keep empty dates when converting a message
mco.setPreserveEmptyDates(true);
MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, mco);
System.out.println(mapiMessage.getClientSubmitTime()); // zero date
// check zero date
if (mapiMessage.getClientSubmitTime().equals(JavaHelper.ZERO_DATE))
    System.out.println("ZERO DATE");
~~~