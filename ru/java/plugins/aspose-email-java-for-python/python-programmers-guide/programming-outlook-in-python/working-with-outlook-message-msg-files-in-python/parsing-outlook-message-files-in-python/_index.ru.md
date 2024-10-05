---
title: "Парсинг файлов сообщений Outlook в Python"
url: /ru/java/parsing-outlook-message-files-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Парсинг файлов сообщений Outlook**
Чтобы парсить файлы сообщений Outlook с использованием **Aspose.Email Java для Python**, используйте следующий код.

**Python код**

```python



mapiMessage = self.MapiMessage

outlook_message_file = mapiMessage.fromFile(self.dataDir + "Message.msg")

\# Отобразить имя отправителя

print "Имя отправителя : " 

print outlook_message_file.getSenderName()

#Отобразить тему

print "Тема : " 

print outlook_message_file.getSubject()

\# Отобразить тело

print "Тело : " 

print outlook_message_file.getBody()

```
## **Скачать рабочий код**
Скачать **Парсинг файлов сообщений Outlook (Aspose.Email)** с любого из нижеупомянутых сайтов социальной кодировки:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)