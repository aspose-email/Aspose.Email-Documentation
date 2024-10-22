---
title: "Creación y Guardado de Archivos MSG"
url: /es/java/creando-y-guardando-archivos-msg/
weight: 10
type: docs
---

Aspose.Email admite la creación de archivos de mensaje de Outlook (MSG). Este artículo explica cómo:

- Crear mensajes MSG.
- Crear mensajes MSG con archivos adjuntos.
- Crear un mensaje MSG con un cuerpo RTF.
- Guardar un mensaje como borrador.
- Trabajar con compresión de cuerpo.

## **Creando y guardando mensajes de Outlook**

La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) tiene el método [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) que puede guardar archivos MSG de Outlook en disco o en un flujo. Los fragmentos de código a continuación crean una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/), establecen propiedades como de, para, asunto y cuerpo. El método [save](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#save-java.lang.String-) toma el nombre del archivo como argumento. Además, los mensajes de Outlook se pueden crear con un [cuerpo RTF comprimido](#creando-archivos-msg-con-cuerpo-rtf) utilizando las [MapiConversionOptions](https://reference.aspose.com/email/java/com.aspose.email/mapiconversionoptions/).

1. Cree una nueva instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) y establezca las propiedades De, Para, Asunto y Cuerpo.
1. Llame al método [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) de la clase [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) que acepta el objeto del tipo [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). El método [fromMailMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#fromMailMessage-com.aspose.email.MailMessage-) convierte el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) en un [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) (MSG).
1. Llame al método [MapiMessage.save](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) para guardar el archivo MSG.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

// Crear una instancia de la clase MailMessage
MailMessage mailMsg = new MailMessage();

// Establecer las propiedades de de, para, asunto y cuerpo
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("Este es un mensaje de prueba");
mailMsg.setBody("Este es el cuerpo de prueba");

// Crear una instancia de la clase MapiMessage y pasar MailMessage como argumento
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);

// Guardar el archivo de mensaje (MSG)
String strMsgFile = "CreandoYGuardandoMensajesDeOutlook_out.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~

## **Creando archivos MSG con archivos adjuntos**

[En el ejemplo anterior](#creando-y-guardando-mensajes-de-outlook), creamos un archivo MSG simple. Aspose.Email también admite el guardado de archivos de mensaje con archivos adjuntos. Todo lo que necesita hacer es agregar los archivos adjuntos a la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Agregue archivos adjuntos llamando al método *addItem* en la colección [MailMessage.Attachments](https://reference.aspose.com/email/java/com.aspose.email/attachmentcollection/).

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

String[] files = new String[2];
files[0] = "attachment.doc";
files[1] = "attachment.png";

// Crear una instancia de la clase MailMessage
MailMessage mailMsg = new MailMessage();

// Establecer las propiedades de de, para, asunto y cuerpo
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("Este es un mensaje de prueba");
mailMsg.setBody("Este es el cuerpo de prueba");

// Agregar los archivos adjuntos
for (String strFileName : files)
{
    mailMsg.getAttachments().addItem(new Attachment(strFileName));
}

// Crear una instancia de la clase MapiMessage y pasar MailMessage como argumento
MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
String strMsgFile = "CrearMensajesConAdjuntos.msg";
outlookMsg.save(dataDir + strMsgFile);
~~~

## **Creando archivos MSG con cuerpo RTF**

También puede crear archivos de mensaje de Outlook (MSG) con cuerpos de texto enriquecido (RTF) con Aspose.Email. El cuerpo RTF admite el formato de texto. Cree uno estableciendo la propiedad [MailMessage.HtmlBody](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setHtmlBody-java.lang.String-). Cuando convierte una instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) en una instancia de [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/), el cuerpo HTML se convierte en RTF. De esta manera, se preserva el formato del cuerpo del correo electrónico.

El siguiente ejemplo crea un archivo MSG con un cuerpo RTF. Hay un encabezado, formato en negrita y subrayado aplicado en el cuerpo HTML. Este formato se mantiene cuando el HTML se convierte en RTF.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

// Crear una instancia de la clase MailMessage
MailMessage mailMsg = new MailMessage();

// Establecer las propiedades de de, para, asunto y cuerpo
mailMsg.setFrom(MailAddress.to_MailAddress("sender@domain.com"));
mailMsg.setTo(MailAddressCollection.to_MailAddressCollection("receiver@domain.com"));
mailMsg.setSubject("Este es un mensaje de prueba");
mailMsg.setHtmlBody("<h3>ejemplo rtf</h3><p>creando un <b><u>mensaje de Outlook (msg)</u></b> usando Aspose.Email.</p>");

MapiMessage outlookMsg = MapiMessage.fromMailMessage(mailMsg);
outlookMsg.save(dataDir + "CreandoArchivosMSGConCuerpoRTF_out.msg");
~~~

## **Guardando mensaje en estado de borrador**

Los correos electrónicos se guardan como borradores cuando alguien ha comenzado a editarlos pero quiere regresar a completarlos más tarde. Aspose.Email admite el guardado de mensajes de correo electrónico en estado de borrador estableciendo una bandera de mensaje. A continuación se muestra el código de ejemplo para guardar un mensaje de correo electrónico de Outlook (MSG) como borrador.

{{% alert %}}
Tenga en cuenta que en el estado de borrador, Outlook no muestra ninguna información del remitente asignada a MapiMessage.
Si necesitamos mostrar la información del remitente, debemos establecer la bandera MSGFLAG_READ.
{{% /alert %}}

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

// Cambiar propiedades de un archivo MSG existente
String strExistingMsg = "mensaje.msg";

// Cargar el archivo existente en MailMessage y cambiar las propiedades
MailMessage msg = MailMessage.load(dataDir + strExistingMsg, new MsgLoadOptions());
msg.setSubject(msg.getSubject() + " NUEVO ASUNTO (actualizado por Aspose.Email)");
msg.setHtmlBody(msg.getHtmlBody() + " NUEVO CUERPO (actualizado por Aspose.Email)");

// Crear una instancia del tipo MapiMessage desde MailMessage, establecer la bandera del mensaje a no enviado (estado de borrador) y guardarlo
MapiMessage mapiMsg = MapiMessage.fromMailMessage(msg);
mapiMsg.setMessageFlags(MapiMessageFlags.MSGFLAG_UNSENT);
mapiMsg.save(dataDir + "GuardandoMensajeEnEstadoDeBorrador_out.msg");
~~~

## **Implicaciones de la compresión del cuerpo**

El método de compresión del cuerpo RTF se puede usar para generar un archivo MSG de menor tamaño. Sin embargo, esto resulta en una velocidad de creación más lenta. Para crear mensajes con una velocidad mejorada, establezca la bandera en **falso**. Esta bandera, a su vez, tiene un efecto en los PST creados: archivos MSG más pequeños resultan en PST más pequeños, y archivos MSG grandes resultan en una creación de PST más lenta.

~~~Java
// Para ejemplos completos y archivos de datos, por favor vaya a https://github.com/aspose-email/Aspose.Email-for-Java
String fileName = "outlook/test.msg";

MailMessage message = MailMessage.load(fileName);
MapiConversionOptions options = new MapiConversionOptions();
options.setUseBodyCompression(true);
MapiMessage ae_mapi = MapiMessage.fromMailMessage(message, options);
~~~