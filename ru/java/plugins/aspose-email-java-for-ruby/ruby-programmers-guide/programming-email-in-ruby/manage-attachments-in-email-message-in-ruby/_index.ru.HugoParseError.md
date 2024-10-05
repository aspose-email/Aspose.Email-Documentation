---
title: Управление вложениями в электронных сообщениях на Ruby
type: docs
weight: 60
url: /java/manage-attachments-in-email-message-in-ruby/
---

## **Aspose.Email - Управление вложениями в электронном сообщении**
Чтобы добавить вложения в новое электронное сообщение с помощью **Aspose.Email Java для Ruby**, вызовите метод **add_attachments** модуля **ManageAttachments**. Здесь вы можете увидеть пример кода.

**Код на Ruby**

``` ruby

 def add_attachments()

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Создаем новый экземпляр класса MailMessage

    message = Rjb::import('com.aspose.email.MailMessage').new

    # Устанавливаем тему сообщения

    message.setSubject("Новое сообщение, созданное с помощью Aspose.Email для Java")

    mail_address = Rjb::import('com.aspose.email.MailAddress')

    # Устанавливаем Html тело

    message.setHtmlBody("<b>Эта строка выделена жирным.</b> <br/> <br/>" +

            "<font color=blue>Эта строка синего цвета</font>")

    # Устанавливаем информацию об отправителе

    message.setFrom(mail_address.new("from@domain.com", "Имя отправителя", false))

    # Добавляем адреса получателей в поле TO

    message.getTo().add(mail_address.new("to1@domain.com", "Получатель 1", false))

    # Добавление вложения

    # Загружаем вложение

    attachment = Rjb::import('com.aspose.email.Attachment').new(data_dir + "attachment.txt")

    # Добавляем вложение в экземпляр класса MailMessage

    message.addAttachment(attachment)

    # Сохраняем сообщение на диск

    message.save(data_dir + "Add-Attachment.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

    # Отображаем статус

    puts "Вложение успешно добавлено."

end

```
## **Скачать работающий код**
Скачайте **Управление вложениями в электронном сообщении (Aspose.Email)** с любого из нижеуказанных сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/manageattachments.rb)