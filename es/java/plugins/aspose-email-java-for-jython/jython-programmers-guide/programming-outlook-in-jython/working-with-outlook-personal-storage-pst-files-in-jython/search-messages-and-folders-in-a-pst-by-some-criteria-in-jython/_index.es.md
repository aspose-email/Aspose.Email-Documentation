---
title: "Busque mensajes y carpetas en un PST según algunos criterios en Jython"
url: /es/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-jython/
weight: 70
type: docs
---

## **Aspose.Email: busca mensajes y carpetas en un PST**
Para buscar mensajes y carpetas en un PST mediante **Aspose.Email Java para Jython**, simplemente invoca **SearchMessagesAndFoldersInPST** módulo. Aquí puedes ver un ejemplo de código.

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



        # Load the Outlook PST file

        personalStorage=PersonalStorage()

        pst = personalStorage.fromFile(dataDir + "sample1.pst")

        folder = pst.getRootFolder().getSubFolder("myInbox")

        builder = PersonalStorageQueryBuilder()

            # High importance messages

        mapiImportance=MapiImportance

        builder.getImportance().equals(mapiImportance.High)

        messages = folder.getContents(builder.getQuery())

        print "Messages with High Imp:"

        print messages.size()

        #builder = PersonalStorageQueryBuilder()

        builder.getMessageClass().equals("IPM.Note")

        messages = folder.getContents(builder.getQuery())

        print "Messages with IPM.Note:"

        print messages.size()

        # Messages with attachments AND high importance

        builder.getImportance().equals(mapiImportance.High)

        mapiMessageFlags=MapiMessageFlags

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Messages with atts: "

        print messages.size()

        # Messages with size > 15 KB

        builder.getMessageSize().greater(15000)

        messages = folder.getContents(builder.getQuery())

        print "messags size > 15Kb:"

        print messages.size()

        # Unread messages

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        messages = folder.getContents(builder.getQuery())

        print "Unread:"

        print messages.size()

        # Unread messages with attachments

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Unread msgs with atts: "

        print messages.size()





if __name__ == '__main__':       

    SearchMessagesAndFoldersInPST()

```
## **Descargar Running Code**
Download **Buscar mensajes y carpetas en un PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
