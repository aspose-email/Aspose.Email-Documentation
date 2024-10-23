---
title: "Lendo um Arquivo de Mensagem do Outlook (MSG) no Aspose.Email"
url: /pt/net/lendo-um-arquivo-de-mensagem-do-outlook-msg-no-aspose-email/
weight: 190
type: docs
---

Para usar objetos de Automação do Office para Microsoft Outlook, você precisa adicionar referências às bibliotecas do Microsoft Office e Microsoft Office Interop para Outlook ao seu projeto.  
### **VSTO**  
``` cs  

 // Criar uma nova classe de aplicativo  

_Application outlook = new Outlook.Application();  

// Criar um objeto MailItem  

MailItem item = (MailItem)outlook.CreateItemFromTemplate("test.msg", Type.Missing);  

// Acessar diferentes campos da mensagem  

System.Console.WriteLine(string.Format("Assunto:{0}", item.Subject));  

System.Console.WriteLine(string.Format("Endereço de Email do Remetente:{0}", item.SenderEmailAddress));  

System.Console.WriteLine(string.Format("Nome do Remetente:{0}", item.SenderName));  

System.Console.WriteLine(string.Format("PARA:{0}", item.To));  

System.Console.WriteLine(string.Format("CC:{0}", item.CC));  

System.Console.WriteLine(string.Format("BCC:{0}", item.BCC));  

System.Console.WriteLine(string.Format("Corpo Html:{0}", item.HTMLBody));  

System.Console.WriteLine(string.Format("Corpo de Texto:{0}", item.Body));  

```  
### **Aspose.Email**  
Para acessar os objetos Aspose.Email.Outlook, você precisa adicionar uma referência ao Aspose.Email em seu projeto.  

``` cs  

  // Criar participantes da reunião  

MailAddressCollection attendees = new MailAddressCollection();  

attendees.Add("recipient1@domain.com");  

attendees.Add("recipient2@domain.com");  

// Configurar o compromisso  

Appointment app = new Appointment(  

    "Localização", // local da reunião  

    DateTime.Now, // data de início  

    DateTime.Now.AddHours(1), // data de término  

    new MailAddress("organizer@domain.com"), // organizador  

    attendees); // participantes  

// Configurar a mensagem que precisa ser enviada  

MailMessage msg = new MailMessage();  

msg.From = "from@domain.com";  

msg.To = "to@domain.com";  

msg.Subject = "pedido de compromisso";  

msg.Body = "você está convidado";  

// Adicionar solicitação de reunião à mensagem  

msg.AddAlternateView(app.RequestApointment());  

// Configurar o cliente SMTP para enviar e-mail com solicitação de reunião  

SmtpClient client = new SmtpClient("host", 25 ,"user", "password");  

client.Send(msg);  

```  
## **Baixar Código de Exemplo**  
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772943)  
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Reading.an.Outlook.Message.MSG.File.Aspose.Email.zip)  
- [Sourceforge](http://goo.gl/TpCQPp)  
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Reading%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)  