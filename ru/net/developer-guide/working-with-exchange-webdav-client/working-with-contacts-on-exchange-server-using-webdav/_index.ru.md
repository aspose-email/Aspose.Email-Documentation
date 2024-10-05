---
title: "Работа с контактами на Exchange Server с использованием WebDav"
url: /ru/net/работа-с-контактами-на-exchange-server-с-использованием-webdav/
weight: 50
type: docs
---

{{% alert color="primary" %}} 

Учетные записи Exchange Server содержат не только электронные сообщения. Вместе с [получением](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#fetch-messages-from-an-exchange-server-mailbox), [перемещением](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#moving-messages), [отправкой](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#sending-email-messages) и [удалением электронных сообщений](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#deleting-messages) с Exchange Servers, Aspose.Email позволяет работать с контактами. Эта статья объясняет, как получить информацию о контактах напрямую с Exchange Server. В этой статье также показано, как перечислить контакты из папки Контакты.

{{% /alert %}} 
## **Получение контактов с Exchange Server**
Метод [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) класса [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) может быть использован для получения информации о контактах с Exchange Server. Метод [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) требует URI папки Контакты, который можно легко получить с помощью свойства [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri).

Чтобы получить контакты с Exchange Server:

1. Инициализируйте класс [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) с адресом и учетными данными.
1. Получите URI папки Контакты с помощью свойства [ExchangeClient.MailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri).
1. Вызовите метод [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts). Он возвращает массив [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact).
1. Используйте цикл foreach для массива [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact), чтобы прочитать информацию о контактах.

Следующий фрагмент кода показывает, как использовать класс [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) для чтения всех контактов с Exchange Server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GettingContactsFromAnExchangeServer-GettingContactsFromAnExchangeServer.cs" >}}