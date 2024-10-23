---
title: "Adicionando MapiJournal ao PST em Python"
url: /pt/java/adding-mapijournal-to-pst-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Adicionando MapiJournal ao PST**
Para adicionar MapiJournal ao PST usando **Aspose.Email Java para Python**, use o seguinte código.

**Código Python**

```python



d1 = self.Date()

calendar = self.Calendar

cl = calendar.getInstance()

cl.setTime(d1)

cl.add(calendar.HOUR, 1)

d2 = cl.getTime()

journal = self.MapiJournal("registro diário", "chamado no escuro", "Chamada telefônica", "Chamada telefônica")

journal.setStartTime(d1)

journal.setEndTime(d2)

personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

journal_folder = pst.createPredefinedFolder("Journal", standardIpmFolder.Journal)

journal_folder.addMapiMessageItem(journal)

print "MapiJournal adicionado com sucesso."

```
## **Baixar Código em Execução**
Baixe **Adicionando MapiJournal ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)