---
title: "Crear un nuevo PST en Ruby"
url: /es/java/create-new-pst-in-ruby/
weight: 70
type: docs
---

## **Aspose.Email - Crear un nuevo PST**
Para crear un nuevo PST usando **Aspose.Email Java para Ruby**, simplemente invoca **CreatePST** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

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
## **Descargar Running Code**
Download **Crear un nuevo PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createpst.rb)
