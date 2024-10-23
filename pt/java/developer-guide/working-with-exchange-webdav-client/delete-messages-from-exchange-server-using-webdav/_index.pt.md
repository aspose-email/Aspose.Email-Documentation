---
title: "Excluir Mensagens do Servidor Exchange usando WebDav"
url: /pt/java/delete-messages-from-exchange-server-using-webdav/
weight: 20
type: docs
---

Você pode excluir mensagens de email de uma pasta com a ajuda do método [ExchangeClient.deleteMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#deleteMessage\(java.lang.String\)). Ele recebe o URI exclusivo da mensagem como parâmetro.

O código de exemplo abaixo exclui uma mensagem da pasta Caixa de Entrada. Para o propósito deste exemplo, o código:

1. Lê mensagens da pasta Caixa de Entrada.
1. Processa mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
1. Exclui a mensagem.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-DeleteMessagesFromExchangeServer-DeleteMessagesFromExchangeServer.java" >}}