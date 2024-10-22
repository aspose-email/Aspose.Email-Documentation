---
title: "Trabajando con Archivos Adjuntos y Objetos Embebidos"
url: /es/java/working-with-attachments-and-embedded-objects/
weight: 20
type: docs
---

## **Gestionando Archivos Adjuntos en Email**

Un archivo adjunto en un correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado así como parte del mensaje al cual está adjunto. La clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//) se utiliza con la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage//). Todos los mensajes incluyen un cuerpo. Además del cuerpo, es posible que desee enviar archivos adicionales. Estos se envían como adjuntos y se representan como una instancia de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment//). Puede enviar cualquier número de archivos adjuntos, pero el tamaño del archivo adjunto está limitado por el servidor de correo. Gmail, por ejemplo, no admite tamaños de archivo mayores a 10MB.
{{% alert %}}
**¡Pruébalo!**

Agrega o elimina archivos adjuntos a correos electrónicos en línea con la gratuita [**Aspose.Email Editor App**](https://products.aspose.app/email/es/editor).
{{% /alert %}}

### **Agregando un Archivo Adjunto**

Para adjuntar un archivo a un correo electrónico, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Cree una instancia de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
1. Cargue el archivo adjunto en la instancia de [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
1. Agregue la instancia de [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) a la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

El siguiente fragmento de código muestra cómo agregar un archivo adjunto a un correo electrónico.

```java
// Crear una instancia de la clase MailMessage
MailMessage message = new MailMessage();
message.setFrom(new MailAddress("sender@from.com"));
message.getTo().add("receiver@to.com");
message.setSubject("Este es un mensaje");
message.setBody("Este es el cuerpo");

// Cargar un archivo adjunto
Attachment attachment = new Attachment("1.txt");

// Agregar múltiples archivos adjuntos en la instancia de la clase MailMessage y guardar el mensaje en disco
message.getAttachments().addItem(attachment);
message.addAttachment(new Attachment("1.jpg"));
message.addAttachment(new Attachment("1.doc"));
message.addAttachment(new Attachment("1.rar"));
message.addAttachment(new Attachment("1.pdf"));
message.save("AddAttachments.eml");
```

Arriba, describimos cómo agregar archivos adjuntos a su mensaje de correo electrónico con Aspose.Email. Lo que sigue muestra cómo eliminar archivos adjuntos y mostrar información sobre ellos en la pantalla.

### **Eliminando un Archivo Adjunto**

Para eliminar un archivo adjunto, siga los pasos a continuación:

- Cree una instancia de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
- Cargue el archivo adjunto en la instancia de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/).
- Agregue el archivo adjunto a la instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Elimine los archivos adjuntos de la instancia de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) utilizando la instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

El siguiente fragmento de código muestra cómo eliminar un archivo adjunto.

```java
// Crear una instancia de la clase MailMessage
MailMessage eml = new MailMessage();
eml.setFrom(new MailAddress("sender@from.com"));
eml.getTo().add("receiver@to.com");

// Cargar un archivo adjunto
Attachment attachment = new Attachment("1.txt");
eml.getAttachments().addItem(attachment);

// Eliminar el archivo adjunto de su MailMessage
eml.getAttachments().removeItem(attachment);
```

### **Mostrando el Nombre del Archivo Adjunto**

Para mostrar el nombre del archivo adjunto, siga estos pasos:

1. Recorra los archivos adjuntos en el mensaje de correo electrónico y
   1. Guarde cada archivo adjunto.
   1. Muestre cada nombre de archivo adjunto en la pantalla.

El siguiente fragmento de código muestra cómo mostrar el nombre de un archivo adjunto en la pantalla.

```java
MailMessage eml = MailMessage.load("Attachments.eml");

for (Attachment attachment : eml.getAttachments()) {
    // Mostrar el nombre del archivo adjunto
    System.out.println(attachment.getName());
}
```

### **Extrayendo Archivos Adjuntos de Emails**

Este tema explica cómo extraer un archivo adjunto de un archivo de correo electrónico. Un archivo adjunto en un correo electrónico es un archivo que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado así como parte del mensaje al cual está adjunto. Todos los mensajes de correo electrónico incluyen una opción para enviar archivos adicionales. Estos se envían como archivos adjuntos y se representan como instancias de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/). La clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) se utiliza con la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) para trabajar con archivos adjuntos. Para extraer archivos adjuntos de un mensaje de correo electrónico, siga estos pasos:

- Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Cargue un archivo de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
- Cree una instancia de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) y úsela en un bucle para extraer todos los archivos adjuntos.
- Guarde el archivo adjunto y muéstrelo en la pantalla.

|**Archivos adjuntos extraídos en email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
El siguiente fragmento de código muestra cómo extraer archivos adjuntos de email.

```java
MailMessage eml = MailMessage.load("Message.eml", new MsgLoadOptions());

for (Attachment attachment : eml.getAttachments()) {
    attachment.save("MessageEmbedded_out.eml");
    System.out.println(attachment.getName());
}
```

#### **Recuperando el Content-Description del Archivo Adjunto**

La API Aspose.Email proporciona la capacidad de leer el Content-Description del archivo adjunto desde el encabezado del archivo adjunto. El siguiente fragmento de código muestra cómo recuperar la descripción del contenido del archivo adjunto.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");
System.out.println(eml.getAttachments().get_Item(0).getHeaders().get_Item("Content-Description"));
```

#### **Determinando si un Archivo Adjunto es un Mensaje Embebido**

El siguiente fragmento de código demuestra cómo determinar si el archivo adjunto es un mensaje embebido o no.

```java
MailMessage eml = MailMessage.load("EmailWithAttachEmbedded.eml");

System.out.println(eml.getAttachments().get_Item(0).isEmbeddedMessage()
        ? "El archivo adjunto es un mensaje embebido."
        : "El archivo adjunto no es un mensaje embebido.");
```
#### **Determinar Archivos Adjuntos Formateados TNEF**

La propiedad [Attachment.isTnef](https://reference.aspose.com/email/java/com.aspose.email/attachment/#isTnef--) de la API Aspose.Email Java indica si el archivo adjunto de mensaje es un mensaje formateado TNEF.

El siguiente fragmento de código demuestra cómo determinar si un archivo adjunto está formateado TNEF:

```java
MailMessage eml = MailMessage.load(fileName);

for (Attachment attachment : eml.getAttachments()) {
    System.out.println("¿Es el archivo adjunto TNEF?: " + attachment.isTnef());
}
```

#### **Extrayendo URI del Archivo Adjunto si el Archivo Adjunto es URI-attachment**

El siguiente fragmento de código demuestra cómo extraer el URI del archivo adjunto.

~~~Java
MailMessage eml = MailMessage.load("fileName");

Attachment attachment = eml.getAttachments().get_Item(0);
if (attachment.isUri()) {
    InputStream inputStream = attachment.getContentStream();
    String uri = new String(IOUtils.toByteArray(inputStream), Charset.forName("utf-8"));
    System.out.println("URI del archivo adjunto: " + uri);
}
~~~

### **Agregando Archivos Adjuntos de Referencia**

Un archivo adjunto de referencia es una alternativa al archivo adjunto local. En algunos casos, los archivos adjuntos de referencia pueden ser preferibles, por ejemplo, si desea gestionar su acceso. Las clases a continuación se utilizan para gestionar y manipular mensajes de correo electrónico y sus archivos adjuntos:

- [ReferenceAttachment](https://reference.aspose.com/email/java/com.aspose.email/referenceattachment/) - Representa un archivo adjunto de referencia. 
- [AttachmentPermissionType](https://reference.aspose.com/email/java/com.aspose.email/attachmentpermissiontype/) - Tipo de datos de permiso asociado con un archivo adjunto de referencia web. 
- [AttachmentProviderType](https://reference.aspose.com/email/java/com.aspose.email/attachmentprovidertype/) - Tipo de servicio web que manipula el archivo adjunto.

El siguiente ejemplo de código demuestra cómo cargar un mensaje de correo electrónico desde un archivo, crear un archivo adjunto de referencia con propiedades específicas, y agregar el archivo adjunto al mensaje de correo electrónico:

```java
MailMessage eml = MailMessage.load("fileName");

ReferenceAttachment refAttach = new ReferenceAttachment("https://[attach_uri]");
refAttach.setName("Document.docx");
refAttach.setProviderType(AttachmentProviderType.OneDrivePro);
refAttach.setPermissionType(AttachmentPermissionType.AnyoneCanEdit);

eml.getAttachments().addItem(refAttach);
```

## **Trabajando con Objetos Embebidos**

Un objeto embebido es un objeto que fue creado con una aplicación y encerrado dentro de un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel puede ser embebida en un informe de Microsoft Word, o un archivo de video puede ser embebido en una presentación de Microsoft PowerPoint. Cuando un archivo está embebido, en lugar de ser insertado o pegado en otro documento, conserva su formato original. El documento embebido puede ser abierto en la aplicación original y modificado.

### **Embeber Objetos en un Email**

La clase [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) se utiliza con la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) para embeber objetos en sus mensajes de correo electrónico. Para agregar un objeto embebido, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Especifique los valores de de, para y asunto en la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Cree una instancia de la clase [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/).
1. Cree una instancia de la clase [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/).
1. Cargue un objeto embebido en la [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/).
1. Agregue el objeto embebido cargado a la instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Agregue la instancia de [AlternateView](https://reference.aspose.com/email/java/com.aspose.email/alternateview/) a la instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

Los fragmentos de código a continuación producen un mensaje de correo electrónico con un cuerpo de texto plano y HTML y una imagen embebida en el HTML.

|**Imagen embebida en el email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
Puede enviar cualquier número de objetos embebidos. El tamaño del archivo adjunto está limitado por el servidor de correo. Gmail, por ejemplo, no admite tamaños de archivo mayores a 10MB. Los fragmentos de código a continuación demuestran cómo embeber objetos en un Email.

```java
// Crear una instancia de la clase MailMessage y establecer las direcciones y contenido
MailMessage mail = new MailMessage();
mail.setFrom(new MailAddress("sender@from.com"));
mail.getTo().add("receiver@to.com");
mail.setSubject("Este es un correo electrónico");

// Crear la parte de texto plano que es visible para aquellos clientes que no soportan HTML
AlternateView plainView = AlternateView.createAlternateViewFromString("Este es mi contenido de texto plano", null, "text/plain");

// Crear la parte HTML. Para embeber imágenes, necesitamos usar el prefijo 'cid' en el valor src de img. 
// El valor cid se mapeará al Content-Id de un recurso enlazado. 
// Así, <img src='cid:barcode'> se mapeará a un LinkedResource con un ContentId de 'barcode'.
AlternateView htmlView = AlternateView.createAlternateViewFromString("Aquí hay una imagen embebida.<img src=cid:barcode>", null, "text/html");

// Crear el LinkedResource (imagen embebida) y agregar el LinkedResource a la vista adecuada
LinkedResource barcode = new LinkedResource("1.jpg", MediaTypeNames.Image.JPEG);
barcode.setContentId("barcode");

mail.getLinkedResources().addItem(barcode);
mail.getAlternateViews().addItem(plainView);
mail.getAlternateViews().addItem(htmlView);
mail.save("EmbeddedImage_out.msg", SaveOptions.getDefaultMsgUnicode());
```

### **Eliminando Objetos Embebidos de un Email**

La [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) se accede a través de la propiedad [MailMessage.LinkedResources](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLinkedResources--). La colección [LinkedResourceCollection](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/) proporciona un método para eliminar completamente objetos embebidos agregados en un mensaje de correo electrónico. Utilice la versión sobrecargada del método [LinkedResourceCollection.removeAt](https://reference.aspose.com/email/java/com.aspose.email/linkedresourcecollection/#removeAt-int-boolean-) para eliminar todos los rastros de un objeto embebido de un mensaje de correo electrónico.

El código de ejemplo a continuación muestra cómo eliminar objetos embebidos de un mensaje de correo electrónico.

```java
// Cargar el mensaje de prueba con Recursos Enlazados
MailMessage msg = MailMessage.load("EmlWithLinkedResources.eml");

// Eliminar un LinkedResource
msg.getLinkedResources().removeAt(0, true);

// Ahora limpie la Vista Alternativa para Recursos Enlazados
msg.getAlternateViews().get_Item(0).getLinkedResources().clear(true);
```

### **Extrayendo Objetos Embebidos**

Este tema explica cómo extraer objetos embebidos de un archivo de correo electrónico. Un objeto embebido es un objeto que fue creado con una aplicación y encerrado dentro de un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel puede ser embebida en un informe de Microsoft Word, o un archivo de video puede ser embebido en una presentación de Microsoft PowerPoint. Cuando un archivo está embebido, en lugar de ser insertado o pegado en otro documento, conserva su formato original. El documento embebido puede ser abierto en la aplicación original y ser modificado. Para extraer un objeto embebido de un mensaje de correo electrónico, siga estos pasos:

1. Cree una instancia de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Cargue un archivo de correo electrónico en la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Cree un bucle y cree una instancia de la clase [Attachment](https://reference.aspose.com/email/java/com.aspose.email/attachment/) dentro de él.
1. Guarde el archivo adjunto y muéstrelo en pantalla.
1. Especifique la dirección del remitente y el destinatario en la instancia de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).
1. Envíe el correo electrónico utilizando la clase [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/).

El siguiente fragmento de código extrae objetos embebidos de un correo electrónico.

|**Objetos embebidos extraídos en email**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_3.png)|
El siguiente fragmento de código muestra cómo extraer objetos embebidos.

```java
MailMessage mailMsg = MailMessage.load("Message.msg", new MsgLoadOptions());

for (Attachment attachment : mailMsg.getAttachments()) {
    attachment.save("MessageEmbedded_out.msg");
    System.out.println(attachment.getName());
}
```

#### **Identificar y Extraer un Archivo Adjunto Embebido desde MSG Formateado como RTF**

El siguiente código puede ser utilizado para mensajes formateados como RTF para diferenciar y extraer archivos adjuntos que son Inline o que aparecen como iconos en el cuerpo del mensaje. El siguiente fragmento de código muestra cómo identificar y extraer un archivo adjunto embebido desde MSG formateado como RTF.

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

## **Recuperando Archivos Adjuntos de Correos Electrónicos Firmados**

Los correos electrónicos firmados contienen un único archivo adjunto **smime.p7m**. Esto significa que el correo electrónico está cifrado por SMIME. 
El formato de archivo **Smime.p7m** es la firma digital. 
Para ver el contenido de este correo electrónico utilice el método [RemoveSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/removesignature/). El método devuelve un objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) sin una firma digital.

```java
MailMessage signedEml = MailMessage.load("signed.eml");

if (signedEml.isSigned()) {
    for (int i = 0; i < signedEml.getAttachments().size(); i++) {
        System.out.println("Archivo adjunto de email firmado " + i + ": " + signedEml.getAttachments().get_Item(i).getName());
    }

    // El correo electrónico está firmado. Eliminar la firma.
    MailMessage eml = signedEml.removeSignature();

    System.out.println("Firma eliminada.");

    for (int i = 0; i < eml.getAttachments().size(); i++) {
        System.out.println("Archivo adjunto de email " + i + ": " + eml.getAttachments().get_Item(i).getName());
    }
}
```

### **Trabajando con Content-Type y Content-Disposition**

La API Aspose.Email proporciona la capacidad de trabajar con el [Content-Type](https://datatracker.ietf.org/doc/html/rfc2045#section-5) y [Content-Disposition](https://datatracker.ietf.org/doc/html/rfc2183) del encabezado del archivo adjunto. El siguiente fragmento de código muestra cómo obtener y cambiar la descripción del contenido del archivo adjunto.

#### **Mostrando Parámetros de Content-Type y Content-Disposition**

El siguiente fragmento de código muestra cómo mostrar parámetros de Content-Type y Content-Disposition en la pantalla:

~~~Java
void run(MailMessage message) {
    // Archivos adjuntos
    for (Attachment attachment : message.getAttachments()) {
        ContentDisposition contentDisposition = attachment.getContentDisposition();
        printContentDisposition(contentDisposition);
        ContentType contentType = attachment.getContentType();
        printContentType(contentType);
    }
    // Recursos enlazados
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

#### **Utilizando Parámetros de Content-Type y Content-Disposition con Archivos Adjuntos**

El siguiente fragmento de código muestra cómo utilizar los parámetros Content-Type y Content-Disposition con un archivo adjunto:

~~~Java
MailMessage eml = MailMessage.load(fileName);

Attachment attachment = new Attachment(pdfFileName, new ContentType("application/octet-stream"));
attachment.getContentDisposition().setDispositionType("attachment");
attachment.getContentDisposition().setFileName(fileName);

eml.addAttachment(attachment);
~~~