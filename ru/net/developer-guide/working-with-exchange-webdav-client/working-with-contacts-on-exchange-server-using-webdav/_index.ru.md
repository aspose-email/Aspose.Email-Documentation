---
title: "Работа с контактами на сервере Exchange с помощью WebDAV"
url: /ru/net/working-with-contacts-on-exchange-server-using-webdav/
weight: 50
type: docs
---


{{% alert color="primary" %}}

Учетные записи Exchange Server содержат больше, чем просто сообщения электронной почты. А также [fetching](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#fetch-messages-from-an-exchange-server-mailbox), [moving](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#moving-messages), [sending](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#sending-email-messages) and [удаление сообщений электронной почты](/email/net/working-with-exchange-mailbox-and-messages-using-webdav/#deleting-messages) с серверов Exchange Aspose.Email позволяет работать с контактами. В этой статье объясняется, как получить контактную информацию непосредственно с сервера Exchange. В этой статье также показано, как вывести список контактов из папки «Контакты».

{{% /alert %}}
## **Получение контактов с сервера Exchange**
The [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) class’ [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) метод можно использовать для получения контактной информации с сервера Exchange. [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) метод требует URI папки Contacts, который можно легко получить с помощью [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri) property.

Чтобы получить контакты с сервера Exchange, выполните следующие действия:

1. Инициализируйте [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) класс с адресом и учетными данными.
1. Получите URI папки «Контакты» с помощью [ExchangeClient.MailboxInfo.ContactsUri](https://apireference.aspose.com/email/net/aspose.email.clients.exchange/exchangemailboxinfo/properties/contactsuri) property.
1. Позвоните [ListContacts()](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/methods/listcontacts) метод. Он возвращает массив [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact).
1. Проделайте петлю foreach на [MapiContact](https://apireference.aspose.com/email/net/aspose.email.mapi/mapicontact) массив для чтения контактной информации.

В следующем фрагменте кода показано, как использовать [ExchangeClient](https://apireference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient) класс для чтения всех контактов с сервера Exchange.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_WebDav-GettingContactsFromAnExchangeServer-GettingContactsFromAnExchangeServer.cs" >}}
