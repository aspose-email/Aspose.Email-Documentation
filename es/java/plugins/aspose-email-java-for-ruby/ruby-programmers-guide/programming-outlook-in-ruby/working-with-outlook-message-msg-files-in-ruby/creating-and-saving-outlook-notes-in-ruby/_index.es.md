---
title: "Crear y guardar notas de Outlook en Ruby"
url: /es/java/creating-and-saving-outlook-notes-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Creación y almacenamiento de notas de Outlook**
Para crear notas de Outlook usando **Aspose.Email Java para Ruby**, simplemente invoca **CreateOutlookNote** módulo. Aquí puedes ver un ejemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

note = Rjb::import('com.aspose.email.MapiNote').new

note.setSubject("Blue color note")

note.setBody("This is a blue color note")

note.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note.setHeight(500)

note.setWidth(500)

note.save(data_dir + "MapiNote.msg", Rjb::import('com.aspose.email.NoteSaveFormat').Msg)

puts "Created outlook note successfully."

```
## **Descargar Running Code**
Download **Creación y almacenamiento de notas de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooknote.rb)
