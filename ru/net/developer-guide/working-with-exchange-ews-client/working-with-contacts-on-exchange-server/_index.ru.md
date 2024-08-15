---
title: "Работа с контактами на сервере Exchange"
url: /ru/net/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} Учетные записи Exchange Server содержат больше, чем просто сообщения электронной почты. А также [fetching](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [moving](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#moving-messages), [sending](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#sending-email-messages) and [удаление сообщений электронной почты](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#deleting-messages) с серверов Exchange Aspose.Email позволяет работать с контактами. В этой статье объясняется, как получить контактную информацию с помощью веб-служб Exchange. В этой статье также показано, как выводить список контактов из папки «Контакты» или разрешать контакты на основе имени контакта. {{% /alert %}}

## **Получение контактов с EWS**

Aspose.Email предоставляет [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс для подключения к серверу Microsoft Exchange с помощью веб-служб Exchange. Следующие фрагменты кода используют веб-службы Exchange для чтения всех контактов. В следующем фрагменте кода показано, как получить контакты с EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cs" >}}

## **Разрешайте контакты, используя имя контакта**

В следующем фрагменте кода показано, как использовать функцию get contacts в EWS

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cs" >}}

## **Определение формата контактных заметок**

Формат Aspose.Email.Mail.Contact.NotesFormat указывает тип текстового формата примечаний к контактам, определенный перечислителем aSpose.Email.TextFormat.

## **Извлечь контакт с помощью идентификатора**

Конкретный контакт можно получить с сервера, используя его идентификатор контакта, как показано в следующем примере кода.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cs" >}}

## **Добавление контактов**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) class [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) метод можно использовать для добавления контактной информации на сервер Exchange. [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) метод принимает объект Contact в качестве входного параметра.

Чтобы добавить контакты на сервер Exchange, выполните следующие действия:

1. Инициализируйте EWSClient, указав адрес и учетные данные.
1. Инициализируйте объект Contact с нужными свойствами.
1. Вызовите метод createContact, чтобы добавить контакт на сервер Exchange.

Aspose.Email предоставляет [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) класс для подключения к серверу Microsoft Exchange с помощью веб-служб Exchange. В фрагментах кода показано, как использовать веб-службы Exchange для добавления контактов на сервер Exchange.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddContactsToExchangeServerUsingEWS-AddContactsToExchangeServerUsingEWS.cs" >}}

## **Обновление контактов**

Контактную информацию можно обновить с помощью Microsoft Outlook. Aspose.Email также может обновлять контактную информацию на сервере Exchange с помощью веб-службы Exchange (EWS). Клиент IEWS [UpdateContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatecontact/) метод может обновлять контактную информацию на сервере Exchange.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cs" >}}

## **Удаление контактов**

The [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс позволяет DeleteContact получать доступ к контактам в папке контактов Exchange Server и удалять их из нее. В этом методе в качестве входного параметра используется идентификатор контакта или MapiContact.

Чтобы удалить контакты с сервера Exchange, выполните следующие действия:

1. Инициализируйте клиент ExchangeWebServiceClient, указав адрес и учетные данные.
1. Удалите контакт, используя его идентификатор.
1. Удалите контакт, позвонив в [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletecontact/) метод с [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/mapicontact/) в качестве входного параметра.

В следующих фрагментах кода показано, как удалять контакты с сервера Exchange с помощью веб-службы Exchange.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cs" >}}

## **Работа с расширенными свойствами контактов на сервере Exchange**

``` cs

 IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

//The required extended properties must be added in order to create or read them from the Exchange Server

string[] extraFields = new string[] {{ "User Field 1", "User Field 2", "User Field 3", "User Field 4" }};

foreach (string extraField in extraFields)

    client.ContactExtendedPropertiesDefinition.Add(extraField);

//Create a test contact on the Exchange Server

Contact contact = new Contact();

contact.DisplayName = "EMAILNET-38433 - " + Guid.NewGuid().ToString();

foreach (string extraField in extraFields)

    contact.ExtendedProperties.Add(extraField, extraField);

string contactId = client.CreateContact(contact);

//retrieve the contact back from the server after some time

Thread.Sleep(5000);

contact = client.GetContact(contactId);

//Parse the extended properties of contact

foreach (string extraField in extraFields)

    if (contact.ExtendedProperties.ContainsKey(extraField))

        Console.WriteLine(contact.ExtendedProperties[extraField].ToString());

```
