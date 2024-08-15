---
title: "Crear un nuevo PST en Jython"
url: /es/java/create-new-pst-in-jython/
weight: 60
type: docs
---

## **Aspose.Email - Crear un nuevo PST**
Para crear un nuevo PST usando **Aspose.Email Java para Jython**, simplemente invoca **CreatePST** módulo. Aquí puedes ver un ejemplo de código.

**Código Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

from com.aspose.email import NoteColor

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

from java.util import Date

from java.util import Calendar

class CreatePST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST/'



        # Create an instance of PersonalStorage

        personalStorage=PersonalStorage()

        pst = personalStorage.create(dataDir + "sample1.pst", 0)

        # Create a folder at root of pst

        pst.getRootFolder().addSubFolder("myInbox")

        # Add message to newly created folder

        mapi_message = MapiMessage()

        pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(dataDir + "Message.msg"))

        print "Created PST successfully."





if __name__ == '__main__':       

    CreatePST()

```
## **Descargar Running Code**
Download **Crear un nuevo PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
