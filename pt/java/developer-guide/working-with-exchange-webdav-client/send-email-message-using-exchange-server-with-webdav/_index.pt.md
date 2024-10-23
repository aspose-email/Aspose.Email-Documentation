---
title: "Enviar Mensagem de Email usando Exchange Server com WebDav"
url: /pt/java/enviar-mensagem-de-email-usando-exchange-server-com-webdav/
weight: 100
type: docs
---
  
Você pode enviar mensagens de email usando um Exchange Server com a ajuda das ferramentas em com.aspose.email. O método [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) aceita uma instância de [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) como parâmetro e envia o email. Este artigo explica como enviar mensagens de email usando um Exchange Client da API.  
## **Enviar Mensagens de Email Usando Exchange WebDav**  
Para enviar emails usando um Exchange Server:  
  
1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).  
1. Especifique o nome do servidor, nome de usuário, senha e domínio.  
1. Crie uma instância da classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).  
1. Especifique as propriedades de [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) de remetente, destinatário, assunto e outras.  
1. Chame o método [ExchangeClient.send()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#send\(com.aspose.email.MailMessage\)) para enviar o email.  
  
O código de exemplo abaixo envia mensagens de email usando Exchange Server.  
  
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SendEmailMessageUsingExchangeServer-SendEmailMessageUsingExchangeServer.java" >}}