---
title: "Создание файла сообщений Outlook (MSG)"
url: /ru/java/creating-an-outlook-message-msg-file/
weight: 20
type: docs
---


{{% alert color="primary" %}}

Наши советы по миграции показывают, как продукты Aspose можно использовать для улучшения приложений и избавления вас от зависимости от традиционной автоматизации.

В этом совете по миграции показано, как создать файл сообщений Outlook (MSG), используя [Автоматизация работы Microsoft Office](#office-automation) and [Aspose.Email](#asposeemail-for-java). В примерах кода задаются основные свойства MSG-файла (To, Cc, Subject и текст HTML) перед сохранением файла на диск.

{{% /alert %}}
## **Автоматизация делопроизводства**
Чтобы использовать Автоматизация делопроизводства, Microsoft Outlook должен быть установлен на компьютере, на котором работает код. Также требуется ссылка на Outlook.Interop.dll.
### **Примеры программирования**
Следующие фрагменты кода создают файл MSG с помощью Автоматизация делопроизводства.

**C#**

~~~cs

 // Creates a new Outlook Application instance

Outlook.Application objOutlook = new Outlook.Application();

// Creating a new Outlook message from the Outlook Application instance

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Set recipient information

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Set the message subject

msgInterop.Subject = "Subject";

// Set some HTML text in the HTML body

msgInterop.HTMLBody = "<h3>HTML Heading 3</h3> <u>This is underlined text</u>";

// Save the MSG file in local disk

string strMsg = @"c:\\temp\TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);



~~~
## **Aspose.Электронная почта для Java**
В приведенных ниже примерах используется Aspose.Email для создания файла Outlook MSG. Он написан на чистом языке Java и не использует COM Interop. Для создания msg-файла таким образом установка Outlook не требуется.

~~~Java

// Create an instance of the Aspose.Email.MailMessage class
MailMessage msg = new MailMessage();

// Set recipients information
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setCC(MailAddressCollection.to_MailAddressCollection("cc@domain.com"));

// Set the subject
msg.setSubject("Subject");

// Set HTML body
msg.setHtmlBody("<h3>HTML Heading 3</h3> <u>This is underlined text</u>");

// Add an attachment
msg.getAttachments().addItem(new Attachment("test.txt"));

// Save it in local disk
String strMsg = "c:\\ TestAspose.msg";
msg.save(strMsg, SaveOptions.getDefaultMsgUnicode());

~~~