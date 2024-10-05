---
title: "Сохранить сообщение как черновик в Python"
url: /ru/java/save-message-as-draft-in-python/
weight: 70
type: docs
---

## **Aspose.Email - Сохранить сообщение как черновик**
Чтобы сохранить сообщение как черновик, используя **Aspose.Email Java для Python**, используйте следующий код.

**Python код**

``` python



\# Создайте экземпляр класса MailMessage

message = self.MailMessage()

\# Установите тему сообщения

message.setSubject("Новое сообщение, созданное Aspose.Email для Java")

mail_address = self.MailAddress

\# Установите HTML-содержимое

message.setHtmlBody("<b>Эта строка написана жирным шрифтом.</b> <br/> <br/>" +

    "<font color=blue>Эта строка синего цвета</font>")

\# Установите информацию об отправителе

message.setFrom(self.MailAddress("from@domain.com", "Имя отправителя", False))

\# Добавьте адресаты в поле "Кому"

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Получатель 1", False))

message.getTo().addMailAddress(self.MailAddress("to2@domain.com", "Получатель 2", False))

\# Создайте экземпляр MapiMessage и загрузите в него экземпляр MailMessage

mapiMessage = self.MapiMessage

mapi_msg = mapiMessage.fromMailMessage(message)

\# Установите флаги MapiMessage как UNSENT и FROMME

mapi_message_flags = self.MapiMessageFlags

\# Сохраните MapiMessage на диск

mapi_msg.save(self.dataDir + "New-Draft.msg")

\# Отобразите статус

print "Черновик успешно сохранён."

```
## **Скачать работающий код**
Скачайте **Сохранить сообщение как черновик (Aspose.Email)** с любого из перечисленных ниже сайтов социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)