---
title: "Добавление вложений и HTML-текста в файл Outlook MSG"
url: /ru/java/adding-attachments-and-html-text-to-outlook-msg-file/
weight: 30
type: docs
---


{{% alert color="primary" %}}

Наши советы по миграции показывают, как продукты Aspose можно использовать для улучшения приложений и избавления вас от зависимости от традиционной автоматизации.

В этом совете по миграции показано, как создать файл MSG с телом в формате HTML и добавить к нему несколько вложений:

- Раздел кода VBA, в котором используется [Автоматизация работы Microsoft Office](#office-automation) для создания файла MSG с вложениями и телом HTML.
- То же самое было сделано с помощью [Aspose.Электронная почта для Java](#asposeemail-for-java).

{{% /alert %}}
## **Автоматизация делопроизводства**
Используя этот метод, Microsoft Outlook должен быть установлен на компьютере, где работает код VBA. Приведенный ниже фрагмент кода создает MSG-файл Outlook с вложениями и телом HTML.

**VBA**

~~~cs

 ' Create an object of type Outlook.Application

Set objOutlookApplication = CreateObject("Outlook.Application")

' Create an object of type olMailItem

Set objMsg = objOutlookApplication.CreateItem(olMailItem)

' Set properties of the message file e.g. subject, body and to address

' Set subject

objMsg.Subject = "This MSG file is created using Автоматизация делопроизводства."

' Set to (recipient) address

objMsg.To = "to@domain.com"

' Set body of the email message

objMsg.HTMLBody = "<html><p>This MSG file is created using VBA code.</p>"

' Add attachments to the message

objMsg.Attachments.Add "C:\test.bmp"

objMsg.Attachments.Add "C:\test2.jpg"

' Save as Outlook MSG file

objMsg.SaveAs ("c:\testvba.msg")

' Open the MSG file

objMsg.Display


~~~
## **Aspose.Электронная почта для Java**
В приведенном ниже фрагменте кода используется библиотека Aspose.Email для Java для создания файла MSG, аналогичного [тот, который создан выше](#office-automation), с несколькими вложениями и телом HTML. Поскольку Aspose.Email для Java написан исключительно на Java, взаимодействие COM не требуется. Кроме того, на компьютере не нужно устанавливать Microsoft Outlook 2003/2007. Описанный ниже метод подходит, когда Microsoft Outlook не установлен или когда вы хотите создать файлы MSG на сервере.

В приведенных ниже фрагментах кода показано, как выполнить ту же задачу на Java с помощью Aspose.Email для Java:

~~~Java

// Create an instance of type MailMessage
MailMessage msg = new MailMessage();

// Set properties of message like subject, to and HTML body
// Set subject
msg.setSubject("This MSG file is created using Aspose.Email for .NET");

// Set from (sender) address
msg.setSender(new MailAddress("from@domain.com", "From Name"));

// Set to (recipient) address and name
msg.getTo().addItem(new MailAddress("to@domain.com", "To Name"));

// Set HTML body of the email message
msg.setHtmlBody("<html><p>This MSG file is created using Java code.</p>"
        + "<p>Microsoft Outlook does not need to be installed on the machine running this code.</p>"
        + "<p>This method is suitable for creating MSG files on the server side.</html>");

// Add attachments to the message file
msg.getAttachments().addItem(new Attachment("C:\\test.bmp"));
msg.getAttachments().addItem(new Attachment("C:\\test2.jpg"));

// Save as Outlook MSG file
String strSaveFile = "C:\\TestAspose.msg";

msg.save(strSaveFile, SaveOptions.getDefaultMsgUnicode());

~~~
