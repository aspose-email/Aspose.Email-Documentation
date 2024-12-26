---
title: Adding MapiJournal to PST in Python
ArticleTitle: Adding MapiJournal to PST in Python
type: docs
weight: 30
url: /java/adding-mapijournal-to-pst-in-python/
---

## **Aspose.Email - Adding MapiJournal to PST**
To Add MapiJournal to PST using **Aspose.Email Java for Python**, Use following code.

**Python Code**

{{< highlight python >}}



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

{{< /highlight >}}
## **Download Running Code**
Download **Adding MapiJournal to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
