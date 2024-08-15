---
title: "Mostrar información de correo electrónico en la pantalla en Jython"
url: /es/java/displaying-email-information-on-screen-in-jython/
weight: 30
type: docs
---

## **Aspose.Email - Mostrar información de correo electrónico**
Para mostrar información de correo electrónico mediante **Aspose.Email Java para Jython**, simplemente invoca **GetEmailInfo** módulo. Aquí puedes ver un ejemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MessageFormat

class GetEmailInfo:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/GetEmailInfo/'



        # Create MailMessage instance by loading an Eml file

        message_format = MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "From: "

        print message.getFrom()

        print "To: "

        print message.getTo()

        print "Subject: "

        print message.getSubject()

        print "HtmlBody: "

        print message.getHtmlBody()

        print "TextBody: "

        print message.getTextBody()





if __name__ == '__main__':       

    GetEmailInfo()

```
## **Descargar Running Code**
Download **Mostrar información de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
