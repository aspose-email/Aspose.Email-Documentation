---
title: "Extracción de Cabeceras de Correo Electrónico en Jython"
url: /es/java/extracting-email-headers-in-jython/
weight: 40
type: docs
---

## **Aspose.Email - Extracción de Cabeceras de Correo Electrónico**
Para extraer cabeceras de correo electrónico usando **Aspose.Email Java para Jython**, simplemente invoca el módulo **ExtractEmailHeaders**. Aquí puedes ver un código de ejemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

class ExtractEmailHeaders:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ExtractEmailHeaders/'



        # Inicializa y carga un archivo EML existente especificando el MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "Imprimiendo todas las cabeceras:"

        # Imprime todas las cabeceras

        i=0

        while (i < message.getHeaders().getCount()):

            print message.getHeaders().get(i)

            i += 1





if __name__ == '__main__':        

    ExtractEmailHeaders()

```
## **Descargar Código en Ejecución**
Descarga **Extracción de Cabeceras de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)