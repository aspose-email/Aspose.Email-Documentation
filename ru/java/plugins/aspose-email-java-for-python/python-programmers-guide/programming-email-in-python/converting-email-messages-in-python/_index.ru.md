---
title: "Преобразование сообщений электронной почты в Python"
url: /ru/java/converting-email-messages-in-python/
weight: 10
type: docs
---

## **Aspose.Email - конвертация сообщений электронной почты**
Для преобразования сообщений электронной почты с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

``` python

 # Initialize and Load an existing EML file by specifying the MessageFormat

mailMessage = self.MailMessage

eml = mailMessage.load(self.dataDir + "Message.eml")

\# Save the Email message to disk in Unicode format

saveOptions= self.SaveOptions

eml.save(self.dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

\# Display Status

print "Converted email to msg successfully."

```
## **Загрузить рабочий код**
Download **Преобразование сообщений электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
