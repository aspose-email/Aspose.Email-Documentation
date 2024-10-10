---
title: "Парсинг файлов сообщений Outlook в Jython"
url: /ru/java/parsing-outlook-message-files-in-jython/
weight: 30
type: docs
---

## **Aspose.Email - Парсинг файлов сообщений Outlook**
Чтобы распарсить файл сообщения Outlook, используя **Aspose.Email Java для Jython**, просто вызовите модуль **ParseOutlookMessageFile**. Здесь вы можете найти пример кода.

**Код Jython**

```python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

class ParseOutlookMessageFile:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile/'



        mapiMessage=MapiMessage()

        outlook_message_file = mapiMessage.fromFile(dataDir + "Message.msg")

        # Отобразить имя отправителя

        print "Sender Name : " 

        print outlook_message_file.getSenderName()

        #Отобразить тему

        print "Subject : " 

        print outlook_message_file.getSubject()

        # Отобразить тело сообщения

        print "Body : " 

        print outlook_message_file.getBody()





if __name__ == '__main__':        

    ParseOutlookMessageFile()

```
## **Скачать рабочий код**
Скачайте **Парсинг файлов сообщений Outlook (Aspose.Email)** с любого из указанных ниже сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)