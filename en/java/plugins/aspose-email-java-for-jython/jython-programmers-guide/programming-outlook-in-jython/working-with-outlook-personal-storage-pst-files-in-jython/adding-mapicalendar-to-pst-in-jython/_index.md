---
title: Adding MapiCalendar to PST in Jython
ArticleTitle: Adding MapiCalendar to PST in Jython
type: docs
weight: 20
url: /java/adding-mapicalendar-to-pst-in-jython/
---

## **Aspose.Email - Adding MapiCalendar to PST**
To Add MapiCalendar to PST using **Aspose.Email Java for Jython**, simply invoke **AddMapiCalendarToPST** module. Here you can see example code.

**Jython Code**

{{< highlight python >}}

 from aspose-email import Settings

from com.aspose.email import MapiCalendar

from com.aspose.email import MapiRecipientCollection

from com.aspose.email import MapiRecipientType

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

class AddFileToPST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddFileToPST/'



        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        pst = personalStorage.create(dataDir + "AddFile1.pst", fileFormatVersion.Unicode)

        standardIpmFolder=StandardIpmFolder

        fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

        fi.addFile(dataDir + "Report.xlsx", "IPM.Document.Excel.Sheet.8")

        pst.dispose()

        print "Added file to PST"





if __name__ == '__main__':        

    AddFileToPST()

{{< /highlight >}}
## **Download Running Code**
Download **Adding MapiCalendar to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
