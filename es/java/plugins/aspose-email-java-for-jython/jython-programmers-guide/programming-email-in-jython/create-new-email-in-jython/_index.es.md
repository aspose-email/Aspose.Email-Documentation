---
title: "Crear Nuevo Correo Electrónico en Jython"
url: /es/java/crear-nuevo-correo-electronico-en-jython/
weight: 20
type: docs
---

## **Aspose.Email - Crear Nuevo Correo Electrónico**
Para crear un nuevo correo electrónico usando **Aspose.Email Java para Jython**, simplemente invoca el módulo **CreateNewEmail**. Aquí puedes ver el código de ejemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import MailMessageSaveType

class CreateNewEmail:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/CreateNewEmail/'



        # Crear una instancia de la clase MailMessage

        message = MailMessage()

        # Establecer el asunto del mensaje

        message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

        mail_address = MailAddress

        # Establecer el cuerpo en Html

        message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

            "<font color=blue>Esta línea está en color azul</font>")

        # Establecer información del remitente

        message.setFrom(MailAddress("from@domain.com", "Nombre del Remitente", False))

        # Agregar destinatarios TO

        message.getTo().add(MailAddress("to1@domain.com", "Destinatario 1", False))

        message.getTo().add(MailAddress("to2@domain.com", "Destinatario 2", False))

        # Agregar destinatarios CC

        message.getCC().add(MailAddress("cc1@domain.com", "Destinatario 3", False))

        message.getCC().add(MailAddress("cc2@domain.com", "Destinatario 4", False))

        # Guardar el mensaje en formatos EML y MSG

        mail_message_save_type = MailMessageSaveType()

        message.save(dataDir + "Message.eml", mail_message_save_type.getEmlFormat())

        message.save(dataDir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

        # Mostrar el estado

        print "Correo electrónico creado con éxito."



if __name__ == '__main__':        

    CreateNewEmail()

```
## **Descargar Código en Ejecución**
Descarga **Crear Nuevo Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)