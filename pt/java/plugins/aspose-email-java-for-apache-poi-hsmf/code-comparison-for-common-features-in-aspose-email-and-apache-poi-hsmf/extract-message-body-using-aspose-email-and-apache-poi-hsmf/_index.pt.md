---
title: "Extrair Corpo da Mensagem usando Aspose.Email e Apache POI HSMF"
url: /pt/java/extract-message-body-using-aspose-email-and-apache-poi-hsmf/
weight: 20
type: docs
---

## **Aspose.Email - Extrair Corpo da Mensagem**
O MailMessage representa uma mensagem de email e permite que os desenvolvedores acessem as propriedades da mensagem de email. As informações do cabeçalho (discutidas em [Extraindo Cabeçalhos de Email](http://www.aspose.com/docs/display/emailjava/Extracting+Email+Headers)) podem ser extraídas e manipuladas de diferentes maneiras.

**Java**

```java

 MailMessage msg = MailMessage.load(dataDir + "message.msg");

System.out.println("Corpo:"+ msg.getBody());

System.out.println("Corpo de Texto:"+ msg.getTextBody());

System.out.println("Corpo de Texto HTML:"+ msg.getHtmlBody());

```
## **Apache POI HSMF - Extrair Corpo da Mensagem**
MAPIMessage pode acessar o corpo da mensagem de email.

**Java**

```java

 MAPIMessage msg = new MAPIMessage(dataDir + "message.msg");

System.out.println("Corpo de Texto:"+ msg.getTextBody());

```
## **Download do Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Download do Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/extractor/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/extractor)

{{% alert color="primary" %}} 

Para mais detalhes, acesse [Exibindo Informações de Email na Tela](/email/java/display-information-in-custom-order-in-mhtml-files/).

{{% /alert %}}