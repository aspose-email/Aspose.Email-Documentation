---
title: "Agregar MapiJournal a PST en Python"
url: /es/java/adding-mapijournal-to-pst-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Agregar MapiJournal a PST**
Para agregar MapiJournal a PST usando **Aspose.Email Java para Python**, usa el siguiente código.

**Código Python**

```python



d1 = self.Date()

calendar = self.Calendar

cl = calendar.getInstance()

cl.setTime(d1)

cl.add(calendar.HOUR, 1)

d2 = cl.getTime()

journal = self.MapiJournal("registro diario", "llamado en la oscuridad", "Llamada telefónica", "Llamada telefónica")

journal.setStartTime(d1)

journal.setEndTime(d2)

personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "JournalPST.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

journal_folder = pst.createPredefinedFolder("Journal", standardIpmFolder.Journal)

journal_folder.addMapiMessageItem(journal)

print "MapiJournal agregado exitosamente."

```
## **Descargar código en ejecución**
Descarga **Agregar MapiJournal a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)