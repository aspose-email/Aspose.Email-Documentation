---
title: "Работа с контактами на Exchange Server"
url: /ru/java/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---


{{% alert color="primary" %}} Аккаунты Exchange Server содержат не только электронные сообщения. Кроме [получения](/email/java/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [перемещения](/email/java/working-with-exchange-mailbox-and-messages/#moving-messages), [отправки](/email/java/working-with-exchange-mailbox-and-messages/#sending-email-messages) и [удаления электронных сообщений](/email/java/working-with-exchange-mailbox-and-messages/#deleting-messages) с Exchange Server, Aspose.Email позволяет работать с контактами. Эта статья объясняет, как получить информацию о контактах с использованием Exchange Web Services. Также в статье показано, как можно перечислить контакты из папки Контакты или разрешить контакты на основе имени контакта. {{% /alert %}} 
## **Получение контактов с EWS**
Aspose.Email предоставляет класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) для подключения к Microsoft Exchange Server с использованием Exchange Web Services. Приведенные ниже фрагменты кода используют Exchange Web Services для чтения всех контактов. Следующий фрагмент кода показывает, как получить контакты с EWS.



~~~Java
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Список всех контактов
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
for (Contact contact : contacts) {
    MapiContact mapiContact = Contact.to_MapiContact(contact);
    // Отобразить имя и адрес электронной почты
    System.out.println("Name: " + mapiContact.getNameInfo().getDisplayName() + "+ Email Address: " + mapiContact.getElectronicAddresses().getEmail1());
}
~~~
## **Разрешение контактов по имени контакта**
Следующий фрагмент кода показывает, как получить контакты с EWS



~~~Java
// Создать экземпляр класса IEWSClient, указав учетные данные
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");

// Список всех контактов
Contact[] contacts = client.resolveContacts("Changed Name", ExchangeListContactsOptions.FetchPhoto);
for (Contact c : contacts) {
    MapiContact contact = Contact.to_MapiContact(c);
    // Отобразить имя и адрес электронной почты
    System.out.println("Name: " + contact.getNameInfo().getDisplayName() + "+ Email Address: " + contact.getElectronicAddresses().getEmail1());
}
~~~
## **Определение формата заметок контактов**
NotesFormat указывает тип формата текста заметок контактов, определяемый перечислением TextFormat.

## **Получение контакта по Id**
Определенный контакт можно получить с сервера, используя его идентификатор контакта, как показано в следующем примере кода.



~~~Java
Contact fetchedContact = client.getContact(id);
~~~
## **Добавление контактов**
Класс [EWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) метод [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) может быть использован для добавления информации о контакте на Exchange Server. Метод [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) принимает объект [Contact](https://apireference.aspose.com/email/java/com.aspose.email/Contact) в качестве входного параметра.

Чтобы добавить контакты на Exchange Server:

1. Инициализируйте EWSClient с адресом и учетными данными.
1. Инициализируйте объект Contact с необходимыми свойствами.
1. Вызовите метод CreateContact, чтобы добавить контакт на Exchange Server.

Aspose.Email предоставляет класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) для подключения к Microsoft Exchange Server с использованием Exchange Web Services. Приведенные ниже фрагменты кода показывают, как использовать Exchange Web Services для добавления контактов на Exchange Server.



~~~Java
// Установить mailboxURI, Имя пользователя, пароль, информацию о домене
String mailboxUri = "https://ex2010/ews/exchange.asmx";
String username = "test.exchange";
String password = "pwd";
String domain = "ex2010.local";
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Создать новый контакт
Contact contact = new Contact();

// Установить общую информацию
contact.setGender(Gender.Male);
contact.setDisplayName("Frank Lin");
contact.setCompanyName("ABC Co.");
contact.setJobTitle("Executive Manager");
PhoneNumber tmp0 = new PhoneNumber();
tmp0.setNumber("123456789");
tmp0.setCategory(PhoneNumberCategory.getHome());

// Добавить номера телефонов
contact.getPhoneNumbers().add(tmp0);
AssociatedPerson tmp1 = new AssociatedPerson();
tmp1.setName("Catherine");
tmp1.setCategory(AssociatedPersonCategory.getSpouse());

// Сопутствующие лица контакта
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

// URL
contact.getUrls().add(tmp4);
Url tmp5 = new Url();
tmp5.setHref("www.homepage.com");
tmp5.setCategory(UrlCategory.getHomePage());
contact.getUrls().add(tmp5);
EmailAddress tmp6 = new EmailAddress();
tmp6.setAddress("Frank.Lin@Abc.com");
tmp6.setDisplayName("Frank Lin");
tmp6.setCategory(EmailAddressCategory.getEmail1());

// Установить адрес электронной почты контакта
contact.getEmailAddresses().add(tmp6);

try {
    client.createContact(contact);
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
## **Обновление контактов**
Информацию о контактах можно обновить с помощью Microsoft Outlook. Aspose.Email также может обновлять информацию о контактах на Exchange Server с использованием Exchange Web Service (EWS). Метод [updateContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateContact\(com.aspose.email.Contact\)) класса [IEWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) может обновить информацию о контактах на Exchange Server.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// Список всех контактов и перебор всех контактов
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
Contact contact = contacts[0];
System.out.println("Name: " + contact.getDisplayName());
contact.setDisplayName("David Ch");
client.updateContact(contact);
~~~
## **Удаление контактов**
Класс [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) предоставляет метод [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) для доступа и удаления контактов из папки контактов Exchange Server. Этот метод принимает идентификатор контакта в качестве входного параметра.

Чтобы удалить контакты с Exchange Server:

1. Инициализируйте ExchangeWebServiceClient с адресом и учетными данными.
1. Удалите контакт, используя его идентификатор.

Следующий фрагмент кода показывает, как удалять контакты с сервера Exchange, используя Exchange Web Service.



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