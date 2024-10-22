---
title: "Especificar Codificação do Corpo do E-mail"
url: /pt/net/specify-mail-body-encoding/
weight: 210
type: docs
---


## **VSTO**
Abaixo está o código para especificar a codificação do corpo do e-mail usando VSTO Outlook.

``` cs

  Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "Este é o assunto";

 mailItem.To = "someone@example.com";

 mailItem.Body = "Esta é a mensagem.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
Abaixo está o código para especificar a codificação do corpo do e-mail usando aspose.email para .NET.

``` cs

  //Crie uma instância da classe MailMessage

 MailMessage message = new MailMessage();

 //Campo De

 message.From = "sender@sender.com";

 //Campo Para

 message.To.Add("receiver@receiver.com");

 //Especificar HtmlBody

 message.HtmlBody = "<html><body>Este é o corpo Html</body></html>";

 //Especificar BodyEncoding como ASCII

 message.BodyEncoding = Encoding.ASCII;

 //Crie uma instância da classe SmtpClient

 SmtpClient client = new SmtpClient();

 //Especificar seu servidor de correio

 client.Host = "smtp.server.com";

 //Especificar seu nome de usuário de e-mail

 client.Username = "Username";

 //Especificar sua senha de e-mail

 client.Password = "Password";

 //Especificar sua porta #

 client.Port = 25;

 try

 {

   //Client.Send enviará esta mensagem

   client.Send(message);

   //Exibir 'Mensagem Enviada', somente se a mensagem for enviada com sucesso

   Console.WriteLine("Mensagem enviada");

 }

 catch (Exception ex)

 {

   System.Diagnostics.Trace.WriteLine(ex.ToString());

 }

 Console.WriteLine("Pressione enter para sair");

 Console.Read();


```
## **Baixar Código Fonte**
- [CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Specify%20Mail%20Body%20Encoding)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Baixar Exemplo em Execução**
- [CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)