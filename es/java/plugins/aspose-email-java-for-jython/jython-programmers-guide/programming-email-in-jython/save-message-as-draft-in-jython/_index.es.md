---
title: "Guardar mensaje como borrador en Jython"
url: /es/java/save-message-as-draft-in-jython/
weight: 60
type: docs
---

## **Aspose.Email - Guardar mensaje como borrador**
Para guardar un mensaje como borrador usando **Aspose.Email Java para Jython**, simplemente invoca el módulo **SaveMessageAsDraft**. Aquí puedes ver un código de ejemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import MapiMessage

from com.aspose.email import MapiMessageFlags

class SaveMessageAsDraft:

    def __init__(self):

        dataDir = Settings.dataDir + 'ProgrammingEmail/SaveMessageAsDraft/'

        # Crear una instancia de la clase MailMessage

        message = MailMessage()

            # Establecer el asunto del mensaje

        message.setSubject("Nuevo mensaje creado por Aspose.Email para Java")

        mail_address = MailAddress

        # Establecer el cuerpo en Html

        message.setHtmlBody("<b>Esta línea está en negrita.</b> <br/> <br/>" +

            "<font color=blue>Esta línea está en color azul</font>")

        # Establecer la información del remitente

        message.setFrom(MailAddress("from@domain.com", "Nombre del Remitente", False))

        # Agregar destinatarios

        message.getTo().add(MailAddress("to1@domain.com", "Destinatario 1", False))

        message.getTo().add(MailAddress("to2@domain.com", "Destinatario 2", False))

        # Crear una instancia de MapiMessage y cargar la instancia de MailMessage en ella

        mapiMessage=MapiMessage()

        mapi_msg = mapiMessage.fromMailMessage(message)

        # Establecer las MapiMessageFlags como UNSENT y FROMME

        mapi_message_flags = MapiMessageFlags()

        # Guardar el MapiMessage en disco

        mapi_msg.save(dataDir + "New-Draft.msg")

        # Mostrar estado

        print "Borrador guardado con éxito."

if __name__ == '__main__':        

    SaveMessageAsDraft()

```
## **Descargar el código en ejecución**
Descarga **Guardar mensaje como borrador (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)