---
title: "Extracción de encabezados de correo electrónico en Jython"
url: /es/java/extracting-email-headers-in-jython/
weight: 40
type: docs
---

## **Aspose.Email - Extracción de encabezados de correo electrónico**
Para extraer encabezados de correo electrónico usando **Aspose.Email Java para Jython**, simplemente invoca **ExtractEmailHeaders** módulo. Aquí puedes ver un ejemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

class ExtractEmailHeaders:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ExtractEmailHeaders/'



        # Initialize and Load an existing EML file by specifying the MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "Printing all Headers:"

        # Print out all the headers

        i=0

        while (i < message.getHeaders().getCount()):

            print message.getHeaders().get(i)

            i += 1





if __name__ == '__main__':       

    ExtractEmailHeaders()

```
## **Descargar Running Code**
Download **Extracción de encabezados de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
