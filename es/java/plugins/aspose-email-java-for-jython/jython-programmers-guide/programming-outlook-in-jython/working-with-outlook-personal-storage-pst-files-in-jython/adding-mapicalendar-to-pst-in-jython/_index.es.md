---
title: "Agregar MapiCalendar a PST en Jython"
url: /es/java/adding-mapicalendar-to-pst-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - Agregar MapiCalendar a PST**
Para agregar MapiCalendar a PST utilizando **Aspose.Email Java para Jython**, simplemente invoca el módulo **AddMapiCalendarToPST**. Aquí puedes ver un código de ejemplo.

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
        print "Archivo agregado a PST"

if __name__ == '__main__':
    AddFileToPST()
```
## **Descargar Código en Ejecución**
Descarga **Agregar MapiCalendar a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)