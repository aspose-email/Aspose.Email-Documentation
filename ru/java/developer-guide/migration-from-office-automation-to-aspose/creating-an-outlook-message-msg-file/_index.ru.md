---
title: "Создание файла сообщения Outlook (MSG)"
url: /ru/java/creating-an-outlook-message-msg-file/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

Наши советы по миграции показывают, как продукты Aspose могут быть использованы для улучшения ваших приложений и освобождения вас от зависимости от традиционной автоматизации.

Этот совет по миграции показывает, как создать файл сообщения Outlook (MSG) с использованием [Microsoft Office Automation](#office-automation) и [Aspose.Email](#asposeemail-for-java). Примеры кода устанавливают основные свойства файла MSG - Кому, Копия, Тема и HTML-содержимое - перед сохранением файла на диск.

{{% /alert %}} 
## **Автоматизация Office**
Для использования автоматизации Office на машине, где выполняется код, должна быть установлена Microsoft Outlook. Также требуется ссылка на Outlook.interop.dll.
### **Примеры программирования**
Следующие фрагменты кода создают файл MSG с использованием автоматизации Office.

**C#**

~~~cs

 // Создает новый экземпляр приложения Outlook

Outlook.Application objOutlook = new Outlook.Application();

// Создание нового сообщения Outlook из экземпляра приложения Outlook

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Установка информации о получателе

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Установка темы сообщения

msgInterop.Subject = "Тема";

// Установка текста HTML в HTML-содержимом

msgInterop.HTMLBody = "<h3>HTML Заголовок 3</h3> <u>Это подчеркиваемый текст</u>";

// Сохранение файла MSG на локальном диске

string strMsg = @"c:\\temp\TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);



~~~
## **Aspose.Email для Java**
Примеры ниже используют Aspose.Email для создания файла MSG Outlook. Он написан на чистом Java и не использует COM Interop. Установка Outlook не требуется для создания файла msg таким образом.

~~~Java

// Создание экземпляра класса Aspose.Email.MailMessage
MailMessage msg = new MailMessage();

// Установка информации о получателях
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setCC(MailAddressCollection.to_MailAddressCollection("cc@domain.com"));

// Установка темы
msg.setSubject("Тема");

// Установка HTML-содержимого
msg.setHtmlBody("<h3>HTML Заголовок 3</h3> <u>Это подчеркиваемый текст</u>");

// Добавление вложения
msg.getAttachments().addItem(new Attachment("test.txt"));

// Сохранение на локальном диске
String strMsg = "c:\\ TestAspose.msg";
msg.save(strMsg, SaveOptions.getDefaultMsgUnicode());

~~~