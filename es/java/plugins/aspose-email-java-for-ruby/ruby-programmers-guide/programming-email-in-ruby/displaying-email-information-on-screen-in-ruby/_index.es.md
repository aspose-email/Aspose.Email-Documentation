---
title: "Mostrando Información de Correo Electrónico en Pantalla en Ruby"
url: /es/java/mostrando-informacion-de-correo-electronico-en-pantalla-en-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Mostrando Información de Correo Electrónico**
Para mostrar información de correo electrónico usando **Aspose.Email Java para Ruby**, simplemente invoque el módulo **GetEmailInfo**. Aquí puede ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Crear instancia MailMessage cargando un archivo Eml

message_format = Rjb::import('com.aspose.email.MessageFormat')

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "De: " + message.getFrom().to_string

puts "Para: " + message.getTo().to_string

puts "Asunto: " + message.getSubject().to_s

puts "HtmlBody: " + message.getHtmlBody().to_s

puts "TextBody: " + message.getTextBody().to_s

```
## **Descargar Código en Ejecución**
Descargue **Mostrando Información de Correo Electrónico (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/getemailinfo.rb)