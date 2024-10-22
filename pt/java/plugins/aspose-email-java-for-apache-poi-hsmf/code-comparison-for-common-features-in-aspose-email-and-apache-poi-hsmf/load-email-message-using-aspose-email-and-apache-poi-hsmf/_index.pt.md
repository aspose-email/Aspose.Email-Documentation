---
title: "Carregar Mensagem de Email usando Aspose.Email e Apache POI HSMF"
url: /pt/java/load-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 40
type: docs
---

## **Aspose.Email - Carregar Mensagens de Email**
{{% alert color="primary" %}} 

O método **load** exposto pela classe **MailMessage** pode ser chamado pelos desenvolvedores para carregar mensagens de Email.

{{% /alert %}} 

Carregar diferentes tipos de mensagens de email

**Java**

```java

 //Criar uma instância de MailMessage carregando um arquivo Eml/Msg/Emlx/Mht

MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");

MailMessage messageEML 	= MailMessage.load(dataDir + "message.eml");

MailMessage messageEMLX = MailMessage.load(dataDir + "message.emlx");

MailMessage messageMHT 	= MailMessage.load(dataDir + "message.mht");

```
## **Apache POI HSMF - Carregar Mensagens de Email**
{{% alert color="primary" %}} 

Apache POI HSMF fornece um construtor MAPIMessages que aceita o nome do arquivo para carregar um novo MAPIMessage.

{{% /alert %}} 

**Java**

```java

 String filename = dataDir + "message.msg";

MAPIMessage msg = new MAPIMessage(filename);

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Atualizar e Salvar um Email](/email/java/loading-and-saving-message/).

{{% /alert %}}