---
title: "Busca de Strings em PST com Ignorar Case em Jython"
url: /pt/java/busca-de-strings-em-pst-com-ignorar-case-em-jython/
weight: 80
type: docs
---

## **Aspose.Email - Busca de Strings em PST com Ignorar Case**
Para buscar strings em PST com ignorar case usando **Aspose.Email Java para Jython**, basta invocar o módulo **StringSearchInPST**. Aqui você pode ver um exemplo de código.

**Código Jython**

```python
 from aspose-email import Settings

from com.aspose.email import MapiMessage

from com.aspose.email import NoteColor

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

from java.util import Date

from java.util import Calendar

class StringSearchInPST:

    def __init__(self):
        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/StringSearchInPST/'
        personalStorage=PersonalStorage()
        fileFormatVersion=FileFormatVersion
        pst = personalStorage.create(dataDir + "search.pst", fileFormatVersion.Unicode)
        standardIpmFolder=StandardIpmFolder
        fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)
        mapiMessage=MapiMessage()
        mailMessage=MailMessage()
        fi.addMessage(mapiMessage.fromMailMessage(mailMessage.load(dataDir + "search.pst")))
        builder = MailQueryBuilder()
        builder.getFrom().contains("automated", true)
        query = builder.getQuery()
        coll = fi.getContents(query)
        print "Total Results:" . coll.size()

if __name__ == '__main__':        
    StringSearchInPST()
```
## **Baixar Código em Execução**
Baixe **Busca de Strings em PST com Ignorar Case (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)