---
title: Working with Contacts on Exchange Server
type: docs
weight: 60
url: /java/working-with-contacts-on-exchange-server/
---


{{% alert color="primary" %}} Exchange Server accounts hold more than just email messages. As well as [fetching](/email/java/working-with-exchange-mailbox-and-messages/#fetch-messages-from-an-exchange-server-mailbox), [moving](/email/java/working-with-exchange-mailbox-and-messages/#moving-messages), [sending](/email/java/working-with-exchange-mailbox-and-messages/#sending-email-messages) and [deleting email messages](/email/java/working-with-exchange-mailbox-and-messages/#deleting-messages) from Exchange Servers, Aspose.Email allows you to work with contacts. This article explains how to retrieve contact information using Exchange Web Services. This article also shows how you can list contacts from the Contacts folder or resolve contacts based on contact name. {{% /alert %}} 
## **Getting Contacts with EWS**
Aspose.Email provides the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class to connect to Microsoft Exchange Server using Exchange Web Services. The code snippets that follow use Exchange Web Services to read all the contacts. The following code snippet shows you how to get Contacts with EWS.



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
## **Resolve Contacts using Contact Name**
The following code snippet shows you how to use get contacts with EWS



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
## **Determining Contact Notes Format**
The NotesFormat specifies the contacts' notes text format type defined by TextFormat enumerator.

## **Fetch Contact using Id**
A particular contact can be retrieved from the server using its contact id as shown in the following code sample.



~~~Java
Contact fetchedContact = client.getContact(id);
~~~
## **Adding Contacts**
The [EWSClient](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) class [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) method can be used to add Contact information to an Exchange Server. The [createContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#createContact\(com.aspose.email.Contact\)) method takes a [Contact](https://apireference.aspose.com/email/java/com.aspose.email/Contact) object as an input parameter.

To add contacts to an Exchange Server:

1. Initialize the EWSClient with address and credentials.
1. Initialize the Contact object with the desired properties.
1. Call the CreateContact method to add the contact to the Exchange Server.

Aspose.Email provides the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class to connect to Microsoft Exchange Server using Exchange Web Services. The code snippets shows you how to follow use Exchange Web Services to add contacts to an Exchange Server.



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
## **Updating Contacts**
Contact information can be updated using Microsoft Outlook. Aspose.Email can also update contact information on Exchange Server using the Exchange Web Service (EWS). The [IEWSClient's](https://apireference.aspose.com/email//java/com.aspose.email/iewsclient) [updateContact()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#updateContact\(com.aspose.email.Contact\)) method can update contact information on Exchange Server.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

// List all the contacts and Loop through all contacts
Contact[] contacts = client.getContacts(client.getMailboxInfo().getContactsUri());
Contact contact = contacts[0];
System.out.println("Name: " + contact.getDisplayName());
contact.setDisplayName("David Ch");
client.updateContact(contact);
~~~
## **Deleting Contacts**
The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/iewsclient) class provides the [deleteItem](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#deleteItem\(java.lang.String,%20com.aspose.email.DeletionOptions\)) to access and delete contacts from an Exchange Server's contacts folder. This method takes the contact ID as an input parameter.

To delete contacts from an Exchange Server:

1. Initialize the ExchangeWebServiceClient with address and credentials.
1. Delete a contact using its ID.

The following code snippets shows you how to deleting contacts from an exchange server using exchange web service.



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