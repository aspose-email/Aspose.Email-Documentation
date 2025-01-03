---
title: Create New Email in Ruby
ArticleTitle: Create New Email in Ruby
type: docs
weight: 20
url: /java/create-new-email-in-ruby/
---

## **Aspose.Email - Create New Email**
To Create new Email using **Aspose.Email Java for Ruby**, simply invoke **CreateNewEmail** module. Here you can see example code.

**Ruby Code**

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
## **Download Running Code**
Download **Create New Email (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/createnewemail.rb)
