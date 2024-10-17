---
title: "Creación y Guardado de Notas de Outlook en Ruby"
url: /es/java/creacion-y-guardado-de-notas-de-outlook-en-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Creación y Guardado de Notas de Outlook**
Para crear notas de Outlook usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **CreateOutlookNote**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

note = Rjb::import('com.aspose.email.MapiNote').new

note.setSubject("Nota de color azul")

note.setBody("Esta es una nota de color azul")

note.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note.setHeight(500)

note.setWidth(500)

note.save(data_dir + "MapiNote.msg", Rjb::import('com.aspose.email.NoteSaveFormat').Msg)

puts "Nota de Outlook creada con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Creación y Guardado de Notas de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooknote.rb)