---
title: "Búsqueda de Cadenas en PST Ignorando Mayúsculas en Python"
url: /es/java/string-searching-in-pst-with-ignore-case-in-python/
weight: 70
type: docs
---

## **Aspose.Email - Búsqueda de Cadenas en PST Ignorando Mayúsculas**
Búsqueda de Cadenas en PST Ignorando Mayúsculas utilizando **Aspose.Email Java para Python**, utilice el siguiente código.

**Código Python**

```python



personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

pst = personalStorage.create(self.dataDir + "search.pst", fileFormatVersion.Unicode)

standardIpmFolder = self.StandardIpmFolder

fi = pst.createPredefinedFolder("Inbox", standardIpmFolder.Inbox)

mapiMessage = self.MapiMessage

mailMessage = self.MailMessage

fi.addMessage(mapiMessage.fromMailMessage(mailMessage.load(self.dataDir + "search.pst")))

builder = self.MailQueryBuilder()

builder.getFrom().contains("automated", True)

query = builder.getQuery()

coll = fi.getContents(query)

print "Total Results:"

print coll.size()

```
## **Descargar Código en Ejecución**
Descargue **Búsqueda de Cadenas en PST Ignorando Mayúsculas (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)