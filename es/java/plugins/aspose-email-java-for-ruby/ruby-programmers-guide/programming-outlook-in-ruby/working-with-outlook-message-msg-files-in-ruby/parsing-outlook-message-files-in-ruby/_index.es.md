---
title: "Análisis de Archivos de Mensajes de Outlook en Ruby"
url: /es/java/parsing-outlook-message-files-in-ruby/
weight: 40
type: docs
---

## **Aspose.Email - Análisis de Archivos de Mensajes de Outlook**
Para analizar un archivo de mensaje de Outlook usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **ParseOutlookMessageFile**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

outlook_message_file = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "Message.msg")

\# Mostrar el nombre del remitente

puts "Nombre del Remitente : " + outlook_message_file.getSenderName().to_s

# Mostrar el Asunto

puts "Asunto : " + outlook_message_file.getSubject().to_s

\# Mostrar el Cuerpo

puts "Cuerpo : " + outlook_message_file.getBody().to_s

```
## **Descargar Código en Ejecución**
Descarga **Análisis de Archivos de Mensajes de Outlook (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/parseoutlookmessagefile.rb)