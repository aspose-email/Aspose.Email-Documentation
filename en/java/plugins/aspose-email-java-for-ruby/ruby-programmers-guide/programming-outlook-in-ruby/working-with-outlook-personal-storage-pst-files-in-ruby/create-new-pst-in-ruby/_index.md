---
title: Create New PST in Ruby
ArticleTitle: Create New PST in Ruby
type: docs
weight: 70
url: /java/create-new-pst-in-ruby/
---

## **Aspose.Email - Create New PST**
To Create new PST using **Aspose.Email Java for Ruby**, simply invoke **CreatePST** module. Here you can see example code.

**Ruby Code**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Create an instance of PersonalStorage

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "sample1.pst", 0)

\# Create a folder at root of pst

pst.getRootFolder().addSubFolder("myInbox")

\# Add message to newly created folder

mapi_message = Rjb::import('com.aspose.email.MapiMessage')

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(data_dir + "Message.msg"))

puts "Created PST successfully."

```
## **Download Running Code**
Download **Create New PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createpst.rb)
