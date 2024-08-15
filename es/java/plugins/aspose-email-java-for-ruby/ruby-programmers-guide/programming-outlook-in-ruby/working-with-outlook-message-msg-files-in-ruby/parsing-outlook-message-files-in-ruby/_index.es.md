---
title: "Análisis de archivos de mensajes de Outlook en Ruby"
url: /es/java/parsing-outlook-message-files-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Análisis de archivos de mensajes de Outlook**
Para analizar el archivo de mensajes de Outlook usando **Aspose.Email Java para Ruby**, simplemente invoca **ParseOutlookMessageFile** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

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
## **Descargar Running Code**
Download **Análisis de archivos de mensajes de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/parseoutlookmessagefile.rb)
