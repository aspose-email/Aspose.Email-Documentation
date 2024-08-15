---
title: "Extracción de encabezados de correo electrónico en Ruby"
url: /es/java/extracting-email-headers-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Extracción de encabezados de correo electrónico**
Para extraer encabezados de correo electrónico usando **Aspose.Email Java para Ruby**, simplemente invoca **ExtractEmailHeaders** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

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
## **Descargar Running Code**
Download **Extracción de encabezados de correo electrónico (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/extractemailheaders.rb)
