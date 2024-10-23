---
title: "Listando Mensagens do Exchange Server usando WebDav"
url: /pt/java/listing-messages-from-exchange-server-using-webdav/
weight: 60
type: docs
---

Uma lista das mensagens de e-mail em uma caixa de correio do Exchange pode ser obtida chamando o [método ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)). Obtenha as informações básicas sobre as mensagens, como assunto, de, para e ID da mensagem, usando o [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) método.

Este artigo mostra como se conectar a um Exchange Server e listar os e-mails em uma caixa de correio diretamente ou usando WebDav. Ele também mostra como listar mensagens de diferentes pastas e como listar mensagens por ID.
## **Listar Mensagens do Exchange Server**
Para listar as mensagens em uma caixa de correio do Exchange:

1. Crie uma instância da classe [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient).
1. Chame o [método listMessages](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) e crie uma coleção de mensagens.
1. Percorra a coleção e exiba as informações das mensagens.

O trecho de código abaixo se conecta à caixa de correio do Exchange e obtém a lista de mensagens da pasta Caixa de Entrada.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromInboxFolderOnExchangeServer.java" >}}
## **Listando Mensagens de Diferentes Pastas**
Os códigos acima listam todas as mensagens na pasta Caixa de Entrada. Também é possível obter a lista de mensagens de outras pastas. O [método ExchangeClient.listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient#listMessages\(java.lang.String\)) aceita um URI de pasta como parâmetro. Desde que o URI da pasta seja válido, você pode obter a lista de mensagens daquela pasta.

Use a propriedade ExchangeClient.getMailboxInfo().xxxFolderUri[](https://apireference.aspose.com/email/java/com.aspose.email/exchangeclient) para obter o URI de diferentes pastas. O restante do código é o mesmo para obter uma lista de mensagens.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-ListMessages-ListMessagesFromOtherFoldersOnExchangeServer.java" >}}