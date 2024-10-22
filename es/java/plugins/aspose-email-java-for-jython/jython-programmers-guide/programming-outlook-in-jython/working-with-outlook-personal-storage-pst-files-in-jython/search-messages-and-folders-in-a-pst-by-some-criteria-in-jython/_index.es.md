---
title: "Buscar mensajes y carpetas en un PST según algunos criterios en Jython"
url: /es/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-jython/
weight: 70
type: docs
---

## **Aspose.Email - Buscar mensajes y carpetas en un PST**
Para buscar mensajes y carpetas en un PST utilizando **Aspose.Email Java para Jython**, simplemente invoca el módulo **SearchMessagesAndFoldersInPST**. Aquí puedes ver un ejemplo de código.

**Código Jython**

```python
 from aspose-email import Settings

from com.aspose.email import PersonalStorage

from com.aspose.email import PersonalStorageQueryBuilder

from com.aspose.email import MapiImportance

from com.aspose.email import MapiMessageFlags

class SearchMessagesAndFoldersInPST:

    def __init__(self):

        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST/'

        # Cargar el archivo PST de Outlook

        personalStorage=PersonalStorage()

        pst = personalStorage.fromFile(dataDir + "sample1.pst")

        folder = pst.getRootFolder().getSubFolder("myInbox")

        builder = PersonalStorageQueryBuilder()

            # Mensajes de alta importancia

        mapiImportance=MapiImportance

        builder.getImportance().equals(mapiImportance.High)

        messages = folder.getContents(builder.getQuery())

        print "Mensajes con alta imp:"

        print messages.size()

        #builder = PersonalStorageQueryBuilder()

        builder.getMessageClass().equals("IPM.Note")

        messages = folder.getContents(builder.getQuery())

        print "Mensajes con IPM.Note:"

        print messages.size()

        # Mensajes con adjuntos Y alta importancia

        builder.getImportance().equals(mapiImportance.High)

        mapiMessageFlags=MapiMessageFlags

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Mensajes con adjuntos:"

        print messages.size()

        # Mensajes con tamaño > 15 KB

        builder.getMessageSize().greater(15000)

        messages = folder.getContents(builder.getQuery())

        print "Mensajes tamaño > 15Kb:"

        print messages.size()

        # Mensajes no leídos

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        messages = folder.getContents(builder.getQuery())

        print "No leídos:"

        print messages.size()

        # Mensajes no leídos con adjuntos

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Mensajes no leídos con adjuntos:"

        print messages.size()

if __name__ == '__main__':        

    SearchMessagesAndFoldersInPST()
```
## **Descargar Código en Ejecución**
Descarga **Buscar mensajes y carpetas en un PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)