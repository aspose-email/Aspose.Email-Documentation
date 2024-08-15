---
title: "Управление вложениями в сообщении электронной почты в Ruby"
url: /ru/java/manage-attachments-in-email-message-in-ruby/
weight: 60
type: docs
---

## **Aspose.Email - Управление вложениями в сообщении электронной почты**
Чтобы добавить вложения в новое сообщение электронной почты, используя **Aspose.Электронная почта Java для Ruby**, позвоните **add_attachments** метод **ManageAttachments** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 def add_attachments()

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Create a new instance of MailMessage class

    message = Rjb::import('com.aspose.email.MailMessage').new

    # Set subject of the message

    message.setSubject("New message created by Aspose.Email for Java")

    mail_address = Rjb::import('com.aspose.email.MailAddress')

    # Set Html body

    message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

            "<font color=blue>This line is in blue color</font>")

    # Set sender information

    message.setFrom(mail_address.new("from@domain.com", "Sender Name", false))

    # Add TO recipients

    message.getTo().add(mail_address.new("to1@domain.com", "Recipient 1", false))

    # Adding attachment

    # Load an attachment

    attachment = Rjb::import('com.aspose.email.Attachment').new(data_dir + "attachment.txt")

    # Add attachment in instance of MailMessage class

    message.addAttachment(attachment)

    # Save message to disc

    message.save(data_dir + "Add-Attachment.msg", Rjb::import('com.aspose.email.MessageFormat').getMsg())

    # Display Status

    puts "Added attachment successfully."

end

```
## **Загрузить рабочий код**
Download **Управление вложениями в сообщении электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/manageattachments.rb)
