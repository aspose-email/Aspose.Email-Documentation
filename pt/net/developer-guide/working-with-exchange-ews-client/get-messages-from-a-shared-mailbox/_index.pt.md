---
title: "Obter Mensagens de uma Caixa de Correio Compartilhada"
url: /pt/net/get-messages-from-a-shared-mailbox/
weight: 160
type: docs
---


Aspose.Email oferece suporte ao acesso a mensagens da caixa de correio compartilhada. Para conseguir isso, você se conecta à sua caixa de correio principal usando a classe [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Para acessar mensagens da caixa de correio compartilhada, você passa a caixa de correio compartilhada como um parâmetro de string para o método [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) ou [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/).

O seguinte exemplo de código mostra como acessar mensagens da caixa de correio compartilhada usando o método [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/).

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-GetMessagesFromSharedMailbox-1.cs" >}}