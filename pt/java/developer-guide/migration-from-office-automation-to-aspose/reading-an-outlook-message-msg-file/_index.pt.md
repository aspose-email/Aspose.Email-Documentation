---
title: "Lendo um arquivo de mensagem do Outlook (MSG)"
url: /pt/java/lendo-um-arquivo-de-mensagem-do-outlook-msg/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Nossas dicas de migração mostram como os produtos Aspose podem ser usados para melhorar suas aplicações e libertá-lo da dependência da automação tradicional.

Esta dica de migração mostra como ler um arquivo de mensagem do Microsoft Outlook e exibir seu conteúdo na tela usando tanto a [Automação do Microsoft Office](#office-automation) quanto o código [Aspose.Email](#asposeemail-for-java). O código de exemplo abaixo mostra apenas o conteúdo no console para lhe dar uma ideia de como funciona. Use os trechos de código em suas próprias aplicações Windows, web ou outras.

{{% /alert %}} 
## **Automação do Office**
Para usar objetos de Automação do Office para Microsoft Outlook, você precisa adicionar referências às bibliotecas Microsoft Office e Microsoft Office Interop para Outlook ao seu projeto.
### **Exemplos de Programação**
**C#**

~~~cs

// Adicione os namespaces

using Microsoft.Office;

using Microsoft.Office.Interop.Outlook;

// Crie uma nova classe Application

Application app = new Application();

// Crie um objeto MailItem

MailItem item = (MailItem)outlook.CreateItemFromTemplate(@"d:\temp\test.msg", Type.Missing);

// Acesse diferentes campos da mensagem

System.Console.WriteLine(string.Format("Assunto:{0}", item.Subject));

System.Console.WriteLine(string.Format("Endereço de Email do Remetente:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("Nome do Remetente:{0}", item.SenderName));

System.Console.WriteLine(string.Format("PARA:{0}", item.To));

System.Console.WriteLine(string.Format("CC:{0}", item.CC));

System.Console.WriteLine(string.Format("BCC:{0}", item.BCC));

System.Console.WriteLine(string.Format("Corpo Html:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Corpo Texto:{0}", item.Body));


~~~
## **Aspose.Email para Java**
O seguinte trecho de código faz a mesma coisa que [o código acima](/#office-automation) usando Aspose.Email para Java.

Para acessar os objetos [Aspose.Email Outlook](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage), você precisa adicionar uma referência ao Aspose.Email ao seu projeto.
### **Exemplos de Programação**

~~~java

// Crie um novo objeto do tipo MapiMessage
MapiMessage msg = MapiMessage.fromFile("d:\\temp\\test.msg");

// Acesse os campos da mensagem
System.out.println("Assunto: " + msg.getSubject());
System.out.println("Endereço de Email do Remetente: " + msg.getSenderEmailAddress());
System.out.println("Nome do Remetente:{0}" + msg.getSenderName());
System.out.println("PARA:{0}" + msg.getDisplayTo());
System.out.println("CC:{0}" + msg.getDisplayCc());
System.out.println("BCC:{0}" + msg.getDisplayBcc());
System.out.println("Corpo Html:{0}" + msg.getBodyHtml());
System.out.println("Corpo Texto:{0}" + msg.getBody());
System.out.println("Corpo Rtf:{0}" + msg.getBodyRtf());


~~~
