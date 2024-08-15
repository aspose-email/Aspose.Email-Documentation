---
title: "Создание и сохранение заметок Outlook в Ruby"
url: /ru/java/creating-and-saving-outlook-notes-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - создание и сохранение заметок Outlook**
Для создания заметок Outlook с помощью **Aspose.Электронная почта Java для Ruby**, просто вызовите **CreateOutlookNote** модуль. Здесь вы можете увидеть пример кода.

**Код Ruby**

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
## **Загрузить рабочий код**
Download **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooknote.rb)
