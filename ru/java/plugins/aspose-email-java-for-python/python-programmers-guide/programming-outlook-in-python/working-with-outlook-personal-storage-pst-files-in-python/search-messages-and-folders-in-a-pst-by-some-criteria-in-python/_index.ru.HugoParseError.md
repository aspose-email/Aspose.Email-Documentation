---
title: Поиск сообщений и папок в PST по некоторым критериям в Python
type: docs
weight: 60
url: /java/search-messages-and-folders-in-a-pst-by-some-criteria-in-python/
---

## **Aspose.Email - Поиск сообщений и папок в PST по некоторым критериям**
Чтобы искать сообщения и папки в PST по некоторым критериям с использованием **Aspose.Email Java для Python**, используйте следующий код.

**Код на Python**

```python



\# Загрузите файл PST Outlook

personalStorage = self.PersonalStorage

pst = personalStorage.fromFile(self.dataDir + "sample1.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = self.PersonalStorageQueryBuilder()

    # Сообщения высокой важности

mapiImportance = self.MapiImportance

builder.getImportance().equals(mapiImportance.High)

messages = folder.getContents(builder.getQuery())

print "Сообщения с высокой важностью:" 

print messages.size()

#builder = PersonalStorageQueryBuilder()

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

print "Сообщения с IPM.Note:" 

print messages.size()

\# Сообщения с вложениями И высокой важностью

builder.getImportance().equals(mapiImportance.High)

mapiMessageFlags = self.MapiMessageFlags

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Сообщения с вложениями: " 

print messages.size()

\# Сообщения размером > 15 КБ

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

print "сообщения размером > 15 Кб:" 

print messages.size()

\# Непрочитанные сообщения

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

print "Непрочитанные:" 

print messages.size()

\# Непрочитанные сообщения с вложениями

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Непрочитанные сообщения с вложениями: " 

print messages.size()

```
## **Скачать работающий код**
Скачайте **Поиск сообщений и папок в PST по некоторым критериям (Aspose.Email)** с любого из нижеуказанных сайтов социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)