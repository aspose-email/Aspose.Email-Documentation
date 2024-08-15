---
title: "Создайте новый PST в Ruby"
url: /ru/java/create-new-pst-in-ruby/
weight: 70
type: docs
---

## **Aspose.Email - Создайте новый PST**
Чтобы создать новый PST, используя **Aspose.Электронная почта Java для Ruby**, просто вызовите **CreatePST** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

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
## **Загрузить рабочий код**
Download **Создайте новый PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createpst.rb)
