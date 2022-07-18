---
title: Working with Gmail Contacts
type: docs
weight: 30
url: /java/working-with-gmail-contacts/
---


Aspose.Email supports working with Gmail contacts. Using the [IGmailClient](https://reference.aspose.com/email/java/com.aspose.email/IGmailClient) interface, users can retrieve contacts from a Gmail account, create new contacts, and update as well as delete existing contacts. Gmail allows developers to perform all these using its public developer's API. The following user information is required for working with Gmail contacts:
User name, email address, password, client ID, client secret refresh token.

## **Access Gmail Contacts**
Following is a sample application which can be used to access the detail of contacts in all the groups.



~~~Java
        try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
            Contact[] contacts = client.getAllContacts();
            for (Contact contact : contacts)
                System.out.println(contact.getDisplayName() + ", " + contact.getEmailAddresses().get_Item(0));

            // Fetch contacts from a specific group
            ContactGroupCollection groups = client.getAllGroups();
            GoogleContactGroup group = null;
            for (GoogleContactGroup g : groups) {
                if ("TestGroup".equals(g.getTitle())) {
                    group = g;
                }
            }

            // Retrieve contacts from the Group
            if (group != null) {
                Contact[] contacts2 = client.getContactsFromGroup(group.getId());
                for (Contact con : contacts2)
                    System.out.println(con.getDisplayName() + "," + con.getEmailAddresses().get_Item(0).toString());
            }
        }

~~~
## **Creating Contact**
The following code snippet shows you how to creating contact.



~~~Java
// Create a Contact
Contact contact = new Contact();
contact.setPrefix("Prefix");
contact.setGivenName("GivenName");
contact.setSurname("Surname");
contact.setMiddleName("MiddleName");
contact.setDisplayName("DisplayName");
contact.setSuffix("Suffix");

contact.setJobTitle("JobTitle");
contact.setDepartmentName("DepartmentName");
contact.setCompanyName("CompanyName");
contact.setProfession("Profession");

contact.setNotes("Notes");

PostalAddress address = new PostalAddress();
address.setCategory(PostalAddressCategory.getWork());
address.setAddress("Address");
address.setStreet("Street");
address.setPostOfficeBox("PostOfficeBox");
address.setCity("City");
address.setStateOrProvince("StateOrProvince");
address.setPostalCode("PostalCode");
address.setCountry("Country");
contact.getPhysicalAddresses().add(address);

PhoneNumber pnWork = new PhoneNumber();
pnWork.setNumber("323423423423");
pnWork.setCategory(PhoneNumberCategory.getWork());
contact.getPhoneNumbers().add(pnWork);
PhoneNumber pnHome = new PhoneNumber();
pnHome.setNumber("323423423423");
pnHome.setCategory(PhoneNumberCategory.getHome());
contact.getPhoneNumbers().add(pnHome);
PhoneNumber pnMobile = new PhoneNumber();
pnMobile.setNumber("323423423423");
pnMobile.setCategory(PhoneNumberCategory.getMobile());
contact.getPhoneNumbers().add(pnMobile);

contact.getUrls().setBlog("Blog.com");
contact.getUrls().setBusinessHomePage("BusinessHomePage.com");
contact.getUrls().setHomePage("HomePage.com");
contact.getUrls().setProfile("Profile.com");

contact.getEvents().setBirthday(new Date());
contact.getEvents().setAnniversary(new Date());

contact.getInstantMessengers().setAIM("AIM");
contact.getInstantMessengers().setGoogleTalk("GoogleTalk");
contact.getInstantMessengers().setICQ("ICQ");
contact.getInstantMessengers().setJabber("Jabber");
contact.getInstantMessengers().setMSN("MSN");
contact.getInstantMessengers().setQQ("QQ");
contact.getInstantMessengers().setSkype("Skype");
contact.getInstantMessengers().setYahoo("Yahoo");

contact.getAssociatedPersons().setSpouse("Spouse");
contact.getAssociatedPersons().setSister("Sister");
contact.getAssociatedPersons().setRelative("Relative");
contact.getAssociatedPersons().setReferredBy("ReferredBy");
contact.getAssociatedPersons().setPartner("Partner");
contact.getAssociatedPersons().setParent("Parent");
contact.getAssociatedPersons().setMother("Mother");
contact.getAssociatedPersons().setManager("Manager");

// Email Address
EmailAddress eAddress = new EmailAddress();
eAddress.setAddress("email@gmail.com");
contact.getEmailAddresses().add(eAddress);
String contactUri = client.createContact(contact);
~~~
## **Updating Contact**
Once a contact is retrieved, its attributes can be updated and the contact can be saved back to the Gmail account. The following code snippet shows you how to retrieves contacts from a Gmail account and then modifies one of these which is then saved back.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {

    Contact[] contacts = client.getAllContacts();
    Contact contact = contacts[0];
    contact.setJobTitle("Manager IT");
    contact.setDepartmentName("Customer Support");
    contact.setCompanyName("Aspose");
    contact.setProfession("Software Developer");
    client.updateContact(contact);
}
~~~
## **Deleting Contact**
In order to delete a Gmail contact, the Gmail client's DeleteContact method is used as shown in the following sample snippet.



~~~Java
client.deleteContact(contact.getId().getGoogleId());
~~~
## **Saving Contact**
Aspose.Email allows saving contact to various output formats such as MSG and VCF. The Save method provides the capability to achieve this. The following code snippet shows you how to save contact.



~~~Java
contact.save(dataDir + "contact_out.msg", ContactSaveFormat.Msg);
contact.save(dataDir + "contact_out.vcf", ContactSaveFormat.VCard);
~~~
