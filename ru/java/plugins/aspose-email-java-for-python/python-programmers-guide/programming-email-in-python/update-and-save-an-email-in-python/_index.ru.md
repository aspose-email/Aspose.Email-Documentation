---
title: "Обновление и сохранение электронной почты в Python"
url: /ru/java/update-and-save-an-email-in-python/
weight: 80
type: docs
---

## **Aspose.Email - Обновление и сохранение электронной почты**
Для обновления и сохранения электронной почты с использованием **Aspose.Email Java для Python** используйте следующий код.

**Python код**

``` python

\# Инициализировать и загрузить существующий MSG файл, указав формат сообщения

mailMessage = self.MailMessage

email = mailMessage.load(self.dataDir + "Message.msg")

\# Инициализировать строковую переменную для получения темы электронной почты

subject = email.getSubject()

\# Добавить дополнительную информацию к теме

subject = subject + " Этот текст добавлен к существующей теме"

\# Установить тему электронной почты

email.setSubject('Этот текст добавлен к существующей теме')

\# Инициализировать строковую переменную для получения HTML тела электронной почты

body = email.getHtmlBody()

\# Добавить дополнительную информацию к переменной Body

body = body + "<br> Этот текст добавлен к существующему телу"

\# Установить тело электронной почты

email.setHtmlBody(body)

\# Инициализировать объект MailAddressCollection

contacts = self.MailAddressCollection()

\# Получить список получателей электронной почты

contacts = email.getTo()

\# Добавить другой адрес электронной почты в коллекцию

contacts.add("to1@domain.com")

\# Установить коллекцию в качестве списка получателей электронной почты

email.setTo(contacts)

\# Инициализировать MailAddressCollection

contacts = self.MailAddressCollection()

\# Получить список копий получателей электронной почты

contacts = email.getCC()

\# Добавить другой адрес электронной почты в коллекцию

contacts.add("cc2@domain.com")

\# Установить коллекцию в качестве списка копий получателей электронной почты

email.setCC(contacts)

\# Сохранить сообщение электронной почты на диске, указав формат сообщения

mailMessageSaveType = self.MailMessageSaveType

email.save(self.dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

\# Показать статус

print "Электронное сообщение успешно обновлено."

```
## **Загрузить работающий код**
Скачайте **Обновление и сохранение электронной почты (Aspose.Email)** с любого из нижеуказанных сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)