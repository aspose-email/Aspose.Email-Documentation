---
title: "Crear nuevo PST en Jython"
url: /es/java/crear-nuevo-pst-en-jython/
weight: 60
type: docs
---

## **Aspose.Email - Crear nuevo PST**
Para crear un nuevo PST utilizando **Aspose.Email Java para Jython**, simplemente invoque el módulo **CreatePST**. Aquí puede ver el código de ejemplo.

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



        # Crear una instancia de PersonalStorage

        personalStorage=PersonalStorage()

        pst = personalStorage.create(dataDir + "sample1.pst", 0)

        # Crear una carpeta en la raíz del pst

        pst.getRootFolder().addSubFolder("miBandejaDeEntrada")

        # Agregar mensaje a la carpeta recién creada

        mapi_message = MapiMessage()

        pst.getRootFolder().getSubFolder("miBandejaDeEntrada").addMessage(mapi_message.fromFile(dataDir + "Message.msg"))

        print "PST creado exitosamente."





if __name__ == '__main__':        

    CreatePST()

```
## **Descargar código en ejecución**
Descargue **Crear nuevo PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)