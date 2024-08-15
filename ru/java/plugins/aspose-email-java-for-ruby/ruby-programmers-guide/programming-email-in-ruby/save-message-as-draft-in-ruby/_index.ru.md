---
title: "Сохранить сообщение как черновик в Ruby"
url: /ru/java/save-message-as-draft-in-ruby/
weight: 70
type: docs
---

## **Aspose.Email - Сохранить сообщение как черновик**
Чтобы сохранить сообщение как черновик, используя **Aspose.Электронная почта Java для Ruby**, просто вызовите **SaveMessageAsDraft** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Create a new instance of MailMessage class

message = Rjb::import('com.aspose.email.MailMessage').new

\# Set subject of the message

message.setSubject("New message created by Aspose.Email for Java")

mail_address = Rjb::import('com.aspose.email.MailAddress')

\# Set Html body

message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

        "<font color=blue>This line is in blue color</font>")

\# Set sender information

message.setFrom(mail_address.new("from@domain.com", "Sender Name", false))

\# Add TO recipients

message.getTo().add(mail_address.new("to1@domain.com", "Recipient 1", false))

message.getTo().add(mail_address.new("to2@domain.com", "Recipient 2", false))

\# Create an instance of MapiMessage and load the MailMessag instance into it

mapi_msg = Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(message)

\# Set the MapiMessageFlags as UNSENT and FROMME

mapi_message_flags = Rjb::import('com.aspose.email.MapiMessageFlags')

mapi_msg.setMessageFlags(mapi_message_flags.MSGFLAG_UNSENT || mapi_message_flags.MSGFLAG_FROMME)

\# Save the MapiMessage to disk

mapi_msg.save(data_dir + "New-Draft.msg")

\# Display Status

puts "Draft saved Successfully."

```
## **Загрузить рабочий код**
Download **Сохранить сообщение как черновик (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/savemessageasdraft.rb)
