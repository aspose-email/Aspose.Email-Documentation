---
title: "Настройка заголовков электронной почты в Python"
url: /ru/java/customizing-email-headers-in-python/
weight: 30
type: docs
---

## **Aspose.Email - Настройка заголовков электронной почты**
Для настройки заголовков электронной почты с использованием **Aspose.Email Java for Python** используйте следующий код.

**Код Python**

``` python



\# Создать экземпляр класса MailMessage

message = self.MailMessage()

    # Установить тему сообщения

message.setSubject("Новое сообщение, созданное Aspose.Email для Java")

\# Установить Html тело

message.setHtmlBody("<b>Эта строка выделена жирным.</b> <br/> <br/>" +

    "<font color=blue>Эта строка синего цвета</font>")

\# Установить информацию об отправителе

message.setFrom(self.MailAddress("from@domain.com", "Имя отправителя", False))

\# Добавить получателей в TO

message.getTo().addMailAddress(self.MailAddress("to@domain.com", "Получатель 1", False))

\# Тема сообщения

message.setSubject("Настройка заголовков электронной почты")

\# Указать дату

timeZone = self.TimeZone

calendar = self.Calendar

calendar = calendar.getInstance(timeZone.getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Указать XMailer

message.setXMailer("Aspose.Email")

\# Указать секретный заголовок

message.getHeaders().add("secret-header", "mystery")

\# Сохранить сообщение на диск

messageFormat= self.MessageFormat

message.save(self.dataDir + "MsgHeaders.msg", messageFormat.getMsg())

\# Показать статус

print "Заголовки сообщения успешно настроены."

```
## **Скачать работающий код**
Скачайте **Настройка заголовков электронной почты (Aspose.Email)** с любого из нижеуказанных сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)