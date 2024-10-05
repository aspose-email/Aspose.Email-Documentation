---
title: "Создание файла сообщения Outlook (MSG) в Aspose.Email"
url: /ru/net/creating-an-outlook-message-msg-file-in-aspose-email/
weight: 90
type: docs
---


Для использования Office Automation на машине, где выполняется код, должен быть установлен Microsoft Outlook. Также требуется ссылка на Outlook.interop.dll.
### **VSTO**
``` cs

 // Создание нового экземпляра Outlook Application

Outlook.Application objOutlook = new Outlook.Application();

// Создание нового сообщения Outlook из экземпляра Outlook Application

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Установка информации о получателе

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Установка темы сообщения

msgInterop.Subject = "Тема";

// Установка некоторого HTML текста в HTML тело

msgInterop.HTMLBody = "<h3>HTML Заголовок 3</h3> <u>Этот текст с подчеркиванием</u>";

// Сохранение файла MSG на локальном диске

string strMsg = "TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);


```
### **Aspose.Email**
Примеры ниже используют Aspose.Email для создания файла MSG Outlook. Он написан на чистом .NET и не использует COM Interop. Установка Outlook не требуется для создания файла msg таким образом.

``` cs

 // Создание экземпляра класса Aspose.Email.MailMessage

MailMessage msg = new MailMessage();

// Установка информации о получателях

msg.To = "to@domain.com";

msg.CC = "cc@domain.com";

// Установка темы

msg.Subject = "Тема";

// Установка HTML тела

msg.HtmlBody = "<h3>HTML Заголовок 3</h3> <u>Этот текст с подчеркиванием</u>";

// Добавление вложения

msg.Attachments.Add(new Attachment("image.bmp"));

// Сохранение на локальном диске

string strMsg = "TestAspose.msg";

msg.Save(strMsg, MessageFormat.Msg);

```
## **Скачать образец кода**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772940)
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Sourceforge](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Creating%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)