---
title: "Crear varias direcciones de correo electrónico"
url: /es/net/create-multiple-email-address/
weight: 60
type: docs
---



## **VSTO**
A continuación se muestra el código para crear varias direcciones con VSTO Outlook.

``` cs

  Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "This is the subject";

 mailItem.To = "receiver1@receiver.com;receiver2@receiver.com";

 mailItem.Body = "This is the message.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
A continuación se muestra el código para crear varias direcciones con aspose.email para.NET.

``` cs

  //Create an Instance of MailMessage class

 MailMessage message = new MailMessage();

 //From field

 message.From = "sender@sender.com";

 //Specify the recipients' mail addresses

 message.To.Add("receiver1@receiver.com");

 message.To.Add("receiver2@receiver.com");

 message.To.Add("receiver3@receiver.com");

 message.CC.Add("CC1@receiver.com");

 message.CC.Add("CC2@receiver.com");

 message.Bcc.Add("Bcc1@receiver.com");

 message.Bcc.Add("Bcc2@receiver.com");

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
## **Descargar código fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20Multiple%20Email%20Addresses)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar Running Example**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)
