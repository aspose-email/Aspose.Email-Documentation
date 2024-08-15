---
title: "Búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas en Python"
url: /es/java/string-searching-in-pst-with-ignore-case-in-python/
weight: 70
type: docs
---

## **Aspose.Email: búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas**
Búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas usando **Aspose.Email Java para Python**, Usa el siguiente código.

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
## **Descargar Running Code**
Download **Búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
