---
title: "Поиск строк в PST с игнорированием регистра в Jython"
url: /ru/java/string-searching-in-pst-with-ignore-case-in-jython/
weight: 80
type: docs
---

## **Aspose.Email - поиск строк в PST с регистром игнорирования**
Для поиска строк в PST с помощью Ignore Case используйте **Aspose.Электронная почта Java для Mython**, просто вызовите **StringSearchInPST** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

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
## **Загрузить рабочий код**
Download **Поиск строк в PST с использованием регистра игнорирования (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
