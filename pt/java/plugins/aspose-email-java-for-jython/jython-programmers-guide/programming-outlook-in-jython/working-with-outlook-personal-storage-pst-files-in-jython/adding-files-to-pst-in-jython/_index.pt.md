---
title: "Adicionando Arquivos ao PST em Jython"
url: /pt/java/adding-files-to-pst-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - Adicionando Arquivos ao PST**
Para adicionar um arquivo ao PST usando **Aspose.Email Java para Jython**, simplesmente invoque o módulo **AddFileToPST**. Aqui você pode ver um código de exemplo.

**Código Jython**

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

        print "Arquivo adicionado ao PST"

if __name__ == '__main__':        

    AddFileToPST()

```
## **Baixar Código em Execução**
Baixe **Adicionando Arquivos ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)