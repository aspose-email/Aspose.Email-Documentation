---
title: "Listando Extensões do Servidor IMAP"
url: /pt/net/listing-imap-server-extensions/
weight: 80
type: docs
---

O [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) da Aspose.Email permite que você recupere as extensões do servidor que um servidor suporta, como IDLE, UNSELECT, QUOTA, etc. Isso ajuda a identificar a disponibilidade de uma extensão antes de usar o cliente para essa funcionalidade específica. O método [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) retorna os tipos de extensão suportados na forma de um array de strings. O seguinte trecho de código mostra como recuperar extensões.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetreivingServerExtensions-RetreivingServerExtensions.cs" >}}