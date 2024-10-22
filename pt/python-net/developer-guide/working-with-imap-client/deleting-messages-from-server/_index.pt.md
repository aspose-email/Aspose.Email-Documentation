---
title: "Deletando Mensagens do Servidor"
url: /pt/python-net/deleting-messages-from-server/
weight: 20
type: docs
---


## **Deletando Mensagens**
A classe ImapClient pode deletar mensagens de um servidor IMAP. A função DeleteMessage() da classe ImapClient é utilizada para deletar mensagens. Ela aceita o número de sequência da mensagem ou o ID único como parâmetro. O ImapClient fornece os métodos DeleteMessage e DeleteMessages para deletar mensagens uma a uma ou múltiplas. O seguinte trecho de código mostra como deletar uma mensagem de email com o ID da mensagem 1 de um servidor IMAP.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteSingleMessage-DeleteSingleMessage.py" >}}
## **Deletando Múltiplas Mensagens**
Múltiplos emails podem ser deletados da caixa de entrada usando o ImapClient da API Aspose.Email. O método DeleteMessages oferece uma série de opções para deletar múltiplas mensagens do servidor usando IDs únicos, números de sequência ou elementos ImapMessageInfoCollection. O seguinte trecho de código mostra como deletar múltiplas mensagens.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteMultipleMessages-DeleteMultipleMessages.py" >}}