---
title: Displaying Email Information on Screen in Ruby
ArticleTitle: Displaying Email Information on Screen in Ruby
type: docs
weight: 40
url: /java/displaying-email-information-on-screen-in-ruby/
---

## **Aspose.Email - Displaying Email Information**
To Display Email Information using **Aspose.Email Java for Ruby**, simply invoke **GetEmailInfo** module. Here you can see example code.

**Ruby Code**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Create MailMessage instance by loading an Eml file

message_format = Rjb::import('com.aspose.email.MessageFormat')

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "From: " + message.getFrom().to_string

puts "To: " + message.getTo().to_string

puts "Subject: " + message.getSubject().to_s

puts "HtmlBody: " + message.getHtmlBody().to_s

puts "TextBody: " + message.getTextBody().to_s

```
## **Download Running Code**
Download **Displaying Email Information (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/getemailinfo.rb)
