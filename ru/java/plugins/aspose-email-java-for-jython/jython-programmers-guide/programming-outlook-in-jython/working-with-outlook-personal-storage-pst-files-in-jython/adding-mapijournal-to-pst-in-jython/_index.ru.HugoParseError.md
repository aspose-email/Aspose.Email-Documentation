---
title: Добавление MapiJournal в PST в Jython
type: docs
weight: 40
url: /java/adding-mapijournal-to-pst-in-jython/
---

## **Aspose.Email - Добавление MapiJournal в PST**
Чтобы добавить MapiJournal в PST с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **AddMapiJournalToPST**. Здесь вы можете увидеть пример кода.

**Код Jython**

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

        journal = MapiJournal("ежедневная запись", "позвонил в темноте", "Телефонный звонок", "Телефонный звонок")

        journal.setStartTime(d1)

        journal.setEndTime(d2)

        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        pst = personalStorage.create(dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

        standardIpmFolder=StandardIpmFolder

        journal_folder = pst.createPredefinedFolder("Журнал", standardIpmFolder.Journal)

        journal_folder.addMapiMessageItem(journal)

        print "MapiJournal успешно добавлен."





if __name__ == '__main__':        

    AddMapiJournalToPST()

```
## **Скачать работающий код**
Скачайте **Добавление MapiJournal в PST (Aspose.Email)** с любого из нижеупомянутых сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)