---
title: Указать кодировку тела письма
type: docs
weight: 210
url: /net/specify-mail-body-encoding/
---


## **VSTO**
Ниже приведен код для указания кодировки тела письма с использованием VSTO Outlook.

``` cs

  Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "Это тема";

 mailItem.To = "someone@example.com";

 mailItem.Body = "Это сообщение.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
Ниже приведен код для указания кодировки тела письма с использованием aspose.email для .NET.

``` cs

  //Создать экземпляр класса MailMessage

 MailMessage message = new MailMessage();

 //Поле From

 message.From = "sender@sender.com";

 //Поле To

 message.To.Add("receiver@receiver.com");

 //Указать HtmlBody

 message.HtmlBody = "<html><body>Это Html тело</body></html>";

 //Указать BodyEncoding как ASCII

 message.BodyEncoding = Encoding.ASCII;

 //Создать экземпляр класса SmtpClient

 SmtpClient client = new SmtpClient();

 //Указать ваш почтовый сервер

 client.Host = "smtp.server.com";

 //Указать ваше имя пользователя для почты

 client.Username = "Username";

 //Указать ваш пароль от почты

 client.Password = "Password";

 //Указать номер порта

 client.Port = 25;

 try

 {

   //Client.Send отправит это сообщение

   client.Send(message);

   //Вывести 'Сообщение отправлено', только если сообщение было отправлено успешно

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
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Specify%20Mail%20Body%20Encoding)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Скачать рабочий пример**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)