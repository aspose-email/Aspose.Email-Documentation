---
title: "Criando e Salvando Notas do Outlook em Ruby"
url: /pt/java/creating-and-saving-outlook-notes-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Criando e Salvando Notas do Outlook**
Para criar notas do Outlook usando **Aspose.Email Java para Ruby**, basta invocar o módulo **CreateOutlookNote**. Aqui você pode ver um exemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

note = Rjb::import('com.aspose.email.MapiNote').new

note.setSubject("Nota de cor azul")

note.setBody("Esta é uma nota de cor azul")

note.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note.setHeight(500)

note.setWidth(500)

note.save(data_dir + "MapiNote.msg", Rjb::import('com.aspose.email.NoteSaveFormat').Msg)

puts "Nota do Outlook criada com sucesso."

```
## **Baixar Código em Execução**
Baixe **Criando e Salvando Notas do Outlook (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooknote.rb)