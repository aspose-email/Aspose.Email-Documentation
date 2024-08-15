---
title: Extracting Email Headers in Ruby
type: docs
weight: 50
url: /java/extracting-email-headers-in-ruby/
---

## **Aspose.Email - Extracting Email Headers**
To Extract Email Headers using **Aspose.Email Java for Ruby**, simply invoke **ExtractEmailHeaders** module. Here you can see example code.

**Ruby Code**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Initialize and Load an existing EML file by specifying the MessageFormat

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "Printing all Headers:"

\# Print out all the headers

i=0

while i < message.getHeaders().getCount()

    puts message.getHeaders().get(i)

    i +=1

end 

```
## **Download Running Code**
Download **Extracting Email Headers (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/extractemailheaders.rb)
