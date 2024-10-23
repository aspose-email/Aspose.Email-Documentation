---
title: "Buscar Mensagens da Caixa de Correio do Servidor Exchange usando WebDav"
url: /pt/java/fetch-messages-from-exchange-server-mailbox-using-webdav/
weight: 30
type: docs
---

{{% alert color="primary" %}} 

Listar Mensagens em um Servidor Exchange usou o [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método para obter uma lista de mensagens de uma caixa de correio do Servidor Exchange. O [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método obtém informações básicas sobre mensagens, por exemplo, o assunto, o ID da mensagem, de e para.

Para obter os detalhes completos da mensagem, Aspose.Email.Exchange fornece o [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) método. Este método aceita a URI da mensagem como parâmetro e retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage). A classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/mailmessage) então fornece detalhes da mensagem como o corpo, cabeçalhos e anexos.

{{% /alert %}} 
## **Buscar Mensagens de uma Caixa de Correio do Servidor Exchange**
Para buscar mensagens da Caixa de Correio do Servidor Exchange:

1. Crie uma instância do tipo [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Especifique o nome do servidor, nome de usuário, senha e domínio.
1. Chame o [listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método para obter a [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection).
1. Percorra a coleção [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/exchangemessageinfocollection) para obter os valores de [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)).
1. Chame [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) e passe [ExchangeMessageInfo.getUniqueUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo#getUniqueUri\(\)) como parâmetro.

O seguinte trecho de código conecta-se à caixa de correio do Servidor Exchange e busca todas as mensagens.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-FetchMessagesFromAnExchangeServerMailbox-FetchMessagesFromAnExchangeServerMailbox.java" >}}