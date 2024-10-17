---
title: "Trabajando con Contactos de Gmail"
url: /es/java/trabajando-con-contactos-de-gmail/
weight: 30
type: docs
---


Aspose.Email admite trabajar con contactos de Gmail. Usando la interfaz [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), los usuarios pueden recuperar contactos de una cuenta de Gmail, crear nuevos contactos y actualizar así como eliminar contactos existentes. Gmail permite a los desarrolladores realizar todas estas acciones utilizando su API pública para desarrolladores. La siguiente información del usuario es requerida para trabajar con contactos de Gmail:
Nombre de usuario, dirección de correo electrónico, contraseña, ID de cliente, secreto del cliente, token de actualización.

## **Acceso a Contactos de Gmail**
A continuación se presenta una aplicación de ejemplo que se puede utilizar para acceder a los detalles de los contactos en todos los grupos.



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
## **Crear Contacto**
El siguiente fragmento de código te muestra cómo crear un contacto.



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
## **Actualizar Contacto**
Una vez que se recupera un contacto, sus atributos se pueden actualizar y el contacto se puede guardar nuevamente en la cuenta de Gmail. El siguiente fragmento de código te muestra cómo recuperar contactos de una cuenta de Gmail y luego modificar uno de ellos que se guarda nuevamente.



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
## **Eliminar Contacto**
Para eliminar un contacto de Gmail, se utiliza el método DeleteContact del cliente de Gmail, como se muestra en el siguiente fragmento de ejemplo.



~~~Java
client.deleteContact(contact.getId().getGoogleId());
~~~
## **Guardar Contacto**
Aspose.Email permite guardar contactos en varios formatos de salida como MSG y VCF. El método Save proporciona la capacidad para lograr esto. El siguiente fragmento de código te muestra cómo guardar un contacto.



~~~Java
contact.save(dataDir + "contact_out.msg", ContactSaveFormat.Msg);
contact.save(dataDir + "contact_out.vcf", ContactSaveFormat.VCard);
~~~