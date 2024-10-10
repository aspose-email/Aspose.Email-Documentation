---
title: "Отображение информации об электронной почте на экране в Python"
url: /ru/java/displaying-email-information-on-screen-in-python/
weight: 40
type: docs
---

## **Aspose.Email - Отображение информации об электронной почте**
Чтобы отобразить информацию об электронной почте с использованием **Aspose.Email Java для Python**, используйте следующий код.

**Python код**

``` python



\# Создайте экземпляр MailMessage, загрузив файл Eml

message_format = self.MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "От: " 

print message.getFrom()

print "Кому: " 

print message.getTo()

print "Тема: " 

print message.getSubject()

print "HtmlBody: " 

print message.getHtmlBody()

print "TextBody: " 

print message.getTextBody()

```
## **Скачать работающий код**
Скачайте **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеуказанных социальных кодирующих сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)