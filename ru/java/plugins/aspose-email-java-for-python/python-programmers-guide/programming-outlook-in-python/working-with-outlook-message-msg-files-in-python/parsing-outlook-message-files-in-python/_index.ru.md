---
title: "Разбор файлов сообщений Outlook в Python"
url: /ru/java/parsing-outlook-message-files-in-python/
weight: 30
type: docs
---

## **Aspose.Email - парсинг файлов сообщений Outlook**
Для анализа файлов сообщений Outlook с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

```python



mapiMessage = self.MapiMessage

outlook_message_file = mapiMessage.fromFile(self.dataDir + "Message.msg")

\# Display sender's name

print "Sender Name : "

print outlook_message_file.getSenderName()

#Display Subject

print "Subject : "

print outlook_message_file.getSubject()

\# Display Body

print "Body : "

print outlook_message_file.getBody()

```
## **Загрузить рабочий код**
Download **Разбор файлов сообщений Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
