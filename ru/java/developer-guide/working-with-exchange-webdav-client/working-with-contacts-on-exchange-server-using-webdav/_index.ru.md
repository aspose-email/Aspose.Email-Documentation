---
title: "Работа с контактами на сервере Exchange с помощью WebDAV"
url: /ru/java/working-with-contacts-on-exchange-server-using-webdav/
weight: 120
type: docs
---


{{% alert color="primary" %}}

В этой статье описывается, как получить контактную информацию непосредственно с сервера Exchange. В этой статье также показано, как вывести список контактов из папки «Контакты».

{{% /alert %}}
## **Получение контактов с сервера Exchange**
The [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) class’ [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) метод можно использовать для получения контактной информации с сервера Exchange. [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) метод требует URI папки Contacts, который можно легко получить с помощью [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getContactsUri\(\)) property.

Чтобы получить контакты с сервера Exchange, выполните следующие действия:

1. Инициализируйте класс ExchangeClient с адресом и учетными данными.
1. Получите URI папки «Контакты» с помощью свойства ExchangeClient.getMailboxInfo () .getContactSuri ().
1. Вызовите метод listContacts (). Он возвращает массив mapiContact.
1. Выполните цикл foreach в массиве MapiContact, чтобы прочитать контактную информацию.

В следующем фрагменте кода показано, как использовать [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) класс для чтения всех контактов с сервера Exchange.


~~~Java
String mailboxURI = "http://ex2003/exchange/administrator"; // WebDAV
String username = "administrator";
String password = "pwd";
String domain = "domain.local";

// Credentials for connecting to Exchange Server
NetworkCredential credential = new NetworkCredential(username, password, domain);
ExchangeClient client = new ExchangeClient(mailboxURI, credential);

// List all the contacts
MapiContact[] contacts = client.listContacts(client.getMailboxInfo().getContactsUri());
for (MapiContact contact : contacts)
{
    // Display name and email address
    System.out.println("Name: " + contact.getNameInfo().getDisplayName() + ", Email Address: " + contact.getElectronicAddresses().getEmail1());
}
~~~
