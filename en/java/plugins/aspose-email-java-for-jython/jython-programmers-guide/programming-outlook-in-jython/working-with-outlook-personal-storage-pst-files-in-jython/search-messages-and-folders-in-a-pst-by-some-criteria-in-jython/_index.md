---
title: Search Messages and Folders in a PST by Some Criteria in Jython
type: docs
weight: 70
url: /java/search-messages-and-folders-in-a-pst-by-some-criteria-in-jython/
---

## **Aspose.Email - Search Messages and Folders in a PST**
To Search Messages and Folders in a PST using **Aspose.Email Java for Jython**, simply invoke **SearchMessagesAndFoldersInPST** module. Here you can see example code.

**Jython Code**

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
## **Download Running Code**
Download **Search Messages and Folders in a PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
