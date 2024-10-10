---
title: "Работа с контактами на Exchange Server"
url: /ru/net/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} Учетные записи Exchange Server содержат не только электронные сообщения. Кроме [получения](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [перемещения](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#moving-messages), [отправки](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#sending-email-messages) и [удаления электронных сообщений](https://docs.aspose.com/email/ru/net/working-with-exchange-mailbox-and-messages/#deleting-messages) с Exchange Server, Aspose.Email позволяет работать с контактами. Эта статья объясняет, как извлечь информацию о контактах с использованием Exchange Web Services. В этой статье также показано, как вы можете перечислить контакты из папки Контакты или разрешить контакты на основе имени контакта. {{% /alert %}} 

## **Получение контактов с EWS**

Aspose.Email предоставляет класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) для подключения к Microsoft Exchange Server с использованием Exchange Web Services. Приведенные далее примеры кода используют Exchange Web Services для чтения всех контактов. Следующий фрагмент кода показывает, как получить контакты с EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cs" >}}

## **Разрешение контактов по имени контакта**

Следующий фрагмент кода показывает, как получать контакты с EWS.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cs" >}}

## **Определение формата заметок контакта**

Aspose.Email.Mail.Contact.NotesFormat задает тип текстового формата заметок контактов, определенный перечислением Aspose.Email.TextFormat.

## **Получение контакта по идентификатору**

Определенный контакт может быть извлечен с сервера с использованием его идентификатора контакта, как показано в следующем примере кода.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cs" >}}

## **Добавление контактов**

Метод класса [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) может быть использован для добавления информации о контакте на Exchange Server. Метод [CreateContact()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createcontact/) принимает объект Contact в качестве входного параметра.

Чтобы добавить контакты на Exchange Server:

1. Инициализируйте EWSClient с адресом и учетными данными.
1. Инициализируйте объект Contact с необходимыми свойствами.
1. Вызовите метод CreateContact для добавления контакта на Exchange Server.

Aspose.Email предоставляет класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/#ewsclient-class) для подключения к Microsoft Exchange Server с использованием Exchange Web Services. Примеры кода показывают, как использовать Exchange Web Services для добавления контактов на Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-AddContactsToExchangeServerUsingEWS-AddContactsToExchangeServerUsingEWS.cs" >}}

## **Обновление контактов**

Информация о контактах может быть обновлена с помощью Microsoft Outlook. Aspose.Email также может обновить информацию о контактах на Exchange Server с использованием Exchange Web Service (EWS). Метод IEWSClient [UpdateContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updatecontact/) может обновить информацию о контактах на Exchange Server.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cs" >}}

## **Удаление контактов**

Класс [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) позволяет использовать DeleteContact для доступа и удаления контактов из папки контактов Exchange Server. Этот метод принимает идентификатор контакта или MapiContact в качестве входного параметра.

Чтобы удалить контакты с Exchange Server:

1. Инициализируйте ExchangeWebServiceClient с адресом и учетными данными.
1. Удалите контакт, используя его идентификатор.
1. Удалите контакт, вызвав метод [DeleteContact](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/deletecontact/) с [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/mapicontact/) в качестве входного параметра.

Следующие примеры кода показывают, как удалить контакты с сервера Exchange с использованием Exchange Web Service.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cs" >}}

## **Работа с дополнительными свойствами контактов на Exchange Server**

``` cs

 IEWSClient client = EWSClient.GetEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

//Необходимые дополнительные свойства должны быть добавлены для их создания или чтения с сервера Exchange

string[] extraFields = new string[] {{ "Пользовательское поле 1", "Пользовательское поле 2", "Пользовательское поле 3", "Пользовательское поле 4" }};

foreach (string extraField in extraFields)

    client.ContactExtendedPropertiesDefinition.Add(extraField);

//Создайте тестовый контакт на сервере Exchange

Contact contact = new Contact();

contact.DisplayName = "EMAILNET-38433 - " + Guid.NewGuid().ToString();

foreach (string extraField in extraFields)

    contact.ExtendedProperties.Add(extraField, extraField);

string contactId = client.CreateContact(contact);

//извлеките контакт с сервера через некоторое время

Thread.Sleep(5000);

contact = client.GetContact(contactId);

//Парсинг дополнительных свойств контакта

foreach (string extraField in extraFields)

    if (contact.ExtendedProperties.ContainsKey(extraField))

        Console.WriteLine(contact.ExtendedProperties[extraField].ToString());

```