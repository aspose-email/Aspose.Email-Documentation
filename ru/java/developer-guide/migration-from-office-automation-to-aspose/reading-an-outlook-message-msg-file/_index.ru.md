---
title: "Чтение файла сообщения Outlook (MSG)"
url: /ru/java/reading-an-outlook-message-msg-file/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Наши советы по миграции показывают, как продукты Aspose могут быть использованы для улучшения ваших приложений и освобождения от зависимости от традиционной автоматизации.

Этот совет по миграции показывает, как читать файл сообщения Microsoft Outlook и отображать его содержимое на экране с использованием как [Microsoft Office Automation](#office-automation), так и [Aspose.Email](#asposeemail-for-java) кода. Пример кода ниже показывает только содержимое в консоли, чтобы дать вам представление о том, как это работает. Используйте эти фрагменты кода в своем собственном приложении для Windows, веб-приложении или другом.

{{% /alert %}} 
## **Office Automation**
Чтобы использовать объекты автоматизации Office для Microsoft Outlook, вам нужно добавить ссылки на библиотеки Microsoft Office и Microsoft Office Interop для Outlook в ваш проект.
### **Примеры программирования**
**C#**

~~~cs

// Добавьте пространства имен

using Microsoft.Office;

using Microsoft.Office.Interop.Outlook;

// Создайте новый объект класса Application

Application app = new Application();

// Создайте объект MailItem

MailItem item = (MailItem)outlook.CreateItemFromTemplate(@"d:\temp\test.msg", Type.Missing);

// Получите доступ к различным полям сообщения

System.Console.WriteLine(string.Format("Тема:{0}", item.Subject));

System.Console.WriteLine(string.Format("Адрес электронной почты отправителя:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("Имя отправителя:{0}", item.SenderName));

System.Console.WriteLine(string.Format("Кому:{0}", item.To));

System.Console.WriteLine(string.Format("Копия:{0}", item.CC));

System.Console.WriteLine(string.Format("СК:{0}", item.BCC));

System.Console.WriteLine(string.Format("Html Тело:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Текстовое тело:{0}", item.Body));


~~~
## **Aspose.Email для Java**
Следующий фрагмент кода выполняет ту же задачу, что и [код выше](/#office-automation), используя Aspose.Email для Java.

Чтобы получить доступ к объектам [Aspose.Email Outlook](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage), вам нужно добавить ссылку на Aspose.Email в ваш проект.
### **Примеры программирования**

~~~java

// Создайте новый объект типа MapiMessage
MapiMessage msg = MapiMessage.fromFile("d:\\temp\\test.msg");

// Получите доступ к полям сообщения
System.out.println("Тема: " + msg.getSubject());
System.out.println("Адрес электронной почты отправителя: " + msg.getSenderEmailAddress());
System.out.println("Имя отправителя:{0}" + msg.getSenderName());
System.out.println("Кому:{0}" + msg.getDisplayTo());
System.out.println("Копия:{0}" + msg.getDisplayCc());
System.out.println("СК:{0}" + msg.getDisplayBcc());
System.out.println("Html Тело:{0}" + msg.getBodyHtml());
System.out.println("Текстовое тело:{0}" + msg.getBody());
System.out.println("Rtf Тело:{0}" + msg.getBodyRtf());


~~~