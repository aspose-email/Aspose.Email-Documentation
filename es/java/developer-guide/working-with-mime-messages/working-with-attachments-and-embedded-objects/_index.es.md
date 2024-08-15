---
title: "Trabajo con archivos adjuntos y objetos incrustados"
url: /es/java/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---


## **Administración de archivos adjuntos de correo electrónico**

Un archivo adjunto de correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje independiente o como parte del mensaje al que está adjunto. El [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) la clase se usa con [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage//) clase. Todos los mensajes incluyen un cuerpo. Además del cuerpo, es posible que desee enviar archivos adicionales. Se envían como archivos adjuntos y se representan como una instancia del [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) clase. Puede enviar cualquier cantidad de archivos adjuntos, pero el servidor de correo limita el tamaño de los archivos adjuntos. Gmail, por ejemplo, no admite archivos de más de 10 MB.
{{% alert %}}
**¡Pruébalo!**

Agregue o elimine archivos adjuntos de correo electrónico en línea con la versión gratuita [**Aplicación Aspose.Email Editor**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregar un archivo adjunto**

Para adjuntar un archivo adjunto a un correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Crea una instancia del [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
1. Cargue el accesorio en el [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) instance.
1. Añada el [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) instancia en el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.

El siguiente fragmento de código muestra cómo añadir un archivo adjunto a un correo electrónico.

```java
// Crea una instancia de MailMessage class
MailMessage message = new MailMessage();
message.setFrom(new MailAddress("sender@from.com"));
message.getTo().add("receiver@to.com");
message.setSubject("This is message");
message.setBody("This is body");

// Load an attachment
Attachment attachment = new Attachment("1.txt");

// Add Multiple Attachment in instance of MailMessage class and Save message to disk
message.getAttachments().addItem(attachment);
message.addAttachment(new Attachment("1.jpg"));
message.addAttachment(new Attachment("1.doc"));
message.addAttachment(new Attachment("1.rar"));
message.addAttachment(new Attachment("1.pdf"));
message.save("AddAttachments.eml");
```

Anteriormente, describimos cómo agregar archivos adjuntos a su mensaje de correo electrónico con Aspose.Email. A continuación se muestra cómo eliminar los archivos adjuntos y mostrar la información sobre ellos en la pantalla.

### **Eliminar un archivo adjunto**

Para eliminar un archivo adjunto, siga los pasos que se indican a continuación:

- Crea una instancia de [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
- Cargue el archivo adjunto en el caso de [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) class.
- Agregue el archivo adjunto a la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Elimine los archivos adjuntos de la instancia de [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) clase que usa el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia de clase.

En el siguiente fragmento de código se muestra cómo eliminar un archivo adjunto.

```java
// Crea una instancia de MailMessage class
MailMessage eml = new MailMessage();
eml.setFrom(new MailAddress("sender@from.com"));
eml.getTo().add("receiver@to.com");

// Load an attachment
Attachment attachment = new Attachment("1.txt");
eml.getAttachments().addItem(attachment);

// Remove attachment from your MailMessage
eml.getAttachments().removeItem(attachment);
```

### **Mostrar el nombre del archivo adjunto**

Para mostrar el nombre del archivo adjunto, sigue estos pasos:

1. Revisa los archivos adjuntos del mensaje de correo electrónico y
   1. Guarda cada archivo adjunto.
   1. Muestra el nombre de cada adjunto en la pantalla.

El siguiente fragmento de código muestra cómo mostrar el nombre de un archivo adjunto en la pantalla.

```java
MailMessage eml = MailMessage.load("Attachments.eml");

for (Attachment attachment : eml.getAttachments()) {
    // Display the attachment file name
    System.out.println(attachment.getName());
}
```

### **Extraer archivos adjuntos de correo electrónico**

En este tema se explica cómo extraer un archivo adjunto de un archivo de correo electrónico. Un archivo adjunto de correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje independiente o como parte del mensaje al que está adjunto. Todos los mensajes de correo electrónico incluyen la opción de enviar archivos adicionales. Se envían como archivos adjuntos y se representan como instancias del [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) clase. El [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) la clase se usa con [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase para trabajar con archivos adjuntos. Para extraer los archivos adjuntos de un mensaje de correo electrónico, sigue estos pasos:

- Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
- Cargue un archivo de correo electrónico en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
- Crea una instancia del [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) clase y úsala en bucle para extraer todos los archivos adjuntos.
- Guarde el archivo adjunto y muéstrelo en la pantalla.

|**Archivos adjuntos extraídos en el correo electrónico**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
El siguiente fragmento de código muestra cómo extraer archivos adjuntos de correo electrónico.

```java
MailMessage eml = MailMessage.load("Message.eml", new MsgLoadOptions());

for (Attachment attachment : eml.getAttachments()) {
    attachment.save("MessageEmbedded_out.eml");
    System.out.println(attachment.getName());
}
```

#### **Recuperar la descripción del contenido del archivo adjunto**

La API Aspose.Email ofrece la capacidad de leer la descripción del contenido del adjunto desde el encabezado del archivo adjunto. El siguiente fragmento de código muestra cómo recuperar la descripción del contenido del archivo adjunto.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");
System.out.println(eml.getAttachments().get_Item(0).getHeaders().get_Item("Content-Description"));
```

#### **Determinar si un adjunto es un mensaje incrustado**

El siguiente fragmento de código muestra cómo determinar si el adjunto es un mensaje incrustado o no.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");

System.out.println(eml.getAttachments().get_Item(0).isEmbeddedMessage()
        ? "Attachment is an embedded message."
        : "Attachment isn't an embedded message.");
```
#### **Determine los archivos adjuntos con formato TNEF**

The [Attachment.isTnef](https://reference.aspose.com/email/java/com.aspose.email/attachment/#isTnef--) La propiedad de la API Java Aspose.Email indica si el adjunto del mensaje es un mensaje con formato TNEF.

El siguiente fragmento de código muestra cómo determinar si un adjunto tiene formato TNEF:

```java
MailMessage eml = MailMessage.load(fileName);

for (Attachment attachment : eml.getAttachments()) {
    System.out.println("Is Attachment TNEF?: " + attachment.isTnef());
}
```

#### **Extraer el URI del archivo adjunto si el archivo adjunto es un enlace URI**

El siguiente fragmento de código muestra cómo extraer el URI del adjunto.

~~~Java
MailMessage eml = MailMessage.load("fileName");

Attachment attachment = eml.getAttachments().get_Item(0);
if (attachment.isUri()) {
    InputStream inputStream = attachment.getContentStream();
    String uri = new String(IOUtils.toByteArray(inputStream), Charset.forName("utf-8"));
    System.out.println("Attachment URI: " + uri);
}
~~~

### **Añadir adjuntos de referencia**

Un archivo adjunto de referencia es una alternativa al archivo adjunto local. En algunos casos, los archivos adjuntos de referencia pueden ser preferibles, por ejemplo, si desea administrar su acceso. Las siguientes clases se utilizan para gestionar y manipular los mensajes de correo electrónico y sus archivos adjuntos:

- [ReferenceAttachment](https://reference.aspose.com/email/java/com.aspose.email/referenceattachment/) - Representa un adjunto de referencia.
- [AttachmentPermissionType](https://reference.aspose.com/email/java/com.aspose.email/attachmentpermissiontype/) - Los datos del tipo de permiso asociados a un adjunto de referencia web.
- [AttachmentProviderType](https://reference.aspose.com/email/java/com.aspose.email/attachmentprovidertype/) - El tipo de servicio web que manipula el archivo adjunto.

El siguiente ejemplo de código muestra cómo cargar un mensaje de correo electrónico desde un archivo, crear un adjunto de referencia con propiedades específicas y agregar el archivo adjunto al mensaje de correo electrónico:

```java
MailMessage eml = MailMessage.load("fileName");

ReferenceAttachment refAttach = new ReferenceAttachment("https://[attach_uri]")
refAttach.setName("Document.docx");
refAttach.setProviderType(AttachmentProviderType.OneDrivePro);
refAttach.setPermissionType(AttachmentPermissionType.AnyoneCanEdit);

eml.getAttachments().addItem(refAttach);
```

## **Trabajo con objetos incrustados**

Un objeto incrustado es un objeto que se creó con una aplicación y se incluyó en un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel se puede incrustar en un informe de Microsoft Word o se puede incrustar un archivo de vídeo en una presentación de Microsoft PowerPoint. Cuando un archivo se incrusta, en lugar de insertarlo o pegarlo en otro documento, conserva su formato original. El documento incrustado se puede abrir en la aplicación original y modificarlo.

### **Incrustar objetos en un correo electrónico**

The [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) la clase se usa con [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) clase para incrustar objetos en tus mensajes de correo electrónico. Para añadir un objeto incrustado, sigue estos pasos

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Especifique los valores de origen, destino y asunto en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Crea una instancia del [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) class.
1. Crea una instancia del [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) class.
1. Cargue un objeto incrustado en [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/).
1. Agregue el objeto incrustado cargado al [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia de clase.
1. Añada el [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) instancia a la [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instancia de clase.

Los fragmentos de código siguientes producen un mensaje de correo electrónico con texto sin formato y cuerpos HTML y una imagen incrustada en el HTML.

|**Imagen incrustada en el correo electrónico**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Puede enviar cualquier cantidad de objetos incrustados. El servidor de correo limita el tamaño del archivo adjunto. Gmail, por ejemplo, no admite archivos de más de 10 MB. Los fragmentos de código que aparecen a continuación muestran cómo incrustar objetos en un correo electrónico.

```java
// Crea una instancia del MailMessage class and Set the addresses and Set the content
MailMessage mail = new MailMessage();
mail.setFrom(new MailAddress("sender@from.com"));
mail.getTo().add("receiver@to.com");
mail.setSubject("This is an email");

// Create the plain text part It is viewable by those clients that don't support HTML
AlternateView plainView = AlternateView.createAlternateViewFromString("This is my plain text content", null, "text/plain");

// Create the HTML part.To embed images, we need to use the prefix 'cid' in the img src value.
// The cid value will map to the Content-Id of a Linked resource.
// Thus <img src='cid:barcode'> will map to a LinkedResource with a ContentId of //'barcode'.
AlternateView htmlView = AlternateView.createAlternateViewFromString("Here is an embedded image.<img src=cid:barcode>", null, "text/html");

// Create the LinkedResource (embedded image) and Añada el LinkedResource to the appropriate view
LinkedResource barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.JPEG);
barcode.setContentId("barcode");

mail.getLinkedResources().addItem(barcode);
mail.getAlternateViews().addItem(plainView);
mail.getAlternateViews().addItem(htmlView);
mail.save("EmbeddedImage_out.msg", SaveOptions.getDefaultMsgUnicode());
```

### **Eliminar objetos incrustados del correo electrónico**

[LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) accedido a través de [MailMessage.LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLinkedResources--) propiedad. El [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) La colección proporciona un método para eliminar por completo los objetos incrustados agregados a un mensaje de correo electrónico. Utilice la versión sobrecargada de [LinkedResourceCollection.removeAt](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/#removeAt-int-boolean-) método para eliminar todos los rastros de un objeto incrustado de un mensaje de correo electrónico.

El código de ejemplo que aparece a continuación muestra cómo eliminar objetos incrustados de un mensaje de correo electrónico.

```java
// Load the test message with Linked Resources
MailMessage msg = MailMessage.load("EmlWithLinkedResources.eml");

// Remove a LinkedResource
msg.getLinkedResources().removeAt(0, true);

// Now clear the Alternate View for linked Resources
msg.getAlternateViews().get_Item(0).getLinkedResources().clear(true);
```

### **Extracción de objetos incrustados**

En este tema se explica cómo extraer objetos incrustados de un archivo de correo electrónico. Un objeto incrustado es un objeto que se creó con una aplicación y se incluyó en un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel se puede incrustar en un informe de Microsoft Word o se puede incrustar un archivo de vídeo en una presentación de Microsoft PowerPoint. Cuando un archivo se incrusta, en lugar de insertarlo o pegarlo en otro documento, conserva su formato original. El documento incrustado se puede abrir en la aplicación original y modificarlo. Para extraer un objeto incrustado de un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class.
1. Cargue un archivo de correo electrónico en [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Cree un bucle y cree una instancia del [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) clase en él.
1. Guarde el archivo adjunto y muéstrelo en la pantalla.
1. Especifique la dirección del remitente y del destinatario en el [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance.
1. Enviar un correo electrónico mediante [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class.

El siguiente fragmento de código extrae los objetos incrustados de un correo electrónico.

|**Objetos incrustados extraídos en el correo electrónico**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
El siguiente fragmento de código muestra cómo extraer objetos incrustados.

```java
MailMessage mailMsg = MailMessage.load("Message.msg", new MsgLoadOptions());

for (Attachment attachment : mailMsg.getAttachments()) {
    attachment.save("MessageEmbedded_out.msg");
    System.out.println(attachment.getName());
}
```

#### **Identificar y extraer un archivo adjunto incrustado de un MSG formateado como RTF**

El siguiente código se puede usar para mensajes formateados como RTF para diferenciar y extraer los archivos adjuntos que están en línea o que aparecen como un icono en el cuerpo del mensaje. En el siguiente fragmento de código, se muestra cómo identificar y extraer un archivo adjunto incrustado de un mensaje con formato RTF.

```java
public static void extractInlineAttachments() {
    MapiMessage message = MapiMessage.load("MSG file with RTF Formatting.msg");
    for (MapiAttachment attachment : message.getAttachments()) {

        if (isAttachmentInline(attachment)) {
            try {
                saveAttachment(attachment, UUID.randomUUID().toString());
            } catch (Exception ex) {
                System.err.println(ex);
            }
        }
    }
}

static boolean isAttachmentInline(MapiAttachment attachment) {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("\u0003ObjInfo".equals(property.getName())) {
            byte[] data = property.getData();
            int odtPersist1 = data[1] << 8 | data[0];
            return (odtPersist1 & 0x40) == 0;
        }
    }
    return false;
}

static void saveAttachment(MapiAttachment attachment, String fileName) throws IOException {
    for (MapiProperty property : attachment.getObjectData().getProperties().get_Values()) {
        if ("Package".equals(property.getName())) {
            try (FileOutputStream fs = new FileOutputStream(fileName)) {
                fs.write(property.getData(), 0, property.getData().length);
            }
        }
    }
}
```

## **Recuperar archivos adjuntos de un correo electrónico firmado**

Los correos electrónicos firmados contienen una **smime.p7m** adjunto. Significa que el correo electrónico está encriptado por SMIME.
**Smime.p7m** el formato del archivo es la firma digital.
Para ver el contenido de este correo electrónico, utilice el [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/) método. El método devuelve un [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) objeto sin firma digital.

```java
MailMessage signedEml = MailMessage.load("signed.eml");

if (signedEml.isSigned()) {
    for (int i = 0; i < signedEml.getAttachments().size(); i++) {
        System.out.println("Signed email attachment" + i + ": " + signedEml.getAttachments().get_Item(i).getName());
    }

    // The email is signed. Remove a signature.
    MailMessage eml = signedEml.removeSignature();

    System.out.println("Signature removed.");

    for (int i = 0; i < eml.getAttachments().size(); i++) {
        System.out.println("Email attachment" + i + ": " + eml.getAttachments().get_Item(i).getName());
    }
}
```

### **Trabajando con el tipo de contenido y la disposición del contenido**

La API Aspose.Email brinda la capacidad de trabajar con el archivo adjunto [Content-Type](https://datatracker.ietf.org/doc/html/rfc2045#section-5) and [Content-Disposition](https://datatracker.ietf.org/doc/html/rfc2183) desde el encabezado del archivo adjunto. El siguiente fragmento de código muestra cómo obtener y cambiar la descripción del contenido del archivo adjunto.

#### **Visualización de los parámetros de tipo y disposición del contenido**

El siguiente fragmento de código muestra cómo mostrar los parámetros de tipo de contenido y disposición del contenido en la pantalla:

~~~Java
void run(MailMessage message) {
    // Attachments
    for (Attachment attachment : message.getAttachments()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
    // Linked Resources
    for (LinkedResource attachment : message.getLinkedResources()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
}

void printContentType(ContentType contentType) {
    System.out.println("media-type: " + contentType.getMediaType());
    System.out.println("charset: " + contentType.getCharSet());
    System.out.println("name: " + contentType.getName());
}

void printContentDisposition(ContentDisposition contentDisposition) {
    System.out.println("disposition-type: " + contentDisposition.getDispositionType());
    System.out.println("is-inline: " + contentDisposition.getInline());
    System.out.println("filename: " + contentDisposition.getFileName());
    System.out.println("creation-date: " + contentDisposition.getCreationDate());
    System.out.println("modification-date: " + contentDisposition.getModificationDate());
    System.out.println("read-date: " + contentDisposition.getReadDate());
    System.out.println("size: " + contentDisposition.getSize());
}
~~~

#### **Uso de los parámetros de tipo y disposición del contenido con archivos adjuntos**

En el siguiente fragmento de código, se muestra cómo usar los parámetros Content-Type y Content-Disposition con un archivo adjunto:

~~~Java
MailMessage eml = MailMessage.load(fileName);

Attachment attachment = new Attachment(pdfFileName, new ContentType("application/octet-stream"));
attachment.getContentDisposition().setDispositionType("attachment");
attachment.getContentDisposition().setFileName(fileName);

eml.addAttachment(attachment);
~~~