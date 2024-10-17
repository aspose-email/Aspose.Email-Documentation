---
title: "Mostrando Información del Correo Electrónico en Pantalla en Jython"
url: /es/java/mostrando-informacion-del-correo-electronico-en-pantalla-en-jython/
weight: 30
type: docs
---

## **Aspose.Email - Mostrando Información del Correo Electrónico**
Para Mostrar la Información del Correo Electrónico usando **Aspose.Email Java para Jython**, simplemente invoca el módulo **GetEmailInfo**. Aquí puedes ver un código de ejemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MessageFormat

class GetEmailInfo:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/GetEmailInfo/'



        # Crear una instancia de MailMessage cargando un archivo Eml

        message_format = MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "De: " 

        print message.getFrom()

        print "Para: " 

        print message.getTo()

        print "Asunto: " 

        print message.getSubject()

        print "CuerpoHtml: " 

        print message.getHtmlBody()

        print "CuerpoTexto: " 

        print message.getTextBody()





if __name__ == '__main__':        

    GetEmailInfo()

```
## **Descargar Código en Ejecución**
Descarga **Mostrando Información del Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)