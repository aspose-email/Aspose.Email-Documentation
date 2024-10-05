---
title: "Добавление файлов в PST на Jython"
url: /ru/java/adding-files-to-pst-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - Добавление файлов в PST**
Чтобы добавить файл в PST, используя **Aspose.Email Java для Jython**, просто вызовите модуль **AddFileToPST**. Здесь вы можете видеть пример кода.

**Код Jython**

```python

 from aspose-email import Settings

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

        print "Файл добавлен в PST"

if __name__ == '__main__':        

    AddFileToPST()

```
## **Скачать рабочий код**
Скачайте **Добавление файлов в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального кодинга:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)