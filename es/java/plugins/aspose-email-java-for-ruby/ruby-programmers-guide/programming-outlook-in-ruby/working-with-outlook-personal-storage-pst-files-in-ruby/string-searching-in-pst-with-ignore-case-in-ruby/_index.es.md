---
title: "Búsqueda de cadenas en PST sin distinción de mayúsculas en Ruby"
url: /es/java/string-searching-in-pst-with-ignore-case-in-ruby/
weight: 90
type: docs
---

## **Aspose.Email - Búsqueda de cadenas en PST sin distinción de mayúsculas**
Para buscar cadenas en PST sin distinción de mayúsculas usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **StringSearchInPST**. Aquí puedes ver un código de ejemplo.

**Código en Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Cargar el archivo PST de Outlook

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "search.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addMessage(Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(Rjb::import('com.aspose.email.MailMessage').load(data_dir + "search.pst")))

builder = Rjb::import('com.aspose.email.MailQueryBuilder').new

builder.getFrom().contains("automated", true)

query = builder.getQuery()

coll = fi.getContents(query)

puts "Total Results:" + coll.size().to_s

```
## **Descargar Código en Ejecución**
Descarga **Búsqueda de cadenas en PST sin distinción de mayúsculas (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/stringsearchinpst.rb)