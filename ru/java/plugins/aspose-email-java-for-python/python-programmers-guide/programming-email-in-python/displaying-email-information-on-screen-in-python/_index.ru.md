---
title: "Отображение информации об электронной почте на экране в Python"
url: /ru/java/displaying-email-information-on-screen-in-python/
weight: 40
type: docs
---

## **Aspose.Email - отображение информации об электронной почте**
Для отображения информации об электронной почте с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

``` python



\# Create MailMessage instance by loading an Eml file

message_format = self.MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "From: "

print message.getFrom()

print "To: "

print message.getTo()

print "Subject: "

print message.getSubject()

print "HtmlBody: "

print message.getHtmlBody()

print "TextBody: "

print message.getTextBody()

```
## **Загрузить рабочий код**
Download **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
