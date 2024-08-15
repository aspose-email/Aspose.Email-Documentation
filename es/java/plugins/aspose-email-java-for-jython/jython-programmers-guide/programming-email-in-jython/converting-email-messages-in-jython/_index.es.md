---
title: "Conversión de mensajes de correo electrónico en Jython"
url: /es/java/converting-email-messages-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - Conversión de mensajes de correo electrónico**
Para convertir mensajes de correo electrónico mediante **Aspose.Email Java para Jython**, llama **convert_eml_to_msg** método de **Converter** módulo. Aquí puedes ver un ejemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import SaveOptions

class Converter:

    def __init__(self):



        # Loading EML, Saving to MSG

        self.convert_eml_to_msg()



    def convert_eml_to_msg(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/Converter/'



        # Initialize and Load an existing EML file by specifying the MessageFormat

        mailMessage = MailMessage()

        eml = mailMessage.load(dataDir + "Message.eml")

        # Save the Email message to disk in Unicode format

        saveOptions= SaveOptions

        eml.save(dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

        # Display Status

        print "Converted email to msg successfully."



if __name__ == '__main__':       

    Converter()

```
## **Descargar Running Code**
Download **Conversión de mensajes de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
