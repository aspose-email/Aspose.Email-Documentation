---
title: "Extracción de Adjunto"
url: /es/net/extracting-attachment/
weight: 120
type: docs
---

## **VSTO**
A continuación se muestra el código para extraer un adjunto usando VSTO Outlook.

``` cs

  string AttachmentFilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\";

 // Crear la clase Application y obtener el espacio de nombres

 Outlook.Application outlook = new Outlook.Application();

 Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

 object _missing = Type.Missing;

 ns.Logon(_missing, _missing, false, true);

 // Obtener información de la Bandeja de entrada en un objeto de tipo MAPIFolder

 Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

 Outlook.MailItem item = inbox.Items[0];

 for (int i = 1; i <= item.Attachments.Count; i++)

 {

   item.Attachments[i].SaveAsFile(AttachmentFilePath + item.Attachments[i].FileName);

 }

```
## **Aspose.Email**
A continuación se muestra el código para extraer un adjunto usando aspose.email para .NET.

``` cs

  string FilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\ExtractAttachment.msg";

 string AttachmentFilePath = @"E:\Aspose\Aspose VS VSTO\Sample Files\";

 //Crear una instancia de MailMessage y cargar un archivo de correo electrónico

 MailMessage mailMsg = MailMessage.Load(FilePath, MailMessageLoadOptions.DefaultEml);

 foreach (Attachment attachment in mailMsg.Attachments)

 {

   //Para mostrar el nombre del archivo del adjunto

   attachment.Save(AttachmentFilePath+attachment.Name);

   Console.WriteLine(attachment.Name);

 }

 mailMsg.From = "sender@sender.com";

 mailMsg.To.Add("receiver@receiver.com");

 SmtpClient client = new SmtpClient("smtp.server.com");

 client.Port = 25;

 client.Username = "UserName";

 client.Password = "password";

 {

   client.Send(mailMsg);

 }

```
## **Descargar Código Fuente**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Extracting%20Attachment)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Descargar Ejemplo Funcional**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)