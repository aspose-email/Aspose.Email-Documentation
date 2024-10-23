---
title: "Mover Mensagens de uma Pasta para Outra usando WebDav"
url: /pt/java/move-messages-from-one-folder-to-another-using-webdav/
weight: 70
type: docs
---

Você pode mover mensagens de email de uma pasta para outra com a ajuda do [método ExchangeClient.moveMessage()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#moveMessage\(com.aspose.email.ExchangeMessageInfo,%20java.lang.String\)). Ele aceita os parâmetros:

- O URI único da mensagem que deve ser movida.
- O URI único da pasta de destino.
## **Mover Mensagens entre Pastas**
O código de exemplo abaixo move uma mensagem em uma caixa de correio da pasta Caixa de Entrada para uma pasta chamada Processado. Neste exemplo, o aplicativo:

1. Lê mensagens da pasta Caixa de Entrada.
1. Processa algumas das mensagens com base em alguns critérios (neste exemplo, encontramos uma palavra-chave no assunto da mensagem).
1. Move mensagens que atendem à condição dada para a pasta Processado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-exchange-MoveMessageFromOneFolderToAnother-MoveMessagesBetweenFolders.java" >}}