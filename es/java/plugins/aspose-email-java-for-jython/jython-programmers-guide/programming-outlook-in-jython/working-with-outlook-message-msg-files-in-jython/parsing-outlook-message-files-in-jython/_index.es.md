---
title: "Análisis de archivos de mensajes de Outlook en Jython"
url: /es/java/parsing-outlook-message-files-in-jython/
weight: 30
type: docs
---

## **Aspose.Email - Análisis de archivos de mensajes de Outlook**
Para analizar el archivo de mensajes de Outlook usando **Aspose.Email Java para Jython**, simplemente invoca **ParseOutlookMessageFile** módulo. Aquí puedes ver un ejemplo de código.

**Código Jython**

```python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

class ParseOutlookMessageFile:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile/'



        mapiMessage=MapiMessage()

        outlook_message_file = mapiMessage.fromFile(dataDir + "Message.msg")

        # Display sender's name

        print "Sender Name : "

        print outlook_message_file.getSenderName()

        #Display Subject

        print "Subject : "

        print outlook_message_file.getSubject()

        # Display Body

        print "Body : "

        print outlook_message_file.getBody()





if __name__ == '__main__':       

    ParseOutlookMessageFile()

```
## **Descargar Running Code**
Download **Análisis de archivos de mensajes de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
