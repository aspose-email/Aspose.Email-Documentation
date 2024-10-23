---
title: "Listando Extensões do Servidor IMAP"
url: /pt/python-net/listing-imap-server-extensions/
weight: 40
type: docs
---


## **Listando Extensões do Servidor**
O ImapClient da Aspose.Email permite que você recupere as extensões do servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método GetCapabilities() retorna os tipos de extensão suportados na forma de um array de strings. O seguinte trecho de código mostra como recuperar extensões.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetrievingServerExtensions-RetrievingServerExtensions.py" >}}