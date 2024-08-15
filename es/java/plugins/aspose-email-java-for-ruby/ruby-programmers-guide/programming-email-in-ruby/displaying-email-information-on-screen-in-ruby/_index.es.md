---
title: "Mostrar información de correo electrónico en la pantalla en Ruby"
url: /es/java/displaying-email-information-on-screen-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Mostrar información de correo electrónico**
Para mostrar información de correo electrónico mediante **Aspose.Email Java para Ruby**, simplemente invoca **GetEmailInfo** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

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
## **Descargar Running Code**
Download **Mostrar información de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/getemailinfo.rb)
