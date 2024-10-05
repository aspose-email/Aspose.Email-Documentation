---
title: "Добавление MapiJournal в PST на Python"
url: /ru/java/adding-mapijournal-to-pst-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Добавление MapiJournal в PST**
Чтобы добавить MapiJournal в PST с помощью **Aspose.Email Java для Python**, используйте следующий код.

**Код на Python**

```python



d1 = self.Date()

calendar = self.Calendar

cl = calendar.getInstance()

cl.setTime(d1)

cl.add(calendar.HOUR, 1)

d2 = cl.getTime()

journal = self.MapiJournal("ежедневная запись", "звонок в темноте", "Телефонный звонок", "Телефонный звонок")

journal.setStartTime(d1)

journal.setEndTime(d2)

personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

journal_folder = pst.createPredefinedFolder("Журнал", standardIpmFolder.Journal)

journal_folder.addMapiMessageItem(journal)

print "Добавлено MapiJournal успешно."

```
## **Скачать работающий код**
Скачайте **Добавление MapiJournal в PST (Aspose.Email)** с любого из нижеупомянутых сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)