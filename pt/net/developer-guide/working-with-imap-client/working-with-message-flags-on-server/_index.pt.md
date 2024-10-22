---
title: "Trabalhando com Flags de Mensagem no Servidor"
url: /pt/net/trabalhando-com-flags-de-mensagem-no-servidor/
weight: 30
type: docs
---


## **Alterando as Flags de Mensagem**

Você pode alterar as flags de mensagem usando o método [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/). Este método aceita dois parâmetros.

1. O número de sequência de uma mensagem ou seu ID único.
2. [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/).

As seguintes flags podem ser configuradas:

- [Answered](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/answered/)
- [Deleted](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/deleted/)
- [Draft](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/draft/)
- [Empty](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/empty/)
- [Flagged](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/flagged/)
- [IsRead](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/isread/)
- [Recent](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/recent/)

### **Definindo Flags de Mensagem**

O seguinte trecho de código mostra como mudar as flags de mensagem em um servidor IMAP com Aspose.Email.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SettingMessageFlags-SettingMessageFlags.cs" >}}

### **Removendo Flags de Mensagem**

As flags de mensagem também podem ser removidas com o método [RemoveMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/removemessageflags/#removemessageflags/). O uso é semelhante ao do método [ChangeMessageFlags()](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/changemessageflags/#changemessageflags/). Ele aceita um número de sequência ou ID único da mensagem e [MessageFlag](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapmessageflags/). O seguinte trecho de código mostra como remover as flags de mensagem.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RemovingMessageFlags-RemovingMessageFlags.cs" >}}

## **Definindo Flags Personalizadas**

Você também pode definir flags personalizadas para uma mensagem usando o [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) da API. O ImapClient AddMessageFlags oferece a capacidade de definir flags personalizadas em mensagens.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-SetCustomFlag-SetCustomFlag.cs" >}}