---
title: Parsing Outlook Message Files in Ruby
ArticleTitle: Parsing Outlook Message Files in Ruby
type: docs
weight: 40
url: /java/parsing-outlook-message-files-in-ruby/
---

## **Aspose.Email - Parsing Outlook Message Files**
To Parse Outlook Message file using **Aspose.Email Java for Ruby**, simply invoke **ParseOutlookMessageFile** module. Here you can see example code.

**Ruby Code**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

outlook_message_file = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "Message.msg")

\# Display sender's name

puts "Sender Name : " + outlook_message_file.getSenderName().to_s

#Display Subject

puts "Subject : " + outlook_message_file.getSubject().to_s

\# Display Body

puts "Body : " + outlook_message_file.getBody().to_s

```
## **Download Running Code**
Download **Parsing Outlook Message Files (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/parseoutlookmessagefile.rb)
