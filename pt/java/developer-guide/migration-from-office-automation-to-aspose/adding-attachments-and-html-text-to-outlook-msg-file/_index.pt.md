---
title: "Adicionando Anexos e Texto HTML a Arquivo MSG do Outlook"
url: /pt/java/adding-attachments-and-html-text-to-outlook-msg-file/
weight: 30
type: docs
---


{{% alert color="primary" %}} 

Nossas dicas de migração mostram como os produtos Aspose podem ser usados para melhorar suas aplicações e liberar você da dependência da automação tradicional.

Esta dica de migração mostra como criar um arquivo MSG com corpo formatado em HTML e adicionar múltiplos anexos a ele:

- Uma seção de código VBA que usa [Automação do Microsoft Office](#office-automation) para criar o arquivo MSG com anexos e corpo HTML.
- A mesma coisa realizada usando [Aspose.Email para Java](#asposeemail-for-java).

{{% /alert %}} 
## **Automação do Office**
Usando este método, o Microsoft Outlook deve estar instalado na máquina onde o código VBA é executado. O trecho de código abaixo cria um arquivo MSG do Outlook com anexos e corpo HTML.

**VBA**

~~~cs

 ' Criar um objeto do tipo Outlook.Application

Set objOutlookApplication = CreateObject("Outlook.Application")

' Criar um objeto do tipo olMailItem

Set objMsg = objOutlookApplication.CreateItem(olMailItem)

' Definir propriedades do arquivo da mensagem, por exemplo, assunto, corpo e endereço para

' Definir assunto

objMsg.Subject = "Este arquivo MSG é criado usando Automação do Office."

' Definir endereço para (destinatário)

objMsg.To = "to@domain.com"

' Definir corpo da mensagem de email

objMsg.HTMLBody = "<html><p>Este arquivo MSG é criado usando código VBA.</p>"

' Adicionar anexos à mensagem

objMsg.Attachments.Add "C:\test.bmp"

objMsg.Attachments.Add "C:\test2.jpg"

' Salvar como arquivo MSG do Outlook

objMsg.SaveAs ("c:\testvba.msg")

' Abrir o arquivo MSG

objMsg.Display


~~~
## **Aspose.Email para Java**
O trecho de código abaixo usa a biblioteca Aspose.Email para Java para criar um arquivo MSG, semelhante ao [criado acima](#office-automation), com múltiplos anexos e corpo HTML. Como o Aspose.Email para Java é escrito exclusivamente em Java, a interoperação COM não é necessária. Além disso, o Microsoft Outlook 2003/2007 não precisa estar instalado na máquina. O método descrito abaixo é adequado quando o Microsoft Outlook não está instalado ou quando você deseja gerar arquivos MSG em um servidor.

Os trechos de código abaixo mostram como realizar a mesma tarefa em Java usando Aspose.Email para Java:

~~~Java

// Criar uma instância do tipo MailMessage
MailMessage msg = new MailMessage();

// Definir propriedades da mensagem como assunto, para e corpo HTML
// Definir assunto
msg.setSubject("Este arquivo MSG é criado usando Aspose.Email para .NET");

// Definir endereço de (remetente)
msg.setSender(new MailAddress("from@domain.com", "Nome do Remetente"));

// Definir endereço e nome de (destinatário)
msg.getTo().addItem(new MailAddress("to@domain.com", "Nome do Destinatário"));

// Definir corpo HTML da mensagem de email
msg.setHtmlBody("<html><p>Este arquivo MSG é criado usando código Java.</p>" 
        + "<p>O Microsoft Outlook não precisa estar instalado na máquina que executa este código.</p>"
        + "<p>Este método é adequado para criar arquivos MSG no lado do servidor.</html>");

// Adicionar anexos ao arquivo da mensagem
msg.getAttachments().addItem(new Attachment("C:\\test.bmp"));
msg.getAttachments().addItem(new Attachment("C:\\test2.jpg"));

// Salvar como arquivo MSG do Outlook
String strSaveFile = "C:\\TestAspose.msg";

msg.save(strSaveFile, SaveOptions.getDefaultMsgUnicode());

~~~
