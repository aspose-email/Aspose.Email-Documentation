---
title: "Extrayendo Encabezados de Email en Ruby"
url: /es/java/extracting-email-headers-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Extrayendo Encabezados de Email**
Para extraer encabezados de email usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **ExtractEmailHeaders**. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'



\# Inicializa y carga un archivo EML existente especificando el MessageFormat

message = Rjb::import('com.aspose.email.MailMessage').load(data_dir + "Message.eml")

puts "Imprimiendo todos los Encabezados:"

\# Imprime todos los encabezados

i=0

while i < message.getHeaders().getCount()

    puts message.getHeaders().get(i)

    i +=1

end 

```
## **Descargar Código en Ejecución**
Descarga **Extrayendo Encabezados de Email (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Email/extractemailheaders.rb)