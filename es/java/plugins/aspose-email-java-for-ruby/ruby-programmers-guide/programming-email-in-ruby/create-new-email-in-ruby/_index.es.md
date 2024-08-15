---
title: "Crear un nuevo correo electrónico en Ruby"
url: /es/java/create-new-email-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Crear nuevo correo electrónico**
Para crear un nuevo correo electrónico usando **Aspose.Email Java para Ruby**, simplemente invoca **CreateNewEmail** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

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

\# Add CC recipients

message.getCC().add(mail_address.new("cc1@domain.com", "Recipient 3", false))

message.getCC().add(mail_address.new("cc2@domain.com", "Recipient 4", false))

\# Save message in EML and MSG formats

mail_message_save_type = Rjb::import('com.aspose.email.MailMessageSaveType')

message.save(data_dir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(data_dir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Display Status

puts "Created email messages Successfully."

```
## **Descargar Running Code**
Download **Crear nuevo correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/createnewemail.rb)
