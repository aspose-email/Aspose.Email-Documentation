---
title: "Adicionando Anexos e Texto HTML ao Arquivo Msg do Outlook no Aspose.Email"
url: /pt/net/adding-attachments-and-html-text-to-outlook-msg-file-in-aspose-email/
weight: 10
type: docs
---

Usando este método, o Microsoft Outlook deve estar instalado na máquina onde o código é executado. O trecho de código abaixo cria um arquivo MSG do Outlook com anexos e corpo HTML.
## **VSTO**
``` cs

 // Criar um objeto do tipo Outlook.Application

Outlook.Application objOutlook = new Outlook.Application();

// Criar um objeto do tipo olMailItem

Outlook.MailItem oIMailItem = objOutlook.CreateItem(Outlook.OlItemType.olMailItem);

// Definir propriedades do arquivo de mensagem, por exemplo, assunto, corpo e endereço para

// Definir assunto

oIMailItem.Subject = "Este arquivo MSG é criado usando Automação do Office.";

// Definir endereço para (destinatário)

oIMailItem.To = "to@domain.com";

// Definir corpo da mensagem de email

oIMailItem.HTMLBody = "<html><p>Este arquivo MSG é criado usando código VBA.</p>";

// Adicionar anexos à mensagem

oIMailItem.Attachments.Add("image.bmp");

oIMailItem.Attachments.Add("pic.jpeg");

// Salvar como arquivo MSG do Outlook

oIMailItem.SaveAs("testvba.msg");

// Abrir o arquivo MSG

oIMailItem.Display();

```
## **Aspose.Email**
O trecho de código abaixo usa a biblioteca Aspose.Email para .NET para criar um arquivo MSG, semelhante ao criado acima, com múltiplos anexos e corpo HTML. Como o Aspose.Email para .NET é puramente escrito em .NET, a interoperabilidade COM não é necessária. Além disso, o Microsoft Outlook 2003/2007 não precisa estar instalado na máquina. O método descrito abaixo é adequado quando o Microsoft Outlook não está instalado ou quando você deseja gerar arquivos MSG em um servidor.

Os trechos de código abaixo mostram como realizar a mesma tarefa em C# usando Aspose.Email para .NET.

``` cs

 // Criar uma instância do tipo MailMessage

MailMessage msg = new MailMessage();

// Definir propriedades da mensagem como assunto, para e corpo HTML

// Definir assunto

msg.Subject = "Este arquivo MSG é criado usando Aspose.Email para .NET";

// Definir endereço e nome do remetente

msg.Sender = new MailAddress("from@domain.com", "Nome do Remetente");

// Definir endereço e nome do destinatário

msg.To.Add(new MailAddress("to@domain.com", "Nome do Destinatário"));

// Definir corpo HTML da mensagem de email

msg.HtmlBody = @"<html><p>Este arquivo MSG é criado usando código C#.</p>" + 

	"<p>O Microsoft Outlook não precisa estar instalado na máquina que executa este código.</p>" + 

	"<p>Este método é adequado para criar arquivos MSG no lado do servidor.</html>";

// Adicionar anexos ao arquivo de mensagem

msg.Attachments.Add(new Attachment("image.bmp"));

msg.Attachments.Add(new Attachment("pic.jpeg"));

// Salvar como arquivo MSG do Outlook

string strSaveFile ="TestAspose.msg";

msg.Save(strSaveFile, MessageFormat.Msg);

```
## **Baixar Código de Exemplo**
- [Codeplex](https://asposevsto.codeplex.com/downloads/get/772938)
- [Github](https://github.com/Aspose/Aspose.Email-for-.NET/tree/master/Plugins/Aspose.Email%20Vs%20VSTO%20Outlook)
- [Sourceforge](https://sourceforge.net/projects/asposevsto/files/Aspose.Email%20Vs%20VSTO%20Outlook/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip/download)
- [Bitbucket](https://bitbucket.org/asposemarketplace/aspose-for-vsto/downloads/Adding%20Attachments%20and%20HTML%20Text%20to%20Outlook%20Msg%20File%20\(Aspose.Email\).zip)