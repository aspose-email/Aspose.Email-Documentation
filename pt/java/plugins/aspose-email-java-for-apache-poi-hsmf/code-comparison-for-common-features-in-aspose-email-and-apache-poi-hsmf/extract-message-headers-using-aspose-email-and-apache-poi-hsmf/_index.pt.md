---
title: "Extrair Cabeçalhos de Mensagem usando Aspose.Email e Apache POI HSMF"
url: /pt/java/extract-message-headers-using-aspose-email-and-apache-poi-hsmf/
weight: 30
type: docs
---

## **Aspose.Email - Extrair Cabeçalhos de Mensagem**
O cabeçalho de e-mail representa um conjunto padrão de campos de cabeçalho definido pela Internet e pelo RFC incluído em mensagens de e-mail da Internet. Um cabeçalho de e-mail pode ser especificado usando a classe MailMessage. Tipos comuns de cabeçalho são definidos na classe HeaderType. É uma classe selada que funciona como uma enumeração normal.

**Java**

```java

 //Obtém os Cabeçalhos de E-mail

System.out.println("De: " 	+ message.getFrom());

System.out.println("Para: " 	+ message.getTo());

System.out.println("CC: " 	+ message.getCC());

System.out.println("Bcc: " 	+ message.getBcc());

System.out.println("Assunto: " 	+ message.getSubject());

```
## **Apache POI HSMF - Extrair Cabeçalhos de Mensagem**
A classe MAPIMessage fornece os métodos para acessar os cabeçalhos de mensagens de e-mail.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("De: " + msg.getDisplayFrom());

System.out.println("Para: " + msg.getDisplayTo());

System.out.println("CC: " + msg.getDisplayCC());

System.out.println("BCC: " + msg.getDisplayBCC());

System.out.println("Assunto: " + msg.getSubject());

```
## **Código em Execução para Download**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Código de Exemplo para Download**
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Extraindo Cabeçalhos de E-mail](/email/java/extracting-message-contents-from-emails/).

{{% /alert %}}