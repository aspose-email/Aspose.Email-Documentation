---
title: "Работа с контактами на Exchange Server с использованием WebDav"
url: /ru/java/working-with-contacts-on-exchange-server-using-webdav/
weight: 120
type: docs
---


{{% alert color="primary" %}} 

В этой статье объясняется, как получить информацию о контактах напрямую с Exchange Server. В статье также показано, как можно перечислить контакты из папки "Контакты".

{{% /alert %}} 
## **Получение контактов с Exchange Server**
Метод [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) класса [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) можно использовать для получения информации о контактах с Exchange Server. Метод [listContacts()](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient#listContacts\(java.lang.String\)) требует URI папки "Контакты", который можно легко получить с помощью свойства [ExchangeMailboxInfo.ContactsUri](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMailboxInfo#getContactsUri\(\)).

Чтобы получить контакты с Exchange Server:

1. Инициализируйте класс ExchangeClient с адресом и учетными данными.
1. Получите URI папки "Контакты" с помощью свойства ExchangeClient.getMailboxInfo().getContactsUri().
1. Вызовите метод listContacts(). Он возвращает массив MapiContact.
1. Выполните цикл foreach по массиву MapiContact, чтобы прочитать информацию о контактах.

Следующий фрагмент кода демонстрирует, как использовать класс [ExchangeClient](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeClient) для чтения всех контактов с Exchange Server.


~~~Java
String mailboxURI = "http://ex2003/exchange/administrator"; // WebDAV
String username = "administrator";
String password = "pwd";
String domain = "domain.local";

// Учетные данные для подключения к Exchange Server
NetworkCredential credential = new NetworkCredential(username, password, domain);
ExchangeClient client = new ExchangeClient(mailboxURI, credential);

// Перечислить все контакты
MapiContact[] contacts = client.listContacts(client.getMailboxInfo().getContactsUri());
for (MapiContact contact : contacts)
{
    // Имя и адрес электронной почты
    System.out.println("Name: " + contact.getNameInfo().getDisplayName() + ", Email Address: " + contact.getElectronicAddresses().getEmail1());
}
~~~