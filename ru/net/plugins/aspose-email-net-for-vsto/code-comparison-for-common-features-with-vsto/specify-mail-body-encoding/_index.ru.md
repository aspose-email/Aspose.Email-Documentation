---
title: "Укажите кодировку текста письма"
url: /ru/net/specify-mail-body-encoding/
weight: 210
type: docs
---


## **VSTO**
Ниже приведен код для указания кодировки текста письма с помощью VSTO Outlook.

``` cs

  Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "This is the subject";

 mailItem.To = "someone@example.com";

 mailItem.Body = "This is the message.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
Ниже приведен код для указания кодировки текста письма с использованием aspose.email для .NET.

``` cs

  //Create an Instance of MailMessage class

 MailMessage message = new MailMessage();

 //From field

 message.From = "sender@sender.com";

 //To field

 message.To.Add("receiver@receiver.com");

 //Specify HtmlBody

 message.HtmlBody = "<html><body>This is the Html body</body></html>";

 //Specify BodyEncoding as ASCII

 message.BodyEncoding = Encoding.ASCII;

 //Create an instance of SmtpClient Class

 SmtpClient client = new SmtpClient();

 //Specify your mailing host server

 client.Host = "smtp.server.com";

 //Specify your mail user name

 client.Username = "Username";

 //Specify your mail password

 client.Password = "Password";

 //Specify your Port #

 client.Port = 25;

 try

 {

   //Client.Send will send this message

   client.Send(message);

   //Display 'Message Sent', only if message sent successfully

   Console.WriteLine("Message sent");

 }

 catch (Exception ex)

 {

   System.Diagnostics.Trace.WriteLine(ex.ToString());

 }

 Console.WriteLine("Press enter to quit");

 Console.Read();


```
## **Загрузить исходный код**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Specify%20Mail%20Body%20Encoding)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Загрузить пример запуска**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)
