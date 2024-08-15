---
title: "Поиск сообщений и папок в PST по некоторым критериям в Jython"
url: /ru/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-jython/
weight: 70
type: docs
---

## **Aspose.Email - поиск сообщений и папок в PST**
Для поиска сообщений и папок в PST с помощью **Aspose.Электронная почта Java для Mython**, просто вызовите **SearchMessagesAndFoldersInPST** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

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
## **Загрузить рабочий код**
Download **Поиск сообщений и папок в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
