---
title: "Agregar MapiNote a PST en Ruby"
url: /es/java/adding-mapinote-to-pst-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Agregar MapiNote a PST**
Para agregar MapiNote a PST usando **Aspose.Email Java para Ruby**, simplemente invoca el módulo **AddMapiNoteToPST**. Aquí puedes ver un código de ejemplo.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

mess = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "MapiNote.msg")

\# Nota #1

note1 = mess.toMapiMessageItem()

note1.setSubject("Nota de color amarillo")

note1.setBody("Esta es una nota de color amarillo")

\# Nota #2

note2 = mess.toMapiMessageItem()

note2.setSubject("Nota de color rosa")

note2.setBody("Esta es una nota de color rosa")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Pink)

\# Nota #3

note3 = mess.toMapiMessageItem()

note2.setSubject("Nota de color azul")

note2.setBody("Esta es una nota de color azul")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note3.setHeight(500)

note3.setWidth(500)

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "MapiNoteToPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

notes_folder = pst.createPredefinedFolder("Notas", Rjb::import('com.aspose.email.StandardIpmFolder').Notes)

notes_folder.addMapiMessageItem(note1)

notes_folder.addMapiMessageItem(note2)

notes_folder.addMapiMessageItem(note3)

puts "MapaNota agregada con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Agregar MapiNote a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapinotetopst.rb)