---
title: "Gestionar Archivos Adjuntos en el Mensaje de Correo en Jython"
url: /es/java/manage-attachments-in-email-message-in-jython/
weight: 50
type: docs
---

## **Aspose.Email - Gestionar Archivos Adjuntos en el Mensaje de Correo**
Para agregar archivos adjuntos a un nuevo mensaje de correo utilizando **Aspose.Email Java para Jython**, llama al método **add_attachments** del módulo **ManageAttachments**. Aquí puedes ver un ejemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import Attachment

from com.aspose.email import MessageFormat

class ManageAttachments:

    def __init__(self):



        self.add_attachments()



    def add_attachments(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ManageAttachments/'



        # Crear una instancia de la clase MailMessage

        message =MailMessage()

        # Establecer el asunto del mensaje

        message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

        mail_address = MailAddress

        # Establecer el cuerpo en Html

        message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

            "<font color=blue>Esta línea está en color azul</font>")

        # Establecer la información del remitente

        message.setFrom(MailAddress("from@domain.com", "Nombre del Remitente", False))

        # Añadir destinatarios TO

        message.getTo().add(MailAddress("to1@domain.com", "Destinatario 1", False))

        # Añadiendo archivo adjunto

        # Cargar un archivo adjunto

        attachment = Attachment(dataDir + "1.txt")

        # Añadir archivo adjunto en la instancia de la clase MailMessage

        message.addAttachment(attachment)

        # Guardar mensaje en disco

        messageFormat=MessageFormat()

        message.save(dataDir + "Add-Attachment.msg", messageFormat.getMsg())

        # Mostrar Estado

        print "Archivo adjunto añadido con éxito."





if __name__ == '__main__':        

    ManageAttachments()

```
## **Descargar Código en Ejecución**
Descargar **Gestionar Archivos Adjuntos en el Mensaje de Correo (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)