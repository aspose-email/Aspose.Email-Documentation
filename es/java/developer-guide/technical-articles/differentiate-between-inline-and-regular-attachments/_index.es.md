---
title: "Diferenciar entre archivos adjuntos en línea y regulares"
url: /es/java/diferentiate-between-inline-and-regular-attachments/
weight: 10
type: docs
---

{{% alert color="primary" %}} 

Los mensajes de correo electrónico pueden contener imágenes en línea así como archivos adjuntos. Usando [MailMessage](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailMessage), los archivos adjuntos en línea pueden ser extraídos de la colección [LinkedResourceCollection](https://apireference.aspose.com/email//java/com.aspose.email/linkedresourcecollection), mientras que los archivos adjuntos regulares pueden ser accedidos y extraídos con la colección [AttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/attachmentcollection) de un mensaje. Sin embargo, esto es diferente cuando el mensaje se carga usando [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage), ya que todas las imágenes en línea y los archivos adjuntos regulares son accesibles para el usuario en la misma colección [MapiAttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/mapiattachmentcollection). Por lo tanto, se necesita un método que pueda diferenciar entre un archivo adjunto en línea y uno regular cuando se utiliza [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage).

{{% /alert %}} 

Este artículo explica cómo diferenciar los archivos adjuntos en línea de los regulares usando [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage). Al decidir, se toma en cuenta el tipo de cuerpo de [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) de la siguiente manera:

- **Cuerpo de texto simple**: Los mensajes de correo electrónico con tipo de cuerpo de texto simple no necesitan ser verificados, ya que todos los archivos adjuntos en tales mensajes son siempre archivos adjuntos regulares.
- **Cuerpo HTML**: Para los mensajes con un cuerpo HTML, el archivo adjunto no solo debe contener la propiedad PR_ATTACH_FLAGS (0x37140003), sino que su valor debe ser igual a 0x00000004 para archivos adjuntos en línea. Si se cumple esta condición, entonces depende además de las etiquetas PR_ATTACH_CONTENT_LOCATION y PR_ATTACH_CONTENT_ID para determinar la naturaleza del archivo adjunto. Sin embargo, en ausencia de la etiqueta MAPI PR_ATTACH_FLAGS, se verifica el archivo adjunto por la propiedad PR_ATTACH_DISPOSITION (0x3716001F o 0x3716001E) para determinar el tipo de archivo adjunto.
- **Cuerpo RTF**: Si el cuerpo es RTF, entonces todos los archivos adjuntos OLE son archivos adjuntos en línea. El valor de PR_ATTACH_METHOD para todos los archivos adjuntos OLE es igual a 0x00000006.

El siguiente ejemplo de código demuestra cómo diferenciar programáticamente entre archivos adjuntos en línea y regulares. La función isInlineAttachment toma un archivo adjunto y MapiMessage como parámetros de entrada y devuelve verdadero si el archivo adjunto es un archivo adjunto en línea.

~~~java
public static boolean isInlineAttachment(MapiAttachment att, MapiMessage msg) {
    if (msg.getBodyType() == BodyContentType.PlainText)
        // ignorar indicaciones para mensajes de texto simple
        return false;
    else if (msg.getBodyType() == BodyContentType.Html) {
        // verificar la propiedad PidTagAttachFlags
        if (att.getProperties().containsKey(0x37140003)) {
            Long attachFlagsValue = att.getPropertyLong(0x37140003);
            if (attachFlagsValue != null && (attachFlagsValue > 3 || attachFlagsValue < 1)) {
                // verificar la propiedad PidTagAttachContentId
                if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                        || att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W)) {
                    String contentId = att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID) 
                            ? att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            : att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W);
                    if (!contentId.isEmpty() && msg.getBodyHtml().contains(contentId)) {
                        return true;
                    }
                }
                // verificar la propiedad PidTagAttachContentLocation
                if (att.getProperties().containsKey(0x3713001E) 
                        || att.getProperties().containsKey(0x3713001F)) {
                    String contentLocation = att.getProperties().containsKey(0x3713001E) 
                            ? att.getPropertyString(0x3713001E) : att.getPropertyString(0x3713001F);
                    if (!contentLocation.isEmpty() && msg.getBodyHtml().contains(contentLocation)) {
                        return true;
                    }
                }
            } else if ((att.getProperties().containsKey(0x3716001F) && att.getPropertyString(0x3716001F).equalsIgnoreCase("inline"))
                    || (att.getProperties().containsKey(0x3716001E) && att.getPropertyString(0x3716001E).equalsIgnoreCase("inline"))) {
                return true;
            }
        } else if ((att.getProperties().containsKey(0x3716001F) && att.getPropertyString(0x3716001F).equalsIgnoreCase("inline"))
                || (att.getProperties().containsKey(0x3716001E) && att.getPropertyString(0x3716001E).equalsIgnoreCase("inline"))) {
            return true;
        }
        return false;
    } else if (msg.getBodyType() == BodyContentType.Rtf) {
        // Si el cuerpo es RTF, entonces todos los archivos adjuntos OLE son archivos adjuntos en línea.
        // Los archivos adjuntos OLE tienen 0x00000006 para el valor de la propiedad PidTagAttachMethod
        if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_METHOD)) {
            return att.getPropertyLong(MapiPropertyTag.PR_ATTACH_METHOD) == 0x00000006;
        }
        return false;
    } else
        throw new ArgumentOutOfRangeException();
}
~~~



Este fragmento de código utiliza la función isInlineAttachment() para evaluar archivos adjuntos.

**Java**

~~~java
String fileName = ("Sample.msg");
MapiMessage message = MapiMessage.fromFile(fileName);
MapiAttachmentCollection attachments = message.getAttachments();
for (int i = 0; i < attachments.size(); i++) {
    MapiAttachment attachment = (MapiAttachment) attachments.get(i);
    if (isInlineAttachment(attachment, message)) {
        System.out.println(attachment.getLongFileName() + " es archivo adjunto en línea");
    } else {
        System.out.println(attachment.getLongFileName() + " es archivo adjunto regular");
    }
}
~~~