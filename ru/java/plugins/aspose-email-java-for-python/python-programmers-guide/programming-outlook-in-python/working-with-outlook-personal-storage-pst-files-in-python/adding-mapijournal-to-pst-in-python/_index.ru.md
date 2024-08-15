---
title: "Добавление журнала MapiJournal в PST на языке Python"
url: /ru/java/adding-mapijournal-to-pst-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Добавление журнала MapiJournal в PST**
Чтобы добавить MapiJournal в PST, используя **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

```python



d1 = self.Date()

calendar = self.Calendar

cl = calendar.getInstance()

cl.setTime(d1)

cl.add(calendar.HOUR, 1)

d2 = cl.getTime()

journal = self.MapiJournal("daily record", "called out in the dark", "Phone call", "Phone call")

journal.setStartTime(d1)

journal.setEndTime(d2)

personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

journal_folder = pst.createPredefinedFolder("Journal", standardIpmFolder.Journal)

journal_folder.addMapiMessageItem(journal)

print "Added MapiJournal Successfully."

```
## **Загрузить рабочий код**
Download **Добавление журнала MAPIjournal в PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
