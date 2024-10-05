---
title: Получение сообщений из общей почтового ящика
type: docs
weight: 160
url: /net/get-messages-from-a-shared-mailbox/
---


Aspose.Email поддерживает доступ к сообщениям из общей почтового ящика. Для этого вы подключаетесь к вашему основному почтовому ящику, используя класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Чтобы получить доступ к сообщениям из общей почтового ящика, вы передаете общий почтовый ящик в качестве строкового параметра методу [ListMessages](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listmessages/) или [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/).

Следующий пример кода показывает, как получить доступ к сообщениям из общей почтового ящика, используя метод [ListItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/listitems/).

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Exchange_EWS-GetMessagesFromSharedMailbox-1.cs" >}}