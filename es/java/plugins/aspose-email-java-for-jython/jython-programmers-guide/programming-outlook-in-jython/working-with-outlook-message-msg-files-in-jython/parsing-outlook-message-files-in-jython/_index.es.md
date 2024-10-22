---
title: "Analizando Archivos de Mensajes de Outlook en Jython"
url: /es/java/analizando-archivos-de-mensajes-de-outlook-en-jython/
weight: 30
type: docs
---

## **Aspose.Email - Analizando Archivos de Mensajes de Outlook**
Para analizar un archivo de mensaje de Outlook usando **Aspose.Email Java para Jython**, simplemente invoca el módulo **ParseOutlookMessageFile**. Aquí puedes ver un código de ejemplo.

**Código Jython**

```python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

class ParseOutlookMessageFile:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile/'



        mapiMessage=MapiMessage()

        outlook_message_file = mapiMessage.fromFile(dataDir + "Message.msg")

        # Mostrar el nombre del remitente

        print "Nombre del Remitente : " 

        print outlook_message_file.getSenderName()

        #Mostrar Asunto

        print "Asunto : " 

        print outlook_message_file.getSubject()

        # Mostrar Cuerpo

        print "Cuerpo : " 

        print outlook_message_file.getBody()





if __name__ == '__main__':        

    ParseOutlookMessageFile()

```
## **Descargar Código en Ejecución**
Descarga **Analizando Archivos de Mensajes de Outlook (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)