---
title: "Diferenciar entre archivos adjuntos en línea y archivos adjuntos normales"
url: /es/net/differentiating-between-inline-and-regular-attachments/
weight: 200
type: docs
---


Es habitual que un mensaje de correo electrónico contenga imágenes en línea en su cuerpo, así como archivos adjuntos normales asociados a él. Utilizando [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage) clase, los archivos adjuntos en línea se pueden extraer del [LinkedResourceCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/linkedresources) clase, mientras que se puede acceder/extraer los archivos adjuntos normales con el [AttachmentCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/attachments) clase de mensaje. Sin embargo, esto es diferente cuando el mensaje se carga con la clase Aspose.Email.MapiMessage, ya que el usuario de la misma clase MAPIAttachmentCollection puede acceder a todas las imágenes en línea y los archivos adjuntos normales. Por lo tanto, es necesario diseñar un método que pueda diferenciar entre un archivo adjunto en línea y uno normal cuando se usa MAPIessage.
## **Uso de Aspose.Email para diferenciar entre archivos adjuntos en línea y regulares**
Este artículo explica cómo diferenciar los archivos adjuntos en línea de los normales mediante MAPIMessage. Para determinar esta diferenciación, se tiene en cuenta el tipo de cuerpo de MapiMessage de la siguiente manera:

**Cuerpo de texto sin formato:**  No es necesario comprobar los mensajes de correo electrónico con texto plano como texto principal, ya que todos los archivos adjuntos de dichos mensajes son siempre archivos adjuntos normales.

**Cuerpo HTML:** En el caso de un mensaje con el tipo de cuerpo HTML, el adjunto no solo debe contener la propiedad PR_ATTACH_FLAGS (0x37140003), sino que su valor debe ser igual a 0x00000004 para los archivos adjuntos en línea. Si se cumple esta condición, la naturaleza del archivo adjunto dependerá además de las etiquetas PR_ATTACH_CONTENT_LOCATION y PR_ATTACH_CONTENT_ID. Sin embargo, en ausencia de la etiqueta Mapi PR_ATTACH_FLAGS, se comprueba la propiedad PR_ATTACH_DISPOSITION (0x3716001F o 0x3716001E) del adjunto para determinar el tipo de archivo adjunto.

**Cuerpo Rtf:** Si el cuerpo es RTF, todos los adjuntos OLE son adjuntos en línea. El valor de PR_ATTACH_METHOD para todos los archivos adjuntos OLE es igual a 0x00000006.

El siguiente ejemplo de código demuestra cómo diferenciar mediante programación entre los archivos adjuntos en línea y los archivos adjuntos normales. La función isInlineAttachment toma un archivo adjunto y un Message BodyType como parámetros de entrada y devuelve el valor true si el archivo adjunto es un archivo adjunto en línea.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-IdentifyInlineAndRegularAttachments-IdentifyInlineAndRegularAttachments.cs" >}}
