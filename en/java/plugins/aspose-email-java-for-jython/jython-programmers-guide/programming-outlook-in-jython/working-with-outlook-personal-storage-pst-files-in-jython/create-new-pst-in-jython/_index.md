---
title: Create New PST in Jython
ArticleTitle: Create New PST in Jython
type: docs
weight: 60
url: /java/create-new-pst-in-jython/
---

## **Aspose.Email - Create New PST**
To Create new PST using **Aspose.Email Java for Jython**, simply invoke **CreatePST** module. Here you can see example code.

**Jython Code**

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
## **Download Running Code**
Download **Create New PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
