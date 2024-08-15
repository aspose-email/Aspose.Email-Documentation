---
title: "Поиск сообщений и папок в PST по некоторым критериям в Python"
url: /ru/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-python/
weight: 60
type: docs
---

## **Aspose.Email - поиск сообщений и папок в PST по некоторым критериям**
Для поиска сообщений и папок в PST по некоторым критериям с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

```python



\# Load the Outlook PST file

personalStorage = self.PersonalStorage

pst = personalStorage.fromFile(self.dataDir + "sample1.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = self.PersonalStorageQueryBuilder()

    # High importance messages

mapiImportance = self.MapiImportance

builder.getImportance().equals(mapiImportance.High)

messages = folder.getContents(builder.getQuery())

print "Messages with High Imp:"

print messages.size()

#builder = PersonalStorageQueryBuilder()

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

print "Messages with IPM.Note:"

print messages.size()

\# Messages with attachments AND high importance

builder.getImportance().equals(mapiImportance.High)

mapiMessageFlags = self.MapiMessageFlags

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Messages with atts: "

print messages.size()

\# Messages with size > 15 KB

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

print "messags size > 15Kb:"

print messages.size()

\# Unread messages

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

print "Unread:"

print messages.size()

\# Unread messages with attachments

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Unread msgs with atts: "

print messages.size()

```
## **Загрузить рабочий код**
Download **Поиск сообщений и папок в PST по некоторым критериям (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)
