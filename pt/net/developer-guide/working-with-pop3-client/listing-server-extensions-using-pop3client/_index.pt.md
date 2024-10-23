---
title: "Listando Extensões do Servidor Usando Pop3Client"
url: /pt/net/listing-server-extensions-using-pop3client/
weight: 30
type: docs
---


Aspose.Email [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) permite que você recupere as extensões do servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) retorna os tipos de extensão suportados na forma de um array de strings.

## **Recuperando Extensões do Servidor**

O seguinte exemplo de código demonstra como recuperar extensões do servidor usando ImapClient para o servidor Gmail.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetServerExtensionsUsingPop3Client-GetServerExtensionsUsingPop3Client.cs" >}}