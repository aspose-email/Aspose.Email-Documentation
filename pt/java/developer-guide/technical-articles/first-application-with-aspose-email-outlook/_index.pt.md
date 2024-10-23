---
title: "Primeira Aplicação com Aspose.Email Outlook"
url: /pt/java/primeira-aplicacao-com-aspose-email-outlook/
weight: 280
type: docs
---


Esta seção demonstra como usar Aspose.Email Mapi. Criamos uma pequena aplicação que carrega um arquivo de mensagem do Outlook (TestMessage.msg) e exibe o assunto, os endereços de remetente e destinatário, e o conteúdo do corpo. Siga estas etapas para criar sua primeira aplicação usando Aspose.Email Outlook.

1. Crie uma instância da classe [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage) fornecendo o caminho do arquivo de mensagem.
1. Use as propriedades públicas para exibir o assunto, de, para e corpo.

A implementação das etapas acima é demonstrada abaixo no seguinte trecho de código.



~~~Java
// Load the outlook message file
MapiMessage msg = MapiMessage.fromFile("outlookmessage.msg");

// Use the public properties
//read subject
System.out.print("Subject:" + msg.getSubject());

//sender name
System.out.print("From:" + msg.getSenderName());

//message body
System.out.print("Body:" + msg.getBody());

//Attachments
for(MapiAttachment att : msg.getAttachments())
{
    System.out.print("Attachment Name:"+att.getFileName());
    att.save(att.getFileName());
}
~~~