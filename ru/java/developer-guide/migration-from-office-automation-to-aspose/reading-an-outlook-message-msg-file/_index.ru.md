---
title: "Чтение файла сообщений Outlook (MSG)"
url: /ru/java/reading-an-outlook-message-msg-file/
weight: 10
type: docs
---


{{% alert color="primary" %}}

Наши советы по миграции показывают, как продукты Aspose можно использовать для улучшения приложений и избавления вас от зависимости от традиционной автоматизации.

В этом совете по миграции показано, как читать файл сообщений Microsoft Outlook и отображать его содержимое на экране, используя оба метода. [Автоматизация работы Microsoft Office](#office-automation) and [Aspose.Email](#asposeemail-for-java) код. Приведенный ниже пример кода показывает содержимое консоли только для того, чтобы дать вам представление о том, как она работает. Используйте фрагменты кода в своем собственном приложении для Windows, в Интернете или другом приложении.

{{% /alert %}}
## **Автоматизация делопроизводства**
Чтобы использовать объекты автоматизации делопроизводства для Microsoft Outlook, необходимо добавить в проект ссылки на библиотеки Microsoft Office и Microsoft Office Interop для Outlook.
### **Примеры программирования**
**C#**

~~~cs

// Add the namespaces

using Microsoft.Office;

using Microsoft.Office.Interop.Outlook;

// Create a new Application Class

Application app = new Application();

// Create a MailItem object

MailItem item = (MailItem)outlook.CreateItemFromTemplate(@"d:\temp\test.msg", Type.Missing);

// Access different fields of the message

System.Console.WriteLine(string.Format("Subject:{0}", item.Subject));

System.Console.WriteLine(string.Format("Sender Email Address:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("SenderName:{0}", item.SenderName));

System.Console.WriteLine(string.Format("TO:{0}", item.To));

System.Console.WriteLine(string.Format("CC:{0}", item.CC));

System.Console.WriteLine(string.Format("BCC:{0}", item.BCC));

System.Console.WriteLine(string.Format("Html Body:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Text Body:{0}", item.Body));


~~~
## **Aspose.Электронная почта для Java**
Следующий фрагмент кода делает то же самое, что и [приведенный выше код](/#office-automation) используя Aspose.Email для Java.

Чтобы получить доступ к [Aspose.Электронная почта Outlook](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) объекты, вам нужно добавить ссылку на Aspose.Email в свой проект.
### **Примеры программирования**

~~~java

// Create a new object of type MapiMessage
MapiMessage msg = MapiMessage.fromFile("d:\\temp\\test.msg");

// Access the fields of the message
System.out.println("Subject: " + msg.getSubject());
System.out.println("Sender Email Address: " + msg.getSenderEmailAddress());
System.out.println("SenderName:{0}" + msg.getSenderName());
System.out.println("TO:{0}" + msg.getDisplayTo());
System.out.println("CC:{0}" + msg.getDisplayCc());
System.out.println("BCC:{0}" + msg.getDisplayBcc());
System.out.println("Html Body:{0}" + msg.getBodyHtml());
System.out.println("Text Body:{0}" + msg.getBody());
System.out.println("Rtf Body:{0}" + msg.getBodyRtf());


~~~
