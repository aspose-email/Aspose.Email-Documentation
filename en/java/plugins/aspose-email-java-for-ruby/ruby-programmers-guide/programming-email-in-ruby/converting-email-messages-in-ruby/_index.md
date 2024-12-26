---
title: Converting Email Messages in Ruby
ArticleTitle: Converting Email Messages in Ruby
type: docs
weight: 10
url: /java/converting-email-messages-in-ruby/
---

## **Aspose.Email - Converting Email Messages**
To Convert Email Messages using **Aspose.Email Java for Ruby**, call **convert_eml_to_msg** method of **Converter** module. Here you can see example code.

**Ruby Code**

``` ruby

 def convert_eml_to_msg()    

    data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

    # Initialize and Load an existing EML file by specifying the MessageFormat

    eml = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

    # Save the Email message to disk in Unicode format

    eml.save(data_dir + "AnEmail.msg", Rjb::import('com.aspose.email.SaveOptions').getDefaultMsgUnicode())

    # Display Status

    puts "Converted eml to msg successfully."

end

```
## **Download Running Code**
Download **Converting Email Messages (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/converter.rb)
