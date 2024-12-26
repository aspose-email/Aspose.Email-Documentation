---
title: Adding MapiJournal to PST in Jython
ArticleTitle: Adding MapiJournal to PST in Jython
type: docs
weight: 40
url: /java/adding-mapijournal-to-pst-in-jython/
---

## **Aspose.Email - Adding MapiJournal to PST**
To Add MapiJournal to PST using **Aspose.Email Java for PHP**, simply invoke **AddMapiJournalToPST** module. Here you can see example code.

**Jython Code**

{{< highlight python >}}

 from aspose-email import Settings

from com.aspose.email import MapiJournal

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

from java.util import Date

from java.util import Calendar

class AddMapiJournalToPST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiJournalToPST/'



        d1 = Date()

        calendar=Calendar

        cl = calendar.getInstance()

        cl.setTime(d1)

        cl.add(calendar.HOUR, 1)

        d2 = cl.getTime()

        journal = MapiJournal("daily record", "called out in the dark", "Phone call", "Phone call")

        journal.setStartTime(d1)

        journal.setEndTime(d2)

        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        pst = personalStorage.create(dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

        standardIpmFolder=StandardIpmFolder

        journal_folder = pst.createPredefinedFolder("Journal", standardIpmFolder.Journal)

        journal_folder.addMapiMessageItem(journal)

        print "Added MapiJournal Successfully."





if __name__ == '__main__':        

    AddMapiJournalToPST()

{{< /highlight >}}
## **Download Running Code**
Download **Adding MapiJournal to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
