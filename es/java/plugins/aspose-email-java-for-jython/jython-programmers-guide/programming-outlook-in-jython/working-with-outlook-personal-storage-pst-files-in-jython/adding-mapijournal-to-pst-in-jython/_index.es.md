---
title: "Agregar MapiJournal a PST en Jython"
url: /es/java/adding-mapijournal-to-pst-in-jython/
weight: 40
type: docs
---

## **Aspose.Email - Agregar MapiJournal a PST**
Para agregar MapiJournal a PST usando **Aspose.Email Java for PHP**, simplemente invoque el módulo **AddMapiJournalToPST**. Aquí puede ver un código de ejemplo.

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

        journal = MapiJournal("registro diario", "llamado en la oscuridad", "Llamada telefónica", "Llamada telefónica")

        journal.setStartTime(d1)

        journal.setEndTime(d2)

        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        pst = personalStorage.create(dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

        standardIpmFolder=StandardIpmFolder

        journal_folder = pst.createPredefinedFolder("Diario", standardIpmFolder.Journal)

        journal_folder.addMapiMessageItem(journal)

        print "MapiJournal agregado con éxito."





if __name__ == '__main__':        

    AddMapiJournalToPST()

```
## **Descargar Código en Ejecución**
Descargue **Agregar MapiJournal a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)