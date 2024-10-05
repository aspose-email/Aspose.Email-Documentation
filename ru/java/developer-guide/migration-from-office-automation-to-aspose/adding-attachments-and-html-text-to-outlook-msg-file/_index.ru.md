---
title: "Добавление вложений и HTML-текста в файл Outlook MSG"
url: /ru/java/adding-attachments-and-html-text-to-outlook-msg-file/
weight: 30
type: docs
---


{{% alert color="primary" %}} 

Наши советы по миграции показывают, как продукты Aspose могут быть использованы для улучшения ваших приложений и освобождения от зависимости от традиционной автоматизации.

Этот совет по миграции показывает, как создать файл MSG с форматированным в HTML телом и добавить к нему несколько вложений:

- Секция кода VBA, которая использует [Microsoft Office Automation](#office-automation) для создания файла MSG с вложениями и HTML телом.
- То же самое, выполненное с использованием [Aspose.Email для Java](#asposeemail-for-java).

{{% /alert %}} 
## **Office Automation**
Используя этот метод, Microsoft Outlook должен быть установлен на машине, где выполняется код VBA. Приведённый ниже фрагмент кода создает файл Outlook MSG с вложениями и HTML телом.

**VBA**

~~~cs

 ' Создать объект типа Outlook.Application

Set objOutlookApplication = CreateObject("Outlook.Application")

' Создать объект типа olMailItem

Set objMsg = objOutlookApplication.CreateItem(olMailItem)

' Установить свойства файла сообщения, такие как тема, тело и адрес назначения

' Установить тему

objMsg.Subject = "Этот файл MSG создан с использованием автоматизации Office."

' Установить адрес (получателя)

objMsg.To = "to@domain.com"

' Установить тело электронного сообщения

objMsg.HTMLBody = "<html><p>Этот файл MSG создан с использованием кода VBA.</p>"

' Добавить вложения к сообщению

objMsg.Attachments.Add "C:\test.bmp"

objMsg.Attachments.Add "C:\test2.jpg"

' Сохранить как файл Outlook MSG

objMsg.SaveAs ("c:\testvba.msg")

' Открыть файл MSG

objMsg.Display


~~~
## **Aspose.Email для Java**
Приведенный ниже фрагмент кода использует библиотеку Aspose.Email для Java для создания файла MSG, аналогичного [созданному выше](#office-automation), с несколькими вложениями и HTML телом. Поскольку Aspose.Email для Java написан полностью на Java, COM-интероп не требуется. Также Microsoft Outlook 2003/2007 не обязательно должен быть установлен на машине. Метод, описанный ниже, подходит, когда Microsoft Outlook не установлен или когда вы хотите генерировать файлы MSG на сервере.

Приведённые ниже фрагменты кода показывают, как выполнить ту же задачу на Java с использованием Aspose.Email для Java:

~~~Java

// Создать экземпляр типа MailMessage
MailMessage msg = new MailMessage();

// Установить свойства сообщения, такие как тема, адрес и HTML тело
// Установить тему
msg.setSubject("Этот файл MSG создан с использованием Aspose.Email для .NET");

// Установить адрес (отправителя)
msg.setSender(new MailAddress("from@domain.com", "Имя отправителя"));

// Установить адрес и имя (получателя)
msg.getTo().addItem(new MailAddress("to@domain.com", "Имя получателя"));

// Установить HTML тело электронного сообщения
msg.setHtmlBody("<html><p>Этот файл MSG создан с использованием кода Java.</p>" 
        + "<p>Microsoft Outlook не нужно устанавливать на машине, выполняющей этот код.</p>"
        + "<p>Этот метод подходит для создания файлов MSG на стороне сервера.</html>");

// Добавить вложения к файлу сообщения
msg.getAttachments().addItem(new Attachment("C:\\test.bmp"));
msg.getAttachments().addItem(new Attachment("C:\\test2.jpg"));

// Сохранить как файл Outlook MSG
String strSaveFile = "C:\\TestAspose.msg";

msg.save(strSaveFile, SaveOptions.getDefaultMsgUnicode());

~~~
