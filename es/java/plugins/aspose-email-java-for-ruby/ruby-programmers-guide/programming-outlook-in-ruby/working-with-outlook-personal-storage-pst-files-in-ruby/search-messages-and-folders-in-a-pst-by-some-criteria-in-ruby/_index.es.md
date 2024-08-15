---
title: "Busca mensajes y carpetas en un PST según algunos criterios en Ruby"
url: /es/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-ruby/
weight: 80
type: docs
---

## **Aspose.Email: busca mensajes y carpetas en un PST**
Para buscar mensajes y carpetas en un PST mediante **Aspose.Email Java para Ruby**, simplemente invoca **SearchMessagesAndFoldersInPST** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Load the Outlook PST file

pst = Rjb::import('com.aspose.email.PersonalStorage').fromFile(data_dir + "sample.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = Rjb::import('com.aspose.email.PersonalStorageQueryBuilder').new

\# High importance messages

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

messages = folder.getContents(builder.getQuery())

puts "Messages with High Imp:" + messages.size().to_s

#builder = new PersonalStorageQueryBuilder();

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

puts "Messages with IPM.Note:" + messages.size().to_s

\# Messages with attachments AND high importance

builder.getImportance().equals(Rjb::import('com.aspose.email.MapiImportance').High)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Messages with atts: " + messages.size().to_s

\# Messages with size > 15 KB

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

puts "messags size > 15Kb:" + messages.size().to_s

\# Unread messages

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

puts "Unread:" + messages.size().to_s

\# Unread messages with attachments

builder.hasNoFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_READ)

builder.hasFlags(Rjb::import('com.aspose.email.MapiMessageFlags').MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

puts "Unread msgs with atts: " + messages.size().to_s

```
## **Descargar Running Code**
Download **Buscar mensajes y carpetas en un PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/searchmessagesandfoldersinpst.rb)
