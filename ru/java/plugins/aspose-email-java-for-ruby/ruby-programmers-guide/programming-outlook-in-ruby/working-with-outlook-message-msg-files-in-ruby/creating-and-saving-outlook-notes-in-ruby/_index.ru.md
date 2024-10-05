---
title: "Создание и сохранение заметок Outlook в Ruby"
url: /ru/java/creating-and-saving-outlook-notes-in-ruby/
weight: 20
type: docs
---

## **Aspose.Email - Создание и сохранение заметок Outlook**
Чтобы создать заметки Outlook с использованием **Aspose.Email Java для Ruby**, просто вызовите модуль **CreateOutlookNote**. Здесь вы можете увидеть пример кода.

**Код Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

note = Rjb::import('com.aspose.email.MapiNote').new

note.setSubject("Заметка синего цвета")

note.setBody("Это заметка синего цвета")

note.setColor(Rjb::import('com.aspose.email.NoteColor').Blue)

note.setHeight(500)

note.setWidth(500)

note.save(data_dir + "MapiNote.msg", Rjb::import('com.aspose.email.NoteSaveFormat').Msg)

puts "Заметка Outlook создана успешно."

```
## **Скачать работающий код**
Скачайте **Создание и сохранение заметок Outlook (Aspose.Email)** с любого из нижеуказанных социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createoutlooknote.rb)