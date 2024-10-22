---
title: "Trabajando con Archivos Adjuntos y Objetos Embebidos"
url: /es/python-net/trabajando-con-archivos-adjuntos-y-objetos-emebidos/
weight: 50
type: docs
---

## **Administrando Archivos Adjuntos de Email**
Un archivo adjunto de email es un archivo informático que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado además de como parte del mensaje al que está adjunto. La clase Attachment se utiliza con la clase MailMessage. Todos los mensajes incluyen un cuerpo. Además del cuerpo, puede que desee enviar archivos adicionales. Estos se envían como archivos adjuntos y se representan como instancias de la clase Attachment. Puede enviar cualquier número de archivos adjuntos, pero el tamaño del archivo adjunto está limitado por el servidor de correo. Gmail, por ejemplo, no admite tamaños de archivos superiores a 10 MB.
{{% alert %}}
**¡Pruébalo!**

Agrega o elimina archivos adjuntos de correo electrónico en línea con la gratuita [**Aplicación de Editor de Aspose.Email**](https://products.aspose.app/email/es/editor).
{{% /alert %}}
### **Añadiendo un Archivo Adjunto**
Para adjuntar un archivo a un correo electrónico, siga estos pasos:

1. Cree una instancia de la clase MailMessage.
1. Cree una instancia de la clase Attachment.
1. Cargue el archivo adjunto en la instancia de Attachment.
1. Agregue la instancia de Attachment a la instancia de MailMessage.

El siguiente fragmento de código le muestra cómo agregar un archivo adjunto a un correo electrónico.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AddEmailAttachments-AddEmailAttachments.py" >}}

Arriba, describimos cómo agregar archivos adjuntos a su mensaje de correo electrónico con Aspose.Email. Lo que sigue muestra cómo eliminar archivos adjuntos y mostrar información sobre ellos en la pantalla.
### **Eliminando un Archivo Adjunto**
Para eliminar un archivo adjunto, siga los pasos que se indican a continuación:

- Cree una instancia de la clase Attachment.
- Cargue el archivo adjunto en la instancia de la clase Attachment.
- Agregue el archivo adjunto a la instancia de la clase MailMessage.
- Elimine los archivos adjuntos de la instancia de la clase Attachment utilizando la instancia de la clase MailMessage.

El siguiente fragmento de código le muestra cómo eliminar un archivo adjunto.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RemovingAttachmentFromMailMessage-RemovingAttachmentFromMailMessage.py" >}}
### **Mostrando el Nombre del Archivo Adjunto**
Para mostrar el nombre del archivo adjunto, siga estos pasos:

1. Recorra los archivos adjuntos en el mensaje de correo electrónico y
   1. Guarde cada archivo adjunto.
   1. Muestre el nombre de cada archivo adjunto en la pantalla.

El siguiente fragmento de código le muestra cómo mostrar el nombre de un archivo adjunto en la pantalla.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayAttachmentFileName-DisplayAttachmentFileName.py" >}}
### **Extrayendo Archivos Adjuntos de Email**
Este tema explica cómo extraer un archivo adjunto de un archivo de correo electrónico. Un archivo adjunto de correo electrónico es un archivo informático que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado además de como parte del mensaje al que está adjunto. Todos los mensajes de correo electrónico incluyen un cuerpo. Así como el cuerpo, puede que desee enviar archivos adicionales. Estos se envían como archivos adjuntos y se representan como instancias de la clase Attachment. La clase Attachment se utiliza con la clase MailMessage para trabajar con archivos adjuntos. Para extraer archivos adjuntos de un mensaje de correo electrónico, siga estos pasos:

- Cree una instancia de la clase MailMessage.
- Cargue un archivo de correo electrónico en la instancia de MailMessage.
- Cree una instancia de la clase Attachment y úselas en un bucle para extraer todos los archivos adjuntos.
- Guarde el archivo adjunto y muéstrelo en la pantalla.
- Especifique la dirección del remitente y el destinatario en la instancia de MailMessage.
- Ahora puede enviar correos electrónicos utilizando la clase SmtpClient.

Los fragmentos de código extraen archivos adjuntos de un correo electrónico.

|**Archivos adjuntos extraídos en el correo electrónico**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
El siguiente fragmento de código muestra cómo extraer archivos adjuntos de correo electrónico.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}
#### **Recuperando Content-Description del Archivo Adjunto**
La API de Aspose.Email proporciona la capacidad de leer la Content-Description del archivo adjunto desde el encabezado del archivo adjunto. El siguiente fragmento de código le muestra cómo recuperar la descripción de contenido del archivo adjunto.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RetrievContentDescriptionFromAttachment-RetrievContentDescriptionFromAttachment.py" >}}
#### **Determinando si el Archivo Adjunto es un Mensaje Embebido**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DetermineAttachmendEmbeddedMessage-DetermineAttachmendEmbeddedMessage.py" >}}
## **Trabajando con Objetos Embebidos**
Un objeto embebido es un objeto que fue creado con una aplicación y se encuentra encerrado dentro de un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel puede ser embebida en un informe de Microsoft Word, o un archivo de video puede ser embebido en una presentación de Microsoft PowerPoint. Cuando un archivo es embebido, en lugar de ser insertado o pegado en otro documento, conserva su formato original. El documento embebido puede abrirse en la aplicación original y modificarse.
### **Embedded Objects en un Email**
Eliminando Objetos Embebidos de Email

LinkedResourceCollection, accesible a través de la propiedad MailMessage.LinkedResources, proporciona un método para eliminar completamente los objetos embebidos añadidos a un mensaje de correo electrónico. Use la versión sobrecargada del método LinkedResourceCollection.RemoveAt para eliminar todos los rastros de un objeto embebido de un mensaje de correo electrónico.

El siguiente código de muestra muestra cómo eliminar objetos embebidos de un mensaje de correo electrónico.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RemoveLRTracesFromMessageBody-RemoveLRTracesFromMessageBody.py" >}}
### **Extrayendo Objetos Embebidos**
Este tema explica cómo extraer objetos embebidos de un archivo de correo electrónico. Un objeto embebido es un objeto que fue creado con una aplicación y se encuentra encerrado dentro de un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel puede ser embebida en un informe de Microsoft Word, o un archivo de video puede ser embebido en una presentación de Microsoft PowerPoint. Cuando un archivo es embebido, en lugar de ser insertado o pegado en otro documento, conserva su formato original. El documento embebido puede abrirse en la aplicación original y modificarse. Para extraer un objeto embebido de un mensaje de correo electrónico, siga estos pasos:

1. Cree una instancia de la clase MailMessage.
1. Cargue un archivo de correo electrónico en la instancia de MailMessage.
1. Cree un bucle y cree una instancia de la clase Attachment en él.
1. Guarde el archivo adjunto y muéstrelo en la pantalla.
1. Especifique la dirección del remitente y el destinatario en la instancia de MailMessage.
1. Envíe un correo electrónico utilizando la clase SmtpClient.

El siguiente fragmento de código extrae objetos embebidos de un correo electrónico.

|**Objetos embebidos extraídos en el correo electrónico**|
| :- |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
El siguiente fragmento de código muestra cómo extraer objetos embebidos.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}