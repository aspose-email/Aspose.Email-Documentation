---
title: "Agregar MapiCalendar a PST en Jython"
url: /es/java/adding-mapicalendar-to-pst-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - Agregar MapiCalendar a PST**
Para agregar MapiCalendar a PST usando **Aspose.Email Java para Jython**, simplemente invoca **AddMapiCalendarToPST** módulo. Aquí puedes ver un ejemplo de código.

**Código Jython**

```python

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

```
## **Descargar Running Code**
Download **Agregar MapiCalendar a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
