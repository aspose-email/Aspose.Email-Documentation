---
title: "Criando um Arquivo de Mensagem do Outlook (MSG) no Aspose.Email"
url: /pt/net/creating-an-outlook-message-msg-file-in-aspose-email/
weight: 90
type: docs
---


Para usar a Automação do Office, o Microsoft Outlook deve estar instalado na máquina em que o código está sendo executado. Também é necessária uma referência ao Outlook.interop.dll.
### **VSTO**
``` cs

 // Cria uma nova instância do Aplicativo do Outlook

Outlook.Application objOutlook = new Outlook.Application();

// Criando uma nova mensagem do Outlook a partir da instância do Aplicativo do Outlook

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Define as informações do destinatário

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Define o assunto da mensagem

msgInterop.Subject = "Assunto";

// Define algum texto HTML no corpo HTML

msgInterop.HTMLBody = "<h3>Cabeçalho HTML 3</h3> <u>Este é um texto sublinhado</u>";

// Salva o arquivo MSG no disco local

string strMsg = "TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);


```
### **Aspose.Email**
Os exemplos abaixo utilizam o Aspose.Email para criar o arquivo MSG do Outlook. Está escrito em .NET puro e não usa COM Interop. A instalação do Outlook não é necessária para criar o arquivo msg dessa forma.

``` cs

 // Cria uma instância da classe Aspose.Email.MailMessage

MailMessage msg = new MailMessage();

// Define as informações dos destinatários

msg.To = "to@domain.com";

msg.CC = "cc@domain.com";

// Define o assunto

msg.Subject = "Assunto";

// Define o corpo HTML

msg.HtmlBody = "<h3>Cabeçalho HTML 3</h3> <u>Este é um texto sublinhado</u>";

// Adiciona um anexo

msg.Attachments.Add(new Attachment("image.bmp"));

// Salva no disco local

string strMsg = "TestAspose.msg";

msg.Save(strMsg, MessageFormat.Msg);

```
## **Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772940)
- [Github](https://github.com/asposemarketplace/Aspose_for_VSTO/releases/download/5/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Sourceforge](https://github.com/aspose-email/Aspose.Email-for-.NET/releases/download/AsposeEmailVsVSTOv1.1/Creating.an.Outlook.Message.MSG.File.Aspose.Email.zip)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Creating%20an%20Outlook%20Message%20\(MSG\)%20File%20\(Aspose.Email\).zip)