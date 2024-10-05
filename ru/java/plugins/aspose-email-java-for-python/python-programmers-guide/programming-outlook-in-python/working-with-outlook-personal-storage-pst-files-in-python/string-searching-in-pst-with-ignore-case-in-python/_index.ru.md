---
title: "Поиск строк в PST с игнорированием регистра в Python"
url: /ru/java/string-searching-in-pst-with-ignore-case-in-python/
weight: 70
type: docs
---

## **Aspose.Email - Поиск строк в PST с игнорированием регистра**
Поиск строк в PST с игнорированием регистра с использованием **Aspose.Email Java для Python**. Используйте следующий код.

**Код на Python**

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
## **Скачать работающий код**
Скачайте **Поиск строк в PST с игнорированием регистра (Aspose.Email)** с любого из нижеуказанных сайтов для социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)