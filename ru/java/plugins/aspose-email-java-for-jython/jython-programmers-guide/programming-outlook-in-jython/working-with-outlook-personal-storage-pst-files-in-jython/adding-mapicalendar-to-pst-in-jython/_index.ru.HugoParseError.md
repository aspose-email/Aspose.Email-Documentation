---
title: Добавление MapiCalendar в PST на Jython
type: docs
weight: 20
url: /java/adding-mapicalendar-to-pst-in-jython/
---

## **Aspose.Email - Добавление MapiCalendar в PST**
Чтобы добавить MapiCalendar в PST с использованием **Aspose.Email Java для Jython**, просто вызовите модуль **AddMapiCalendarToPST**. Здесь вы можете увидеть пример кода.

**Код Jython**

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

        print "Добавлен файл в PST"





if __name__ == '__main__':        

    AddFileToPST()

```

## **Скачать исполняемый код**
Скачайте **Добавление MapiCalendar в PST (Aspose.Email)** с любого из указанных ниже сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)