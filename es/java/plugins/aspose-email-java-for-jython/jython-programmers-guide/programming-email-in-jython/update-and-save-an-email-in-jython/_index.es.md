---
title: "Actualizar y Guardar un Correo Electrónico en Jython"
url: /es/java/update-and-save-an-email-in-jython/
weight: 70
type: docs
---

## **Aspose.Email - Actualizar y Guardar un Correo Electrónico**
Para Actualizar y Guardar un Correo Electrónico utilizando **Aspose.Email Java para Jython**, simplemente invoca el módulo **UpdateEmail**. Aquí puedes ver un código de ejemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddressCollection

from com.aspose.email import MailMessageSaveType

class UpdateEmail:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/UpdateEmail/'



        # Inicializar y cargar un archivo MSG existente especificando el MessageFormat

        mailMessage=MailMessage()

        email = mailMessage.load(dataDir + "Message.msg")

        # Inicializar una variable String para obtener el Asunto del Correo

        subject = email.getSubject()

        # Agregar más información al Asunto

        subject = subject + " Este texto se agrega al asunto existente"

        # Establecer el Asunto del Correo

        email.setSubject('Este texto se agrega al asunto existente')

        # Inicializar una variable String para obtener el Cuerpo HTML del Correo

        body = email.getHtmlBody()

        # Agregar más información a la variable Cuerpo

        body = body + "<br> Este texto se agrega al cuerpo existente"

        # Establecer el Cuerpo del Correo

        email.setHtmlBody(body)

        # Inicializar el objeto MailAddressCollection

        contacts = MailAddressCollection()

        # Recuperar la lista TO del Correo

        contacts = email.getTo()

        # Agregar otra dirección de correo electrónico a la colección

        contacts.add("to1@domain.com")

        # Establecer la colección como la lista TO del Correo

        email.setTo(contacts)

        # Inicializar MailAddressCollection

        contacts = MailAddressCollection()

        # Recuperar la lista CC del Correo

        contacts = email.getCC()

        # Agregar otra dirección de correo electrónico a la colección

        contacts.add("cc2@domain.com")

        # Establecer la colección como la lista CC del Correo

        email.setCC(contacts)

        # Guardar el mensaje del Correo en disco especificando el MessageFormat

        mailMessageSaveType=MailMessageSaveType

        email.save(dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

        # Mostrar Estado

        print "Mensaje de correo electrónico actualizado con éxito."

if __name__ == '__main__':        

    UpdateEmail()

```
## **Descargar Código en Ejecución**
Descargar **Actualizar y Guardar un Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)