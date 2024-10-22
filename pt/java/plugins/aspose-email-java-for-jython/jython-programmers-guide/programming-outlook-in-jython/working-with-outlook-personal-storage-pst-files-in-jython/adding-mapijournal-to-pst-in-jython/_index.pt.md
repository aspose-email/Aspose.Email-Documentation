---
title: "Adicionando MapiJournal ao PST em Jython"
url: /pt/java/adding-mapijournal-to-pst-in-jython/
weight: 40
type: docs
---

## **Aspose.Email - Adicionando MapiJournal ao PST**
Para adicionar MapiJournal ao PST usando **Aspose.Email Java para PHP**, basta invocar o módulo **AddMapiJournalToPST**. Aqui você pode ver um exemplo de código.

**Código Jython**

```python

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

        journal = MapiJournal("registro diário", "chamado na escuridão", "Chamada telefônica", "Chamada telefônica")

        journal.setStartTime(d1)

        journal.setEndTime(d2)

        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        pst = personalStorage.create(dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

        standardIpmFolder=StandardIpmFolder

        journal_folder = pst.createPredefinedFolder("Journal", standardIpmFolder.Journal)

        journal_folder.addMapiMessageItem(journal)

        print "MapiJournal adicionado com sucesso."





if __name__ == '__main__':        

    AddMapiJournalToPST()

```
## **Baixar Código em Execução**
Baixe **Adicionando MapiJournal ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)