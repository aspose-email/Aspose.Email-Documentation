---
title: "Работа с контактами на сервере Exchange"
url: /ru/java/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} Учетные записи Exchange Server содержат больше, чем просто сообщения электронной почты. А также [fetching](/email/java/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [moving](/email/java/working-with-exchange-mailbox-and-messages/#moving-messages), [sending](/email/java/working-with-exchange-mailbox-and-messages/#sending-email-messages) and [удаление сообщений электронной почты](/email/java/working-with-exchange-mailbox-and-messages/#deleting-messages) с серверов Exchange Aspose.Email позволяет работать с контактами. В этой статье объясняется, как получить контактную информацию с помощью веб-служб Exchange. В этой статье также показано, как выводить список контактов из папки «Контакты» или разрешать контакты на основе имени контакта. {{% /alert %}}
## **Получение контактов с EWS**
Aspose.Email предоставляет [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс для подключения к серверу Microsoft Exchange с помощью веб-служб Exchange. Следующие фрагменты кода используют веб-службы Exchange для чтения всех контактов. В следующем фрагменте кода показано, как получить контакты с EWS.



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// List all the contacts
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    MapiContact mapiContact = Contact.to_MapiContact(contact);
    // Display name and email address
    System.out.println("Name: " + mapiContact.getNameInfo().getDisplayName() + "+ Email Address: " + mapiContact.getElectronicAddresses().getEmail1());
}
~~~
## **Разрешайте контакты, используя имя контакта**
В следующем фрагменте кода показано, как использовать функцию get contacts в EWS



~~~Java
// Create instance of IEWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// List all the contacts
Contact[] contacts = client.resolveContacts("Changed Name", ExchangeListContactsOptions.FetchPhoto);
for (Contact c : contacts) {
    MapiContact contact = Contact.to_MapiContact(c);
    // Display name and email address
    System.out.println("Name: " + contact.getNameInfo().getDisplayName() + "+ Email Address: " + contact.getElectronicAddresses().getEmail1());
}
~~~
## **Определение формата контактных заметок**
NotesFormat указывает тип текстового формата заметок контактов, определенный перечислителем TextFormat.

## **Извлечь контакт с помощью идентификатора**
Конкретный контакт можно получить с сервера, используя его идентификатор контакта, как показано в следующем примере кода.



~~~Java
Contact fetchedContact = client.getContact(id);
~~~
## **Добавление контактов**
The [EWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) class [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) метод можно использовать для добавления контактной информации на сервер Exchange. [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) метод принимает [Contact](https://apireference.aspose.com/email/java/com.aspose.email/Contact) объект в качестве входного параметра.

Чтобы добавить контакты на сервер Exchange, выполните следующие действия:

1. Инициализируйте EWSClient, указав адрес и учетные данные.
1. Инициализируйте объект Contact с нужными свойствами.
1. Вызовите метод createContact, чтобы добавить контакт на сервер Exchange.

Aspose.Email предоставляет [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс для подключения к серверу Microsoft Exchange с помощью веб-служб Exchange. Во фрагментах кода показано, как использовать веб-службы Exchange для добавления контактов на сервер Exchange.



~~~Java
// Set mailboxURI, Username, password, domain information
String mailboxUri = "https://ex2010/ews/exchange.asmx";
String username = "test.exchange";
String password = "pwd";
String domain = "ex2010.local";
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Create New Contact
Contact contact = new Contact();

// Set general info
contact.setGender(Gender.Male);
contact.setDisplayName("Frank Lin");
contact.setCompanyName("ABC Co.");
contact.setJobTitle("Executive Manager");
PhoneNumber tmp0 = new PhoneNumber();
tmp0.setNumber("123456789");
tmp0.setCategory(PhoneNumberCategory.getHome());

// Add Phone numbers
contact.getPhoneNumbers().add(tmp0);
AssociatedPerson tmp1 = new AssociatedPerson();
tmp1.setName("Catherine");
tmp1.setCategory(AssociatedPersonCategory.getSpouse());

// contact's associated persons
contact.getAssociatedPersons().add(tmp1);
AssociatedPerson tmp2 = new AssociatedPerson();
tmp2.setName("Bob");
tmp2.setCategory(AssociatedPersonCategory.getChild());
contact.getAssociatedPersons().add(tmp2);
AssociatedPerson tmp3 = new AssociatedPerson();
tmp3.setName("Merry");
tmp3.setCategory(AssociatedPersonCategory.getSister());
contact.getAssociatedPersons().add(tmp3);
Url tmp4 = new Url();
tmp4.setHref("www.blog.com");
tmp4.setCategory(UrlCategory.getBlog());

// URLs
contact.getUrls().add(tmp4);
Url tmp5 = new Url();
tmp5.setHref("www.homepage.com");
tmp5.setCategory(UrlCategory.getHomePage());
contact.getUrls().add(tmp5);
EmailAddress tmp6 = new EmailAddress();
tmp6.setAddress("Frank.Lin@Abc.com");
tmp6.setDisplayName("Frank Lin");
tmp6.setCategory(EmailAddressCategory.getEmail1());

// Set contact's Email address
contact.getEmailAddresses().add(tmp6);

try {
    client.createContact(contact);
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Обновление контактов**
Контактную информацию можно обновить с помощью Microsoft Outlook. Aspose.Email также может обновлять контактную информацию на сервере Exchange с помощью веб-службы Exchange (EWS). [IEWSClient's](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) [updateContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateContact\(com.aspose.email.Contact\)) метод может обновлять контактную информацию на сервере Exchange.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// List all the contacts and Loop through all contacts
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
Contact contact = contacts[0];
System.out.println("Name: " + contact.getDisplayName());
contact.setDisplayName("David Ch");
client.updateContact(contact);
~~~
## **Удаление контактов**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) класс предоставляет [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) для доступа к контактам и их удаления из папки контактов сервера Exchange. Этот метод принимает идентификатор контакта в качестве входного параметра.

Чтобы удалить контакты с сервера Exchange, выполните следующие действия:

1. Инициализируйте клиент ExchangeWebServiceClient, указав адрес и учетные данные.
1. Удалите контакт, используя его идентификатор.

В следующих фрагментах кода показано, как удалить контакты с сервера Exchange с помощью веб-службы Exchange.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

String strContactToDelete = "John Teddy";
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    if (contact.getDisplayName().equals(strContactToDelete))
        client.deleteItem(contact.getId().getEWSId(), DeletionOptions.getDeletePermanently());

}
client.dispose();
~~~