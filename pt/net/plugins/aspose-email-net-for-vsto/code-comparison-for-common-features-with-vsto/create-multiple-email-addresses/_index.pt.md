---
title: "Criar Múltiplos Endereços de E-mail"
url: /pt/net/create-multiple-email-addresses/
weight: 70
type: docs
---


## **VSTO**
Abaixo está o código para criar múltiplos endereços usando VSTO Outlook.

``` cs



 Outlook.MailItem mailItem = (Outlook.MailItem)this.Application.CreateItem(Outlook.OlItemType.olMailItem);

 mailItem.Subject = "Este é o assunto";

 mailItem.To = "receiver1@receiver.com;receiver2@receiver.com";

 mailItem.Body = "Esta é a mensagem.";

 mailItem.BodyFormat = Microsoft.Office.Interop.Outlook.OlBodyFormat.olFormatRichText;

 mailItem.Importance = Outlook.OlImportance.olImportanceLow;

 mailItem.Display(false);


```
## **Aspose.Email**
Abaixo está o código para criar múltiplos endereços usando aspose.email para .NET.

``` cs

  //Criar uma Instância da classe MailMessage

 MailMessage message = new MailMessage();

 //Campo de Remetente

 message.From = "sender@sender.com";

 //Especificar os endereços de e-mail dos destinatários

 message.To.Add("receiver1@receiver.com");

 message.To.Add("receiver2@receiver.com");

 message.To.Add("receiver3@receiver.com");

 message.CC.Add("CC1@receiver.com");

 message.CC.Add("CC2@receiver.com");

 message.Bcc.Add("Bcc1@receiver.com");

 message.Bcc.Add("Bcc2@receiver.com");

 //Criar uma instância da Classe SmtpClient

 SmtpClient client = new SmtpClient();

 //Especificar o servidor de e-mail

 client.Host = "smtp.server.com";

 //Especificar seu nome de usuário de e-mail

 client.Username = "Username";

 //Especificar sua senha de e-mail

 client.Password = "Password";

 //Especificar sua Porta #

 client.Port = 25;

 try

 {

   //Client.Send irá enviar esta mensagem

   client.Send(message);

   //Exibir 'Mensagem Enviada', apenas se a mensagem for enviada com sucesso

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
- [url:CodePlex](https://asposeemailvsto.codeplex.com/SourceControl/latest#Code)
- [url:GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook/Code%20Comparison%20of%20Common%20Features/Create%20Multiple%20Email%20Addresses)
- [url:Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8/view/SourceCode#content)
## **Baixar Exemplo em Execução**
- [url:CodePlex](https://asposeemailvsto.codeplex.com/releases/view/620910)
- [url:GitHub](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/tag/AsposeEmailVsVSTOv1.2)
- [url:Code.MSDN](https://code.msdn.microsoft.com/Code-Comparison-of-common-4e0f39b8)