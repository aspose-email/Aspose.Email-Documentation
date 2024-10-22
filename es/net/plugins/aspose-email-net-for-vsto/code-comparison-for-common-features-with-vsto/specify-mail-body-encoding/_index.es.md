---
title: "Especificar la codificación del cuerpo del correo"
url: /es/net/especificar-codificacion-cuerpo-correo/
weight: 210
type: docs
---


## **VSTO**
A continuación se muestra el código para especificar la codificación del cuerpo del correo usando VSTO Outlook.

``` cs

  Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "Este es el asunto";

 mailItem.To = "alguien@ejemplo.com";

 mailItem.Body = "Este es el mensaje.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
A continuación se muestra el código para especificar la codificación del cuerpo del correo usando aspose.email para .NET.

``` cs

  //Crear una instancia de la clase MailMessage

 MailMessage message = new MailMessage();

 //Campo De

 message.From = "remitente@remitente.com";

 //Campo Para

 message.To.Add("receptor@receptor.com");

 //Especificar HtmlBody

 message.HtmlBody = "<html><body>Este es el cuerpo Html</body></html>";

 //Especificar BodyEncoding como ASCII

 message.BodyEncoding = Encoding.ASCII;

 //Crear una instancia de la clase SmtpClient

 SmtpClient client = new SmtpClient();

 //Especificar su servidor de correo

 client.Host = "smtp.servidor.com";

 //Especificar su nombre de usuario de correo

 client.Username = "NombreDeUsuario";

 //Especificar su contraseña de correo

 client.Password = "Contraseña";

 //Especificar su # de Puerto

 client.Port = 25;

 try

 {

   //Client.Send enviará este mensaje

   client.Send(message);

   //Mostrar 'Mensaje Enviado', solo si el mensaje se envió correctamente

   Console.WriteLine("Mensaje enviado");

 }

 catch (Exception ex)

 {

   System.Diagnostics.Trace.WriteLine(ex.ToString());

 }

 Console.WriteLine("Presione enter para salir");

 Console.Read();


```
## **Descargar Código Fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Specify%20Mail%20Body%20Encoding)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar Ejemplo en Ejecución**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)