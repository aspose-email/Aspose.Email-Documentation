---
title: "Búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas en Ruby"
url: /es/java/string-searching-in-pst-with-ignore-case-in-ruby/
weight: 90
type: docs
---

## **Aspose.Email: búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas**
Para buscar cadenas en PST con ignorar mayúsculas y minúsculas usando **Aspose.Email Java para Ruby**, simplemente invoca **StringSearchInPST** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Load the Outlook PST file

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "search.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

fi = pst.createPredefinedFolder("Inbox", Rjb::import('com.aspose.email.StandardIpmFolder').Inbox)

fi.addMessage(Rjb::import('com.aspose.email.MapiMessage').fromMailMessage(Rjb::import('com.aspose.email.MailMessage').load(data_dir + "search.pst")))

builder = Rjb::import('com.aspose.email.MailQueryBuilder').new

builder.getFrom().contains("automated", true)

query = builder.getQuery()

coll = fi.getContents(query)

puts "Total Results:" + coll.size().to_s

```
## **Descargar Running Code**
Download **Búsqueda de cadenas en PST con ignorar mayúsculas y minúsculas (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/stringsearchinpst.rb)
