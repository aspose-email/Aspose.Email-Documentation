---
title: "Buscar mensajes y carpetas en un PST por algunos criterios en Ruby"
url: /es/java/buscar-mensajes-y-carpetas-en-un-pst-por-algunos-criterios-en-ruby/
weight: 80
type: docs
---

## **Aspose.Email - Buscar mensajes y carpetas en un PST**
Para buscar mensajes y carpetas en un PST usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **SearchMessagesAndFoldersInPST**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Cargar el archivo PST de Outlook

pst = Rjb::import('com.aspose.email.PersonalStorage').fromFile(data_dir + "sample.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = Rjb::import('com.aspose.email.PersonalStorageQueryBuilder').new

\# Mensajes de alta importancia

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

messages = folder.getContents(builder.getQuery())

puts "Mensajes con alta importancia:" + messages.size().to_s

#builder = new PersonalStorageQueryBuilder();

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

puts "Mensajes con IPM.Note:" + messages.size().to_s

\# Mensajes con archivos adjuntos Y alta importancia

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Mensajes con adjuntos: " + messages.size().to_s

\# Mensajes con tamaño > 15 KB

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

puts "mensajes tamaño > 15Kb:" + messages.size().to_s

\# Mensajes no leídos

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

puts "No leídos:" + messages.size().to_s

\# Mensajes no leídos con archivos adjuntos

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Mensajes no leídos con adjuntos: " + messages.size().to_s

```
## **Descargar código en ejecución**
Descarga **Buscar mensajes y carpetas en un PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/searchmessagesandfoldersinpst.rb)