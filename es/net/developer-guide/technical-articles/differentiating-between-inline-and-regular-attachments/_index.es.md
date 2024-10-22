---
title: "Distinguiendo entre Archivos Adjuntos En Línea y Regulares"
url: /es/net/differentiating-between-inline-and-regular-attachments/
weight: 200
type: docs
---

Es un escenario común cuando un mensaje de correo electrónico puede contener imágenes en línea dentro de su cuerpo, así como archivos adjuntos regulares asociados a él. Utilizando la clase [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage), los archivos adjuntos en línea pueden ser extraídos de la clase [LinkedResourceCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/linkedresources), mientras que los archivos adjuntos regulares pueden ser accedidos/extrados con la clase [AttachmentCollection](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/attachments) de un mensaje. Sin embargo, esto es diferente cuando el mensaje se carga utilizando la clase Aspose.Email.Mapi.MapiMessage, ya que todas las imágenes en línea y los archivos adjuntos regulares son accesibles para el usuario en la misma clase MapiAttachmentCollection. Por lo tanto, es necesario idear un método que pueda diferenciar entre un archivo adjunto en línea y uno regular cuando se utiliza MapiMessage.
## **Uso de Aspose.Email para Distinguir entre Archivos Adjuntos En Línea y Regulares**
Este artículo explica cómo diferenciar los archivos adjuntos en línea de los regulares utilizando MapiMessage. Para determinar esta diferenciación, se tiene en cuenta el tipo de cuerpo de MapiMessage de la siguiente manera:

**Cuerpo de Texto Plano:** Los mensajes de correo electrónico con tipo de cuerpo de texto plano no necesitan ser verificados, ya que todos los archivos adjuntos en tales mensajes son siempre archivos adjuntos regulares.

**Cuerpo Html:** En el caso de un mensaje con tipo de cuerpo HTML, el archivo adjunto no solo debe contener la propiedad PR_ATTACH_FLAGS (0x37140003), sino que su valor también debe ser igual a 0x00000004 para los archivos adjuntos en línea. Si se cumple esta condición, entonces depende además de las etiquetas PR_ATTACH_CONTENT_LOCATION y PR_ATTACH_CONTENT_ID para determinar la naturaleza del archivo adjunto. Sin embargo, en ausencia de la etiqueta Mapi PR_ATTACH_FLAGS, se verifica el archivo adjunto para la propiedad PR_ATTACH_DISPOSITION (0x3716001F o 0x3716001E) para determinar el tipo de archivo adjunto.

**Cuerpo Rtf:** Si el cuerpo es RTF, entonces todos los archivos adjuntos OLE son archivos adjuntos en línea. El valor de PR_ATTACH_METHOD para todos los archivos adjuntos OLE es igual a 0x00000006.

El siguiente ejemplo de código demuestra cómo diferenciar programáticamente entre archivos adjuntos en línea y regulares. La función IsInlineAttachment toma un archivo adjunto y el tipo de cuerpo del mensaje como parámetros de entrada y devuelve verdadero si el archivo adjunto es un archivo adjunto en línea.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-IdentifyInlineAndRegularAttachments-IdentifyInlineAndRegularAttachments.cs" >}}