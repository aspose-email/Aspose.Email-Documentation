---
title: "Crear múltiples direcciones de correo electrónico"
url: /es/net/create-multiple-email-address/
weight: 60
type: docs
---



## **VSTO**
A continuación se muestra el código para crear múltiples direcciones usando VSTO Outlook.

``` cs

  Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "Este es el asunto";

 mailItem.To = "receiver1@receiver.com;receiver2@receiver.com";

 mailItem.Body = "Este es el mensaje.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
A continuación se muestra el código para crear múltiples direcciones usando aspose.email para .NET.

``` cs

  //Crear una instancia de la clase MailMessage

 MailMessage message = new MailMessage();

 //Campo De

 message.From = "sender@sender.com";

 //Especificar las direcciones de correo de los destinatarios

 message.To.Add("receiver1@receiver.com");

 message.To.Add("receiver2@receiver.com");

 message.To.Add("receiver3@receiver.com");

 message.CC.Add("CC1@receiver.com");

 message.CC.Add("CC2@receiver.com");

 message.Bcc.Add("Bcc1@receiver.com");

 message.Bcc.Add("Bcc2@receiver.com");

 //Crear una instancia de la clase SmtpClient

 SmtpClient client = new SmtpClient();

 //Especificar su servidor de correo

 client.Host = "smtp.server.com";

 //Especificar su nombre de usuario de correo

 client.Username = "Username";

 //Especificar su contraseña de correo

 client.Password = "Password";

 //Especificar su número de puerto

 client.Port = 25;

 try

 {

   //Client.Send enviará este mensaje

   client.Send(message);

   //Mostrar 'Mensaje enviado', solo si el mensaje se envió con éxito

   Console.WriteLine("Mensaje enviado");

 }

 catch (Exception ex)

 {

   System.Diagnostics.Trace.WriteLine(ex.ToString());

 }

 Console.WriteLine("Presione enter para salir");

 Console.Read();

```
## **Descargar código fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20Multiple%20Email%20Addresses)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar ejemplo en ejecución**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)