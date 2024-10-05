---
title: "Поиск сообщений и папок в PST по заданным критериям в Jython"
url: /ru/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-jython/
weight: 70
type: docs
---

## **Aspose.Email - Поиск сообщений и папок в PST**
Чтобы искать сообщения и папки в PST с использованием **Aspose.Email Java для Jython**, просто вызовите модуль **SearchMessagesAndFoldersInPST**. Здесь вы можете увидеть пример кода.

**Код на Jython**

```python

 from aspose-email import Settings

from com.aspose.email import PersonalStorage

from com.aspose.email import PersonalStorageQueryBuilder

from com.aspose.email import MapiImportance

from com.aspose.email import MapiMessageFlags

class SearchMessagesAndFoldersInPST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/SearchMessagesAndFoldersInPST/'



        # Загрузите файл PST Outlook

        personalStorage=PersonalStorage()

        pst = personalStorage.fromFile(dataDir + "sample1.pst")

        folder = pst.getRootFolder().getSubFolder("myInbox")

        builder = PersonalStorageQueryBuilder()

            # Сообщения с высокой важностью

        mapiImportance=MapiImportance

        builder.getImportance().equals(mapiImportance.High)

        messages = folder.getContents(builder.getQuery())

        print "Сообщения с высокой важностью:" 

        print messages.size()

        #builder = PersonalStorageQueryBuilder()

        builder.getMessageClass().equals("IPM.Note")

        messages = folder.getContents(builder.getQuery())

        print "Сообщения с IPM.Note:" 

        print messages.size()

        # Сообщения с вложениями И высокой важностью

        builder.getImportance().equals(mapiImportance.High)

        mapiMessageFlags=MapiMessageFlags

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Сообщения с вложениями: " 

        print messages.size()

        # Сообщения размером > 15 КБ

        builder.getMessageSize().greater(15000)

        messages = folder.getContents(builder.getQuery())

        print "сообщения размером > 15Кб:" 

        print messages.size()

        # Непрочитанные сообщения

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        messages = folder.getContents(builder.getQuery())

        print "Непрочитанные:" 

        print messages.size()

        # Непрочитанные сообщения с вложениями

        builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

        builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

        messages = folder.getContents(builder.getQuery())

        print "Непрочитанные сообщения с вложениями: " 

        print messages.size()





if __name__ == '__main__':        

    SearchMessagesAndFoldersInPST()

```
## **Скачать работающий код**
Скачать **Поиск сообщений и папок в PST (Aspose.Email)** с любого из нижеприведенных сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)