---
title: "Adicionando MapiCalendar ao PST em Jython"
url: /pt/java/adding-mapicalendar-to-pst-in-jython/
weight: 20
type: docs
---

## **Aspose.Email - Adicionando MapiCalendar ao PST**
Para adicionar MapiCalendar ao PST usando **Aspose.Email Java para Jython**, basta invocar o módulo **AddMapiCalendarToPST**. Aqui você pode ver um código de exemplo.

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

        print "Arquivo adicionado ao PST"





if __name__ == '__main__':        

    AddFileToPST()

```
## **Baixar Código em Execução**
Baixe **Adicionando MapiCalendar ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)