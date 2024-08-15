---
title: "Добавление MapiCalendar в PST в Jython"
url: /ru/java/adding-mapicalendar-to-pst-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - Добавление MapiCalendar в PST**
Чтобы добавить MapicaLendar в PST, используя **Aspose.Электронная почта Java для Mython**, просто вызовите **AddMapiCalendarToPST** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

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
## **Загрузить рабочий код**
Download **Добавление MapicaLendar в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
