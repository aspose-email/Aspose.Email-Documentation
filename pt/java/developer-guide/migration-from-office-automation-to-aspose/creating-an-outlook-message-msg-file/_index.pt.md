---
title: "Criando um arquivo de Mensagem do Outlook (MSG)"
url: /pt/java/creating-an-outlook-message-msg-file/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

Nossas dicas de migração mostram como os produtos Aspose podem ser usados para melhorar suas aplicações e liberá-lo da dependência de automação tradicional.

Esta dica de migração mostra como criar um arquivo de Mensagem do Outlook (MSG) usando [Automação do Microsoft Office](#office-automation) e [Aspose.Email](#asposeemail-for-java). Os exemplos de código definem as propriedades básicas do arquivo MSG - Para, Cc, Assunto e corpo HTML - antes de salvar o arquivo no disco.

{{% /alert %}} 
## **Automação do Office**
Para usar a Automação do Office, o Microsoft Outlook deve estar instalado na máquina onde o código é executado. Uma referência a Outlook.interop.dll também é necessária.
### **Exemplos de Programação**
Os seguintes trechos de código criam um arquivo MSG usando a Automação do Office.

**C#**

~~~cs

 // Cria uma nova instância do Aplicativo do Outlook

Outlook.Application objOutlook = new Outlook.Application();

// Criando uma nova mensagem do Outlook a partir da instância do Aplicativo do Outlook

Outlook.MailItem msgInterop = (Outlook.MailItem)(objOutlook.CreateItem(Outlook.OlItemType.olMailItem));

// Definir informações do destinatário

msgInterop.To = "to@domain.com";

msgInterop.CC = "cc@domain.com";

// Definir o assunto da mensagem

msgInterop.Subject = "Assunto";

// Definir algum texto HTML no corpo HTML

msgInterop.HTMLBody = "<h3>Cabeçalho HTML 3</h3> <u>Este é um texto sublinhado</u>";

// Salvar o arquivo MSG no disco local

string strMsg = @"c:\\temp\TestInterop.msg";

msgInterop.SaveAs(strMsg, Outlook.OlSaveAsType.olMSG);



~~~
## **Aspose.Email para Java**
Os exemplos abaixo usam Aspose.Email para criar o arquivo MSG do Outlook. Está escrito em Java puro e não utiliza COM Interop. A instalação do Outlook não é necessária para criar o arquivo msg dessa forma.

~~~Java

// Cria uma instância da classe Aspose.Email.MailMessage
MailMessage msg = new MailMessage();

// Definir informações dos destinatários
msg.setTo(MailAddressCollection.to_MailAddressCollection("to@domain.com"));
msg.setCC(MailAddressCollection.to_MailAddressCollection("cc@domain.com"));

// Definir o assunto
msg.setSubject("Assunto");

// Definir corpo HTML
msg.setHtmlBody("<h3>Cabeçalho HTML 3</h3> <u>Este é um texto sublinhado</u>");

// Adicionar um anexo
msg.getAttachments().addItem(new Attachment("test.txt"));

// Salvar no disco local
String strMsg = "c:\\ TestAspose.msg";
msg.save(strMsg, SaveOptions.getDefaultMsgUnicode());

~~~