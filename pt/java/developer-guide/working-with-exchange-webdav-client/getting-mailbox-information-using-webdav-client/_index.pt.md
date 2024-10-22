---
title: "Obtendo Informações da Caixa de Correio usando o Cliente WebDav"
url: /pt/java/getting-mailbox-information-using-webdav-client/
weight: 50
type: docs
---

{{% alert color="primary" %}}  

A classe [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) possui membros que podem ser usados para obter informações da caixa de correio de um Servidor Exchange chamando o método [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)). Ele retorna uma instância do tipo [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo). Obtenha informações da caixa de correio a partir de propriedades como [MailboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getMailboxUri\(\)), [InboxUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getInboxUri\(\)) e [DraftsUri](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo#getDraftsUri\(\)).  

Este artigo mostra como acessar informações da caixa de correio diretamente de um Servidor Exchange.  

{{% /alert %}}  
## **Obter Informações da Caixa de Correio de um Servidor Exchange**  
Para obter as informações da Caixa de Correio do Exchange:  

1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).  
1. Especifique o Servidor Exchange, nome de usuário, senha e domínio no construtor do ExchangeClient.  
1. Chame o método [ExchangeClient.getMailboxSize()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxSize\(\)) para obter o tamanho da caixa de correio.  
1. Chame o método [ExchangeClient.getMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#getMailboxInfo\(\)) para obter uma instância da classe [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo).  
1. Obtenha as informações da caixa de correio usando as diferentes propriedades da classe [ExchangeMailboxInfo](https://apireference.aspose.com/email/java/com.aspose.email/exchangemailboxinfo).  

Os códigos de exemplo abaixo obtêm informações da caixa de correio do Exchange.  

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-GetMailboxInformationFromExchangeServer-GetMailboxInformationFromAnExchangeServer.java" >}}  