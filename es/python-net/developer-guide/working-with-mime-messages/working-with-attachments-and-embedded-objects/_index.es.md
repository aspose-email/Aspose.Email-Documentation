---
title: "Trabajo con archivos adjuntos y objetos incrustados"
url: /es/python-net/working-with-attachments-and-embedded-objects/
weight: 50
type: docs
---


## **Administración de archivos adjuntos de correo electrónico**
Un archivo adjunto de correo electrónico es un archivo de computadora que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado, así como como una parte del mensaje al que está adjunto. La clase Attachment se usa con la clase MailMessage. Todos los mensajes incluyen un cuerpo. Además del cuerpo, es posible que desee enviar archivos adicionales. Se envían como archivos adjuntos y se representan como una instancia de la clase Attachment. Puede enviar cualquier cantidad de archivos adjuntos, pero el servidor de correo limita su tamaño. Gmail, por ejemplo, no admite archivos de más de 10 MB.
{{% alert %}}
**¡Pruébalo!**

Agregue o elimine archivos adjuntos de correo electrónico en línea con la versión gratuita [**Aplicación Aspose.Email Editor**](https://products.aspose.app/email/es/editor).
{{% /alert %}}
### **Agregar un archivo adjunto**
Para adjuntar un archivo adjunto a un correo electrónico, sigue estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Crea una instancia de la clase Attachment.
1. Carga el archivo adjunto en la instancia de Attachment.
1. Añade la instancia de Attachment a la instancia de la clase MailMessage.

El siguiente fragmento de código muestra cómo añadir un archivo adjunto a un correo electrónico.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AddEmailAttachments-AddEmailAttachments.py" >}}



Anteriormente, describimos cómo agregar archivos adjuntos a su mensaje de correo electrónico con Aspose.Email. A continuación se muestra cómo eliminar los archivos adjuntos y mostrar la información sobre ellos en la pantalla.
### **Eliminar un archivo adjunto**
Para eliminar un archivo adjunto, siga los pasos que se indican a continuación:

- Crea una instancia de la clase Attachment.
- Cargue el archivo adjunto en la instancia de la clase Attachment.
- Añade un archivo adjunto a la instancia de la clase MailMessage.
- Elimine los archivos adjuntos de la instancia de la clase Attachment mediante la instancia de la clase MailMessage.

En el siguiente fragmento de código se muestra cómo eliminar un archivo adjunto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RemovingAttachmentFromMailMessage-RemovingAttachmentFromMailMessage.py" >}}
### **Mostrar el nombre del archivo adjunto**
Para mostrar el nombre del archivo adjunto, sigue estos pasos:

1. Revisa los archivos adjuntos del mensaje de correo electrónico y
   1. Guarda cada archivo adjunto.
   1. Muestra el nombre de cada adjunto en la pantalla.

El siguiente fragmento de código muestra cómo mostrar el nombre de un archivo adjunto en la pantalla.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayAttachmentFileName-DisplayAttachmentFileName.py" >}}
### **Extraer archivos adjuntos de correo electrónico**
En este tema se explica cómo extraer un archivo adjunto de un archivo de correo electrónico. Un archivo adjunto de correo electrónico es un archivo de ordenador que se envía junto con un mensaje de correo electrónico. El archivo puede enviarse como un mensaje separado, así como como una parte del mensaje al que está adjunto. Todos los mensajes de correo electrónico incluyen un cuerpo. Además del cuerpo, es posible que desees enviar archivos adicionales. Se envían como archivos adjuntos y se representan como instancias de la clase Attachment. La clase Attachment se usa con la clase MailMessage para trabajar con los archivos adjuntos. Para extraer los archivos adjuntos de un mensaje de correo electrónico, sigue estos pasos:

- Crea una instancia de la clase MailMessage.
- Carga un archivo de correo electrónico en la instancia de MailMessage.
- Crea una instancia de la clase Attachment y úsala en bucle para extraer todos los adjuntos.
- Guarde el archivo adjunto y muéstrelo en la pantalla.
- Especifique la dirección del remitente y del destinatario en la instancia de MailMessage.
- Ahora puede enviar correos electrónicos con la clase SmtpClient.

Los fragmentos de código extraen los archivos adjuntos de un correo electrónico.

|**Archivos adjuntos extraídos en el correo electrónico**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_1.png)|
El siguiente fragmento de código muestra cómo extraer archivos adjuntos de correo electrónico.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}
#### **Recuperar la descripción del contenido del archivo adjunto**
La API Aspose.Email ofrece la capacidad de leer la descripción del contenido del adjunto desde el encabezado del archivo adjunto. El siguiente fragmento de código muestra cómo recuperar la descripción del contenido del archivo adjunto.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RetrievContentDescriptionFromAttachment-RetrievContentDescriptionFromAttachment.py" >}}
#### **Determinar si el archivo adjunto es un mensaje incrustado**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DetermineAttachmendEmbeddedMessage-DetermineAttachmendEmbeddedMessage.py" >}}
## **Trabajo con objetos incrustados**
Un objeto incrustado es un objeto que se creó con una aplicación y se incluyó en un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel se puede incrustar en un informe de Microsoft Word o se puede incrustar un archivo de vídeo en una presentación de Microsoft PowerPoint. Cuando un archivo se incrusta, en lugar de insertarlo o pegarlo en otro documento, conserva su formato original. El documento incrustado se puede abrir en la aplicación original y modificarlo.
### **Incrustar objetos en un correo electrónico**
Eliminar objetos incrustados del correo electrónico

La propiedad LinkedResourceCollection, a la que se accede mediante la propiedad MailMessage.LinkedResources, proporciona un método para eliminar por completo los objetos incrustados agregados a un mensaje de correo electrónico. Utilice la versión sobrecargada del método LinkedResourceCollection.removeAt para eliminar todos los rastros de un objeto incrustado de un mensaje de correo electrónico.

El código de ejemplo que aparece a continuación muestra cómo eliminar objetos incrustados de un mensaje de correo electrónico.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-RemoveLRTracesFromMessageBody-RemoveLRTracesFromMessageBody.py" >}}
### **Extracción de objetos incrustados**
En este tema se explica cómo extraer objetos incrustados de un archivo de correo electrónico. Un objeto incrustado es un objeto que se creó con una aplicación y se incluyó en un documento o archivo creado por otra aplicación. Por ejemplo, una hoja de cálculo de Microsoft Excel se puede incrustar en un informe de Microsoft Word o se puede incrustar un archivo de vídeo en una presentación de Microsoft PowerPoint. Cuando un archivo se incrusta, en lugar de insertarlo o pegarlo en otro documento, conserva su formato original. El documento incrustado se puede abrir en la aplicación original y modificarlo. Para extraer un objeto incrustado de un mensaje de correo electrónico, siga estos pasos:

1. Crea una instancia de la clase MailMessage.
1. Carga un archivo de correo electrónico en la instancia de MailMessage.
1. Crea un bucle y crea una instancia de la clase Attachment en él.
1. Guarde el archivo adjunto y muéstrelo en la pantalla.
1. Especifique la dirección del remitente y del destinatario en la instancia de MailMessage.
1. Envía correos electrónicos mediante la clase SmtpClient.

El siguiente fragmento de código extrae los objetos incrustados de un correo electrónico.

|**Objetos incrustados extraídos en el correo electrónico**|
|: - |
|![todo:image_alt_text](working-with-attachments-and-embedded-objects_2.png)|
El siguiente fragmento de código muestra cómo extraer objetos incrustados.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractEmbeddedObjectsFromEmail-ExtractEmbeddedObjectsFromEmail.py" >}}