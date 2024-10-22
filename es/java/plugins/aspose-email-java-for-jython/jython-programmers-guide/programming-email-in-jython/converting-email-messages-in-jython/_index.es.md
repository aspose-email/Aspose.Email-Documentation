---
title: "Conversión de Mensajes de Correo en Jython"
url: /es/java/converting-email-messages-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - Conversión de Mensajes de Correo**
Para convertir mensajes de correo utilizando **Aspose.Email Java para Jython**, llama al método **convert_eml_to_msg** del módulo **Converter**. Aquí puedes ver un código de ejemplo.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import SaveOptions

class Converter:

    def __init__(self):

        # Cargando EML, guardando en MSG

        self.convert_eml_to_msg()

    def convert_eml_to_msg(dataDir):

        dataDir = Settings.dataDir + 'ProgrammingEmail/Converter/'

        # Inicializar y cargar un archivo EML existente especificando el MessageFormat

        mailMessage = MailMessage()

        eml = mailMessage.load(dataDir + "Message.eml")

        # Guardar el mensaje de correo en disco en formato Unicode

        saveOptions= SaveOptions

        eml.save(dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

        # Mostrar estado

        print "Correo convertido a msg con éxito."

if __name__ == '__main__':        

    Converter()

```
## **Descargar Código en Ejecución**
Descarga **Conversión de Mensajes de Correo (Aspose.Email)** de cualquiera de los siguientes sitios de codificación social mencionados:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)