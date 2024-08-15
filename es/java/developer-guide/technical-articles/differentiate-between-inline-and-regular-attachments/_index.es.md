---
title: "Diferenciar entre archivos adjuntos en línea y regulares"
url: /es/java/differentiate-between-inline-and-regular-attachments/
weight: 10
type: docs
---

{{% alert color="primary" %}}

Los mensajes de correo electrónico pueden contener imágenes en línea y archivos adjuntos. Utilizando [MailMessage](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailMessage), los archivos adjuntos en línea se pueden extraer del [LinkedResourceCollection](https://apireference.aspose.com/email//java/com.aspose.email/linkedresourcecollection) colección, mientras que se puede acceder a los archivos adjuntos normales y extraerlos con un mensaje [AttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/attachmentcollection) colección. Sin embargo, esto es diferente cuando el mensaje se carga usando [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage), ya que el usuario puede acceder a todas las imágenes en línea y los archivos adjuntos normales en el mismo [MapiAttachmentCollection](https://apireference.aspose.com/email//java/com.aspose.email/mapiattachmentcollection). Por lo tanto, es un método que puede diferenciar entre un archivo adjunto en línea y uno normal cuando [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) se usa si es necesario.

{{% /alert %}}

Este artículo explica cómo diferenciar los archivos adjuntos en línea de los normales mediante [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage). A la hora de decidir, el tipo de cuerpo de [MapiMessage](https://apireference.aspose.com/email//java/com.aspose.email/mapimessage) se tiene en cuenta de la siguiente manera:

- **Cuerpo de texto plano**: No es necesario comprobar los mensajes de correo electrónico con texto plano como texto principal, ya que todos los archivos adjuntos de dichos mensajes son siempre archivos adjuntos normales.
- **Cuerpo HTML**: Para los mensajes con un cuerpo HTML, el archivo adjunto no solo debe contener la propiedad PR_ATTACH_FLAGS (0x37140003), sino que su valor debe ser igual a 0x00000004 para los archivos adjuntos en línea. Si se cumple esta condición, la naturaleza del archivo adjunto dependerá además de las etiquetas PR_ATTACH_CONTENT_LOCATION y PR_ATTACH_CONTENT_ID. Sin embargo, en ausencia de la etiqueta MAPI PR_ATTACH_FLAGS, se comprueba la propiedad PR_ATTACH_DISPOSITION (0x3716001F o 0x3716001E) del adjunto para determinar el tipo de adjunto.
- **Cuerpo RTF**: Si el cuerpo es RTF, todos los adjuntos OLE son adjuntos en línea. El valor de PR_ATTACH_METHOD para todos los archivos adjuntos OLE es igual a 0x00000006.

El siguiente ejemplo de código demuestra cómo diferenciar mediante programación entre los archivos adjuntos en línea y los archivos adjuntos normales. La función isInlineAttachment toma un archivo adjunto y mapiMessage como parámetros de entrada y devuelve el valor true si el archivo adjunto es un archivo adjunto en línea.

~~~java
public static boolean isInlineAttachment(MapiAttachment att, MapiMessage msg) {
    if (msg.getBodyType() == BodyContentType.PlainText)
        // ignore indications for plain text messages
        return false;
    else if (msg.getBodyType() == BodyContentType.Html) {
        // check the PidTagAttachFlags property
        if (att.getProperties().containsKey(0x37140003)) {
            Long attachFlagsValue = att.getPropertyLong(0x37140003);
            if (attachFlagsValue != null && (attachFlagsValue > 3 || attachFlagsValue < 1)) {
                // check PidTagAttachContentId property
                if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                        || att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W)) {
                    String contentId = att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            ? att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID)
                            : att.getPropertyString(MapiPropertyTag.PR_ATTACH_CONTENT_ID_W);
                    if (!contentId.isEmpty() && msg.getBodyHtml().contains(contentId)) {
                        return true;
                    }
                }
                // check PidTagAttachContentLocation property
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
        // If the body is RTF, then all OLE attachments are inline attachments.
        // OLE attachments have 0x00000006 for the value of the PidTagAttachMethod property
        if (att.getProperties().containsKey(MapiPropertyTag.PR_ATTACH_METHOD)) {
            return att.getPropertyLong(MapiPropertyTag.PR_ATTACH_METHOD) == 0x00000006;
        }
        return false;
    } else
        throw new ArgumentOutOfRangeException();
}
~~~



Este fragmento de código usa la función isInlineAttachment () para evaluar los archivos adjuntos.

**Java**

~~~java
String fileName = ("Sample.msg");
MapiMessage message = MapiMessage.fromFile(fileName);
MapiAttachmentCollection attachments = message.getAttachments();
for (int i = 0; i < attachments.size(); i++) {
    MapiAttachment attachment = (MapiAttachment) attachments.get(i);
    if (isInlineAttachment(attachment, message)) {
        System.out.println(attachment.getLongFileName() + " is inline attachment");
    } else {
        System.out.println(attachment.getLongFileName() + " is regular attachment");
    }
}
~~~
