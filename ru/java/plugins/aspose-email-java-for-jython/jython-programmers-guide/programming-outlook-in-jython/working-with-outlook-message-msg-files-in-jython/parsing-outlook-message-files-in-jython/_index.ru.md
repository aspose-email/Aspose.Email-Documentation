---
title: "Разбор файлов сообщений Outlook в Jython"
url: /ru/java/parsing-outlook-message-files-in-jython/
weight: 30
type: docs
---

## **Aspose.Email - парсинг файлов сообщений Outlook**
Для анализа файла сообщений Outlook с помощью **Aspose.Электронная почта Java для Mython**, просто вызовите **ParseOutlookMessageFile** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

```python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

class ParseOutlookMessageFile:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile/'



        mapiMessage=MapiMessage()

        outlook_message_file = mapiMessage.fromFile(dataDir + "Message.msg")

        # Display sender's name

        print "Sender Name : "

        print outlook_message_file.getSenderName()

        #Display Subject

        print "Subject : "

        print outlook_message_file.getSubject()

        # Display Body

        print "Body : "

        print outlook_message_file.getBody()





if __name__ == '__main__':       

    ParseOutlookMessageFile()

```
## **Загрузить рабочий код**
Download **Разбор файлов сообщений Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
