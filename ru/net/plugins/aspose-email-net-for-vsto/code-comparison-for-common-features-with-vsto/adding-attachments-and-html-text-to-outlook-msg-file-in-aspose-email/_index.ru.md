---
title: "Добавление вложений и HTML-текста в файл Outlook Msg в Aspose.Email"
url: /ru/net/adding-attachments-and-html-text-to-outlook-msg-file-in-aspose-email/
weight: 10
type: docs
---


При использовании этого метода Microsoft Outlook должен быть установлен на машине, где выполняется код. Приведенный ниже код создает файл Outlook MSG с вложениями и HTML-содержимым.
## **VSTO**
``` cs

 // Создание объекта типа Outlook.Application

Outlook.Application objOutlook = new Outlook.Application();

//Создание объекта типа olMailItem

Outlook.MailItem oIMailItem = objOutlook.CreateItem(Outlook.OlItemType.olMailItem);

//Установка свойств файла сообщения, например, темы, содержимого и адреса получателя

//Установка темы

oIMailItem.Subject = "Этот MSG файл создан с использованием автоматизации Office.";

//Установка адреса получателя

oIMailItem.To = "to@domain.com";

//Установка содержимого электронного письма

oIMailItem.HTMLBody = "<html><p>Этот MSG файл создан с использованием кода VBA.</p>";

//Добавление вложений к сообщению

oIMailItem.Attachments.Add("image.bmp");

oIMailItem.Attachments.Add("pic.jpeg");

//Сохранение как файл Outlook MSG

oIMailItem.SaveAs("testvba.msg");

//Открытие файла MSG

oIMailItem.Display();

```
## **Aspose.Email**
Приведенный ниже код использует библиотеку Aspose.Email для .NET для создания файла MSG, аналогичного ранее созданному, с несколькими вложениями и HTML-содержимым. Так как Aspose.Email для .NET полностью написан на .NET, COM-интероп не требуется. Также Microsoft Outlook 2003/2007 не обязательно должен быть установлен на машине. Описанный ниже метод подходит, когда Microsoft Outlook не установлен или когда вы хотите генерировать файлы MSG на сервере.

Приведенные ниже фрагменты кода показывают, как выполнить ту же задачу на C# с использованием Aspose.Email для .NET.

``` cs

 // Создание экземпляра типа MailMessage

MailMessage msg = new MailMessage();

// Установка свойств сообщения, таких как тема, адрес получателя и HTML-содержимое

// Установка темы

msg.Subject = "Этот MSG файл создан с использованием Aspose.Email для .NET";

// Установка адреса отправителя

msg.Sender = new MailAddress("from@domain.com", "Имя отправителя");

// Установка адреса и имени получателя

msg.To.Add(new MailAddress("to@domain.com", "Имя получателя"));

// Установка HTML-содержимого электронного письма

msg.HtmlBody = @"<html><p>Этот MSG файл создан с использованием кода C#.</p>" +

	"<p>Microsoft Outlook не нужно устанавливать на машине, на которой выполняется этот код.</p>" +

	"<p>Этот метод подходит для создания файлов MSG на стороне сервера.</html>";

// Добавление вложений к файлу сообщения

msg.Attachments.Add(new Attachment("image.bmp"));

msg.Attachments.Add(new Attachment("pic.jpeg"));

// Сохранение как файл Outlook MSG

string strSaveFile ="TestAspose.msg";

msg.Save(strSaveFile, MessageFormat.Msg);

```
## **Скачать пример кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772938)
- [Github](https://github.com/Aspose/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip)