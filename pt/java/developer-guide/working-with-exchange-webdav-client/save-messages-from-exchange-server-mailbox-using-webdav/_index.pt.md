---
title: "Salvar Mensagens da Caixa de Correio do Exchange Server usando WebDav"
url: /pt/java/save-messages-from-exchange-server-mailbox-using-webdav/
weight: 90
type: docs
---

Este artigo mostra como obter mensagens de uma caixa de correio do Exchange Server e salvá-las no disco nos formatos EML e MSG.
## **Salvar Mensagens de uma Caixa de Correio do Exchange Server em EML**
Para obter mensagens e salvar no formato EML:

1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Forneça o nome do servidor, nome de usuário, senha e domínio.
1. Chame o método [ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) para obter uma instância da coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection).
1. Percorra a coleção [ExchangeMessagesInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) para obter o URI exclusivo de cada mensagem.
1. Chame o método [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) e passe o URI exclusivo como um parâmetro.
1. Forneça um método [saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) com um caminho para onde você deseja salvar o arquivo.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesAsEML.java" >}}
## **Salvar Mensagens em um OutputStream**
Em vez de salvar arquivos EML no disco, é possível salvá-los em um OutputStream. Isso é útil quando você deseja salvar o fluxo em algum local de armazenamento, como um banco de dados. Uma vez que o fluxo foi salvo em um banco de dados, você pode recarregar o arquivo EML na classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage).

Os trechos de código abaixo salvam mensagens de uma caixa de correio do Exchange Server em um fluxo de memória.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesToOutputStream.java" >}}
## **Salvar Mensagens no Formato MSG**
O método [ExchangeClient.saveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#saveMessage\(java.lang.String,%20java.io.OutputStream\)) pode salvar diretamente a mensagem no formato EML. Para salvar as mensagens no formato MSG, primeiro, chame o método [ExchangeClient.fetchMessage()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#fetchMessage\(java.lang.String\)) que retorna uma instância da classe [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage). Em seguida, chame o método [MailMessage.save()](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage#save\(java.io.OutputStream\)) para salvar a mensagem em MSG.

O trecho de código abaixo obtém mensagens de uma caixa de correio do Exchange Server e as salva no formato MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-SaveMessagesFromExchangeServerMailbox-SaveMessagesInMSGFormat.java" >}}