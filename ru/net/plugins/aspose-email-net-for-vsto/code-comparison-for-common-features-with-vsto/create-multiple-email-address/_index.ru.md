---
title: "Создание нескольких адресов электронной почты"
url: /ru/net/create-multiple-email-address/
weight: 60
type: docs
---



## **VSTO**
Ниже представлен код для создания нескольких адресов с использованием VSTO Outlook.

``` cs

  Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "Это тема";

 mailItem.To = "receiver1@receiver.com;receiver2@receiver.com";

 mailItem.Body = "Это сообщение.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
Ниже представлен код для создания нескольких адресов с использованием aspose.email для .NET.

``` cs

  //Создание экземпляра класса MailMessage

 MailMessage message = new MailMessage();

 //Поле From

 message.From = "sender@sender.com";

 //Укажите адреса электронной почты получателей

 message.To.Add("receiver1@receiver.com");

 message.To.Add("receiver2@receiver.com");

 message.To.Add("receiver3@receiver.com");

 message.CC.Add("CC1@receiver.com");

 message.CC.Add("CC2@receiver.com");

 message.Bcc.Add("Bcc1@receiver.com");

 message.Bcc.Add("Bcc2@receiver.com");

 //Создание экземпляра класса SmtpClient

 SmtpClient client = new SmtpClient();

 //Укажите ваш почтовый сервер

 client.Host = "smtp.server.com";

 //Укажите ваше имя пользователя

 client.Username = "Username";

 //Укажите ваш пароль

 client.Password = "Password";

 //Укажите номер порта

 client.Port = 25;

 try

 {

   //Client.Send отправит это сообщение

   client.Send(message);

   //Вывод 'Сообщение отправлено', только если сообщение было успешно отправлено

   Console.WriteLine("Сообщение отправлено");

 }

 catch (Exception ex)

 {

   System.Diagnostics.Trace.WriteLine(ex.ToString());

 }

 Console.WriteLine("Нажмите Enter, чтобы выйти");

 Console.Read();

```
## **Скачать исходный код**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20Multiple%20Email%20Addresses)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Скачать рабочий пример**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)