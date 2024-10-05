---
title: Управление Вложениями в Email Сообщении на Python
type: docs
weight: 60
url: /java/manage-attachments-in-email-message-in-python/
---

## **Aspose.Email - Управление Вложениями в Email**
Чтобы управлять вложениями в Email с использованием **Aspose.Email Java для Python**, используйте следующий код.

**Код Python**

``` python



\# Создайте экземпляр класса MailMessage

message = self.MailMessage()

\# Установите тему сообщения

message.setSubject("Новое сообщение, созданное с помощью Aspose.Email для Java")

mail_address = self.MailAddress

\# Установите Html тело

message.setHtmlBody("<b>Эта строка выделена жирным шрифтом.</b> <br/> <br/>" +

    "<font color=blue>Эта строка синего цвета</font>")

\# Установите информацию об отправителе

message.setFrom(self.MailAddress("from@domain.com", "Имя отправителя", False))

\# Добавьте адреса получателей TO

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Получатель 1", False))

\# Добавление вложения

\# Загрузите вложение

attachment = self.Attachment(self.dataDir + "1.txt")

\# Добавьте вложение в экземпляр класса MailMessage

message.addAttachment(attachment)

\# Сохраните сообщение на диск

messageFormat = self.MessageFormat

message.save(self.dataDir + "Add-Attachment.msg", messageFormat.getMsg())

\# Отобразите статус

print "Вложение успешно добавлено."

```
## **Скачать Рабочий Код**
Скачайте **Управление Вложениями в Email Сообщении (Aspose.Email)** с любого из указанных ниже сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)