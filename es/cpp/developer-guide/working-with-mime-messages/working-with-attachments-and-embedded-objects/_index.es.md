---
title: "Trabajando con Adjuntos y Objetos Incrustados usando la Biblioteca C++ Email Parser"
description: "Puedes agregar y eliminar adjuntos de correos electrónicos, mostrar el nombre del archivo adjunto y trabajar con objetos incrustados utilizando la API de la Biblioteca C++ Email Parser."
url: /es/cpp/working-with-attachments-and-embedded-objects/
weight: 50
type: docs
linktitle: "Trabajando con Adjuntos y Objetos Incrustados"
---

## **Gestión de Adjunts de Correo Electrónico**
Un adjunto de correo electrónico es un archivo informático que se envía junto con un mensaje de correo electrónico. El archivo puede ser enviado como un mensaje separado así como parte del mensaje al que está adjunto. La clase Attachment se utiliza junto con la clase MailMessage. Todos los mensajes incluyen un cuerpo. Además del cuerpo, es posible que desees enviar archivos adicionales. Estos se envían como adjuntos y se representan como instancias de la clase Attachment. Puedes enviar cualquier número de adjuntos, pero el tamaño del adjunto está limitado por el servidor de correo. Gmail, por ejemplo, no admite tamaños de archivo mayores a 10MB.
{{% alert %}}
**¡Pruébalo!**

Agrega o elimina adjuntos de correos electrónicos con la gratuita [**Aspose.Email Editor App**](https://products.aspose.app/email/es/editor).
{{% /alert %}}
### **Agregando un Adjunto**
Para adjuntar un archivo a un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Crea una instancia de la clase Attachment.
1. Carga el adjunto en la instancia de Attachment.
1. Agrega la instancia de Attachment en la instancia de la clase MailMessage.

El siguiente fragmento de código muestra cómo agregar un adjunto a un correo electrónico.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-AddEmailAttachments-AddEmailAttachments.cpp" >}}

Arriba, describimos cómo agregar adjuntos a tu mensaje de correo electrónico con Aspose.Email. Lo que sigue muestra cómo eliminar adjuntos y mostrar información sobre ellos en pantalla.

### **Eliminando un Adjunto**
Para eliminar un adjunto, sigue los pasos indicados a continuación:

- Crea una instancia de la clase Attachment.
- Carga el adjunto en la instancia de la clase Attachment.
- Agrega el adjunto a la instancia de la clase MailMessage.
- Elimina los adjuntos de la instancia de la clase Attachment usando la instancia de la clase MailMessage.

El siguiente fragmento de código muestra cómo eliminar un adjunto.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-RemoveAttachments-RemoveAttachments.cpp" >}}

### **Mostrando el Nombre del Archivo Adjunto**
Para mostrar el nombre del archivo adjunto, sigue estos pasos:

1. Recorre los adjuntos en el mensaje de correo electrónico y
   1. Guarda cada adjunto.
   1. Muestra el nombre de cada adjunto en pantalla.

El siguiente fragmento de código muestra cómo mostrar el nombre de un archivo adjunto en la pantalla.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-DisplayAttachmentFileName-DisplayAttachmentFileName.cpp" >}}

### **Extracción de Adjunts de Correo Electrónico**
Este tema explica cómo extraer un adjunto de un archivo de correo electrónico. Un adjunto de correo electrónico es un archivo informático que se envía junto con un mensaje de correo electrónico. El archivo puede ser enviado como un mensaje separado así como parte del mensaje al que está adjunto. Todos los mensajes de correo electrónico incluyen un cuerpo. Además del cuerpo, es posible que desees enviar archivos adicionales. Estos se envían como adjuntos y se representan como instancias de la clase Attachment. La clase Attachment se utiliza con la clase MailMessage para trabajar con adjuntos. Para extraer adjuntos de un mensaje de correo electrónico, sigue estos pasos:

- Crea una instancia de la clase MailMessage.
- Carga un archivo de correo electrónico en la instancia de MailMessage.
- Crea una instancia de la clase Attachment y úsala en un bucle para extraer todos los adjuntos.
- Guarda el adjunto y muéstralo en pantalla.
- Especifica la dirección del remitente y del destinatario en la instancia de MailMessage.
- Los fragmentos de código extraen adjuntos de un correo electrónico.

|**Adjuntos extraídos en el correo**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
El siguiente fragmento de código muestra cómo extraer adjuntos de correo electrónico.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.cpp" >}}
#### **Recuperando la Descripción de Contenido del Adjunto**
La API de Aspose.Email proporciona la capacidad de leer la Descripción de Contenido del adjunto desde el encabezado del adjunto. El siguiente fragmento de código muestra cómo recuperar la descripción de contenido del adjunto.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-RetrieveContentDescriptionFromAttachment-RetrieveContentDescriptionFromAttachment.cpp" >}}
## **Trabajando con Objetos Incrustados**
Un objeto incrustado es un objeto que fue creado con una aplicación y encerrado dentro de un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel puede estar incrustada en un informe de Microsoft Word, o un archivo de video puede estar incrustado en una presentación de Microsoft PowerPoint. Cuando un archivo está incrustado, en lugar de insertarse o pegarse en otro documento, retiene su formato original. El documento incrustado puede ser abierto en la aplicación original y modificado.
### **Incrustando Objetos en un Correo**
La clase LinkedResources se utiliza con la clase MailMessage para incrustar objetos en tus mensajes de correo electrónico. Para agregar un objeto incrustado, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Especifica los valores de de, para y asunto en la instancia de MailMessage.
1. Crea una instancia de la clase AlternateView.
1. Crea una instancia de la clase LinkedResources.
1. Carga un objeto incrustado en la instancia de LinkedResources.
1. Agrega el objeto incrustado cargado en la instancia de la clase MailMessage.
1. Agrega la instancia de AlternateViews a la instancia de la clase MailMessage.

Los fragmentos de código a continuación producen un mensaje de correo electrónico con ambos cuerpos en texto claro y HTML, y una imagen incrustada en el HTML

|**Imagen incrustada en el correo**|
| :- |
|![todo:image_alt_text](/plugins/servlet/confluence/placeholder/unknown-attachment)|
Puedes enviar cualquier número de objetos incrustados. El tamaño del adjunto está limitado por el servidor de correo. Gmail, por ejemplo, no admite tamaños de archivo mayores a 10MB. Los fragmentos de código a continuación muestran cómo incrustar objetos en un correo.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-EmbeddedObjects-EmbeddedObjects.cpp" >}}
### **Extracción de Objetos Incrustados**
Este tema explica cómo extraer objetos incrustados de un archivo de correo electrónico. Un objeto incrustado es un objeto que fue creado con una aplicación y encerrado dentro de un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel puede estar incrustada en un informe de Microsoft Word, o un archivo de video puede estar incrustado en una presentación de Microsoft PowerPoint. Cuando un archivo está incrustado, en lugar de insertarse o pegarse en otro documento, retiene su formato original. El documento incrustado puede ser abierto en la aplicación original y modificado. Para extraer un objeto incrustado de un mensaje de correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Carga un archivo de correo electrónico en la instancia de MailMessage.
1. Crea un bucle y crea una instancia de la clase Attachment en él.
1. Guarda el adjunto y muéstralo en pantalla.
1. Especifica la dirección del remitente y del destinatario en la instancia de MailMessage.
1. El fragmento de código a continuación extrae objetos incrustados de un correo.

|**Objetos incrustados extraídos en el correo**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
El siguiente fragmento de código muestra cómo extraer objetos incrustados.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.cpp" >}}