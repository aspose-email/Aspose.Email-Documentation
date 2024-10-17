---
title: "Gestión de archivos de mensaje con Aspose.Email.Outlook"
url: /es/java/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Conversión de MSG a mensaje MIME**

La API de Aspose.Email proporciona la capacidad de convertir archivos MSG a mensajes MIME utilizando el método [toMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMailMessage-com.aspose.email.MailConversionOptions-).

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
MapiMessage msg = new MapiMessage(
                            "sender@test.com",
                            "recipient1@test.com; recipient2@test.com",
                            "Asunto de prueba",
                            "Este es el cuerpo del mensaje.");
MailConversionOptions options = new MailConversionOptions();
options.setConvertAsTnef(true);
MailMessage mail = msg.toMailMessage(options);
~~~

## **Conversión de MSG a EML preservando el cuerpo RTF**

La API proporciona los siguientes métodos para preservar el cuerpo RTF al convertir MSG a EML:

- [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-) - Obtiene o establece un valor que indica si se debe mantener el cuerpo RTF en MailMessage.
- [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-) - Obtiene o establece un valor que indica si se debe mantener el cuerpo RTF en MailMessage.

Los siguientes fragmentos de código demuestran cómo mantener el cuerpo RTF en MailMessage:

- usando [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/msgloadoptions/#setPreserveRtfContent-boolean-)

```java
MsgLoadOptions options = new MsgLoadOptions();
options.setPreserveRtfContent(true);
MailMessage message = MailMessage.load("fileName", options);
```
- usando [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/java/com.aspose.email/mailconversionoptions/#setPreserveRtfContent-boolean-)

```java
MapiMessage mapi = MapiMessage.load("fileName");
MailConversionOptions options = new MailConversionOptions();
options.setPreserveRtfContent(true);
MailMessage message = mapi.toMailMessage(options);
```
## **Conversión de MSG a MHTML preservando el encabezado de categoría**

La API de Aspose.Email proporciona la capacidad de agregar un encabezado de categoría al convertir un mensaje a MHTML. Esta característica se especifica mediante la clase [MhtSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mhtsaveoptions/) como una opción adicional al guardar MailMessage en formato Mhtml.

El siguiente fragmento de código muestra cómo crear un archivo MHT (MHTML) a partir de un objeto MapiMessage, personalizar el formato y los encabezados del archivo MHT utilizando MhtSaveOptions, establecer categorías para el mensaje de correo electrónico y luego modificar las plantillas de formato y los encabezados de representación para el archivo MHT antes de guardarlo.

```java
MapiMessage msg = new MapiMessage("from@aaa.com", "to@aaa.com", "subj", "body");

msg.setCategories(new String[] { "Urgentemente", "Importante" });

MhtSaveOptions saveOptions = new MhtSaveOptions();

saveOptions.getFormatTemplates().set_Item(MhtTemplateName.CATEGORIES,
    saveOptions.getFormatTemplates().get_Item(MhtTemplateName.CATEGORIES).replace("Categories", "Las categorías"));

saveOptions.getRenderingHeaders().add(MhtTemplateName.CATEGORIES);

msg.save("fileName.mhtml", saveOptions);
```

## **Lectura y escritura de archivo de plantilla de Outlook (.OFT)**

Las plantillas de Outlook son muy útiles cuando quieres enviar un mensaje de correo electrónico similar una y otra vez. En lugar de preparar el mensaje desde cero cada vez, primero, prepara el mensaje en Outlook y guárdalo como una plantilla de Outlook (OFT). Después de eso, cada vez que necesites enviar el mensaje, puedes crearlo a partir de la plantilla, ahorrando tiempo escribiendo el mismo texto en el cuerpo o en la línea de asunto, configurando el formato, etc. La clase Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) se puede usar para cargar y leer un archivo de plantilla de Outlook (OFT). Una vez que la plantilla de Outlook está cargada en una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), puedes actualizar el remitente, destinatario, cuerpo, asunto y otras propiedades. Después de actualizar las propiedades:

- Envía el correo electrónico usando la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) o
- Guarda el mensaje como MSG y realiza más actualizaciones/validaciones usando Microsoft Outlook.

En los fragmentos de código a continuación, hacemos:

1. Cargamos la plantilla usando la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
2. Actualizamos algunas de las propiedades.
3. Guardamos el mensaje en formato MSG.

El siguiente fragmento de código muestra cómo cargar el archivo OFT, actualizar el mensaje y guardarlo en formato MSG.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

// Cargar el archivo de plantilla de Outlook (OFT) en una instancia de MailMessage
MailMessage message = MailMessage.load(dataDir + "sample.oft", new MsgLoadOptions());

// Establecer la información del remitente y destinatarios
String senderDisplayName = "John";
String senderEmailAddress = "john@abc.com";
String recipientDisplayName = "William";
String recipientEmailAddress = "william@xzy.com";

message.setSender(new MailAddress(senderEmailAddress, senderDisplayName));
message.getTo().addMailAddress(new MailAddress(recipientEmailAddress, recipientDisplayName));
message.setHtmlBody(message.getHtmlBody().replace("DisplayName", "<b>" + recipientDisplayName + "</b>"));

// Establecer el nombre, la ubicación y la hora en el cuerpo del correo electrónico
String meetingLocation = "<u>" + "Salón 1, Centro de Convenciones, Nueva York, EE. UU." + "</u>";
String meetingTime = "<u>" + "Lunes, 28 de junio de 2010" + "</u>";
message.setHtmlBody(message.getHtmlBody().replace("MeetingPlace", meetingLocation));
message.setHtmlBody(message.getHtmlBody().replace("MeetingTime", meetingTime));

// Guardar el mensaje en formato MSG y abrir en Office Outlook
MapiMessage mapimessage = MapiMessage.fromMailMessage(message);
mapimessage.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapimessage.save(dataDir + "ReadAndWritingOutlookTemplateFile_out.msg");
~~~

### **Guardar archivo MSG de Outlook como plantilla**

El siguiente fragmento de código muestra cómo guardar el archivo MSG de Outlook como una plantilla.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

try (MapiMessage mapi = new MapiMessage("test@from.to", "test@to.to", "asunto de plantilla", "Cuerpo de plantilla")) {
    mapi.saveAsTemplate(dataDir + "mapiToOft.msg");
}
~~~

## **Establecer categoría de color para archivos MSG de Outlook**

Una categoría de color marca un mensaje de correo electrónico para algún tipo de importancia o categoría. Microsoft Outlook permite a los usuarios asignar categorías de color para diferenciar los correos electrónicos. Para manejar la categoría de color, utiliza el [FollowUpManager](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/). Contiene funciones como [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-), [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-), [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) y [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-).

- [addCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#addCategory-com.aspose.email.MapiMessage-java.lang.String-) toma [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) y la cadena de categoría de color, por ejemplo, "Categoría Púrpura" o "Categoría Roja" como argumentos.
- [removeCategory](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#removeCategory-com.aspose.email.MapiMessage-java.lang.String-) toma [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) y la cadena de categoría de color que se eliminará del mensaje.
- [clearCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#clearCategories-com.aspose.email.MapiMessage-) se utiliza para eliminar todas las categorías de color del mensaje.
- [getCategories](https://reference.aspose.com/email/java/com.aspose.email/followupmanager/#getCategories-com.aspose.email.MapiMessage-) se utiliza para recuperar todas las categorías de color de un mensaje en particular.

El siguiente ejemplo realiza las tareas como se indica a continuación:

1. Agregar una categoría de color.
2. Agregar otra categoría de color.
3. Recuperar la lista de todas las categorías.
4. Eliminar todas las categorías.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");

// Agregar dos categorías
FollowUpManager.addCategory(msg, "Categoría Púrpura");
FollowUpManager.addCategory(msg, "Categoría Roja");

// Recuperar la lista de categorías disponibles
IList categories = FollowUpManager.getCategories(msg);

// Eliminar la categoría especificada y luego limpiar todas las categorías
FollowUpManager.removeCategory(msg, "Categoría Roja");
FollowUpManager.clearCategories(msg);
~~~ 

## **Acceso a la información de seguimiento del archivo MSG**

La API de Aspose.Email proporciona la capacidad de acceder a la información de seguimiento de un mensaje enviado o recibido. Puede recuperar la información de recibo de lectura, recibo de entrega y votos de un archivo de mensaje.

### **Recuperación de información de recibo de lectura y entrega**

El siguiente fragmento de código muestra cómo recuperar la información de recibo de lectura y entrega.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");
for (MapiRecipient recipient : msg.getRecipients()) {
    System.out.println("Destinatario: " + recipient.getDisplayName());

    // Obtener la propiedad PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY
    System.out.println("Hora de entrega: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_DELIVERY).getDateTime());

    // Obtener la propiedad PR_RECIPIENT_TRACKSTATUS_TIME_READ
    System.out.println("Hora de lectura: " + recipient.getProperties().get_Item(MapiPropertyTag.PR_RECIPIENT_TRACKSTATUS_TIME_READ).getDateTime());
}
~~~ 

## **Creación de mensajes de reenvío y respuesta**

La API de Aspose.Email proporciona la capacidad de crear y dar formato a mensajes de reenvío y respuesta. Las clases [ReplyMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/replymessagebuilder/) y [ForwardMessageBuilder](https://reference.aspose.com/email/java/com.aspose.email/forwardmessagebuilder/) de la API se utilizan para crear los mensajes de respuesta y reenvío respectivamente. Se puede especificar que un mensaje de respuesta o reenvío se cree utilizando cualquiera de los modos de la enumeración [OriginalMessageAdditionMode](https://reference.aspose.com/email/java/com.aspose.email/originalmessageadditionmode/). Esta enumeración tiene los siguientes valores:

- **OriginalMessageAdditionMode.None** - El mensaje original no se incluye en el mensaje de respuesta.
- **OriginalMessageAdditionMode.Attachment** - El mensaje original se incluye como un archivo adjunto en el mensaje de respuesta.
- **OriginalMessageAdditionMode.Textpart** - El mensaje original se incluye como un texto en el cuerpo del mensaje de respuesta.

### **Creación de un mensaje de respuesta**

El siguiente fragmento de código muestra cómo crear un mensaje de respuesta.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ReplyMessageBuilder builder = new ReplyMessageBuilder();

// Establecer propiedades de ReplyMessageBuilder
builder.setReplyAll(true);
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
builder.setResponseText(
        "<p><b>Querido amigo,</b></p> Lo que quiero hacer es presentar a mi coautor y coprofesor. <p><a href=\"www.google.com\">Este es un primer enlace</a></p><p><a href=\"www.google.com\">Este es un segundo enlace</a></p>");

MapiMessage replyMsg = builder.buildResponse(originalMsg);
replyMsg.save(dataDir + "reply_out.msg");
~~~ 

### **Creación de un mensaje de reenvío**

El siguiente fragmento de código muestra cómo crear un mensaje de reenvío.

~~~Java
// Para ejemplos completos y archivos de datos, por favor visita https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MapiMessage originalMsg = MapiMessage.fromFile(dataDir + "message1.msg");
ForwardMessageBuilder builder = new ForwardMessageBuilder();
builder.setAdditionMode(OriginalMessageAdditionMode.Textpart);
MapiMessage forwardMsg = builder.buildResponse(originalMsg);
forwardMsg.save(dataDir + "forward_out.msg");
~~~ 

## **Preservar fechas vacías al convertir un mensaje**

La propiedad [MapiConversionOptions.setPreserveEmptyDates(boolean)](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/#setPreserveEmptyDates-boolean-) indica si es necesario mantener las fechas vacías al convertir un mensaje. Esta API aparece en Aspose.Email 21.5. El siguiente fragmento de código muestra cómo preservar fechas vacías.

~~~java
MailMessage mailMessage = MailMessage.load("message.eml");
System.out.println(mailMessage.getDate()); // fecha cero
MapiConversionOptions mco = MapiConversionOptions.getUnicodeFormat();
// mantener fechas vacías al convertir un mensaje
mco.setPreserveEmptyDates(true);
MapiMessage mapiMessage = MapiMessage.fromMailMessage(mailMessage, mco);
System.out.println(mapiMessage.getClientSubmitTime()); // fecha cero
// verificar la fecha cero
if (mapiMessage.getClientSubmitTime().equals(JavaHelper.ZERO_DATE))
    System.out.println("FECHA CERO");
~~~