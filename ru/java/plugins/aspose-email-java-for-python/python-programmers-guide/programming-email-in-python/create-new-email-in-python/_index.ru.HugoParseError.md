---
title: Создание нового email на Python
type: docs
weight: 20
url: /java/create-new-email-in-python/
---

## **Aspose.Email - Создание нового email**
Чтобы создать новый email с помощью **Aspose.Email Java для Python**, используйте следующий код.

**Код Python**

``` python



\# Создание экземпляра класса MailMessage

message = self.MailMessage()

\# Установка темы сообщения

message.setSubject("Новое сообщение, созданное с помощью Aspose.Email для Java")

mail_address = self.MailAddress

\# Установка Html-содержимого

message.setHtmlBody("<b>Эта строка выделена жирным шрифтом.</b> <br/> <br/>" +

   "<font color=blue>Эта строка синего цвета</font>")

\# Установка информации об отправителе

message.setFrom(self.MailAddress("from@domain.com", "Имя отправителя", False))

\# Добавление получателей в TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Получатель 1", False))

message.getTo().addMailAddress(self.MailAddress("to2@domain.com", "Получатель 2", False))

\# Добавление получателей в CC

message.getCC().addMailAddress(self.MailAddress("cc1@domain.com", "Получатель 3", False))

message.getCC().addMailAddress(self.MailAddress("cc2@domain.com", "Получатель 4", False))

\# Сохранение сообщения в форматах EML и MSG

mail_message_save_type = self.MailMessageSaveType

message.save(self.dataDir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(self.dataDir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Отображение статуса

print "Сообщение успешно создано."

```
## **Скачать работающий код**
Скачайте **Создание нового email (Aspose.Email)** с любого из нижеупомянутых сайтов социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)