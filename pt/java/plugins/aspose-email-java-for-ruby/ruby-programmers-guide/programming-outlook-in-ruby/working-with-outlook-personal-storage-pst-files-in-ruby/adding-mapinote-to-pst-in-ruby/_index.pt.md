---
title: "Adicionando MapiNote ao PST em Ruby"
url: /pt/java/adding-mapinote-to-pst-in-ruby/
weight: 50
type: docs
---

## **Aspose.Email - Adicionando MapiNote ao PST**
Para adicionar MapiNote ao PST usando **Aspose.Email Java para Ruby**, basta invocar o módulo **AddMapiNoteToPST**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

mess = Rjb::import('com.aspose.email.MapiMessage').fromFile(data_dir + "MapiNote.msg")

\# Nota #1

note1 = mess.toMapiMessageItem()

note1.setSubject("Nota de cor amarela")

note1.setBody("Esta é uma nota de cor amarela")

\# Nota #2

note2 = mess.toMapiMessageItem()

note2.setSubject("Nota de cor rosa")

note2.setBody("Esta é uma nota de cor rosa")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Pink)

\# Nota #3

note3 = mess.toMapiMessageItem()

note2.setSubject("Nota de cor azul")

note2.setBody("Esta é uma nota de cor azul")

note2.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note3.setHeight(500)

note3.setWidth(500)

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "MapiNoteToPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

notes_folder = pst.createPredefinedFolder("Notas", Rjb::import('com.aspose.email.StandardIpmFolder').Notes)

notes_folder.addMapiMessageItem(note1)

notes_folder.addMapiMessageItem(note2)

notes_folder.addMapiMessageItem(note3)

puts "MapiNote adicionado com sucesso."

```
## **Baixar Código em Execução**
Baixe **Adicionando MapiNote ao PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapinotetopst.rb)