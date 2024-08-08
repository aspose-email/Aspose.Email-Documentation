---
title: String Searching in PST with Ignore Case in Jython
type: docs
weight: 80
url: /java/string-searching-in-pst-with-ignore-case-in-jython/
---

## **Aspose.Email - String Searching in PST with Ignore Case**
To string Searching in PST with Ignore Case using **Aspose.Email Java for Jython**, simply invoke **StringSearchInPST** module. Here you can see example code.

**Jython Code**

{{< highlight python >}}

 from aspose-email import Settings

from com.aspose.email import MapiMessage

from com.aspose.email import NoteColor

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

from java.util import Date

from java.util import Calendar

class StringSearchInPST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST/'



        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        pst = personalStorage.create(dataDir + "search.pst", fileFormatVersion.Unicode)

        standardIpmFolder=StandardIpmFolder

        fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

        mapiMessage=MapiMessage()

        mailMessage=MailMessage()

        fi.addMessage(mapiMessage.fromMailMessage(mailMessage.load(dataDir + "search.pst")))

        builder = MailQueryBuilder()

        builder.getFrom().contains("automated", true)

        query = builder.getQuery()

        coll = fi.getContents(query)

        print "Total Results:" . coll.size()





if __name__ == '__main__':        

    StringSearchInPST()

{{< /highlight >}}
## **Download Running Code**
Download **String Searching in PST with Ignore Case (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
