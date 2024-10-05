---
title: "Работа с контактами Gmail"
url: /ru/java/working-with-gmail-contacts/
weight: 30
type: docs
---


Aspose.Email поддерживает работу с контактами Gmail. Используя интерфейс [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), пользователи могут извлекать контакты из учетной записи Gmail, создавать новые контакты, а также обновлять и удалять существующие контакты. Gmail позволяет разработчикам выполнять все эти действия с помощью своего публичного API для разработчиков. Следующая информация пользователя необходима для работы с контактами Gmail:
Имя пользователя, адрес электронной почты, пароль, идентификатор клиента, секрет клиента, токен обновления.

## **Доступ к контактам Gmail**
Ниже приведено примерное приложение, которое можно использовать для доступа к деталям контактов во всех группах.



~~~Java
        try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
            Contact[] contacts = client.getAllContacts();
            for (Contact contact : contacts)
                System.out.println(contact.getDisplayName() + ", " + contact.getEmailAddresses().get_Item(0));

            // Извлечение контактов из конкретной группы
            ContactGroupCollection groups = client.getAllGroups();
            GoogleContactGroup group = null;
            for (GoogleContactGroup g : groups) {
                if ("TestGroup".equals(g.getTitle())) {
                    group = g;
                }
            }

            // Извлечение контактов из группы
            if (group != null) {
                Contact[] contacts2 = client.getContactsFromGroup(group.getId());
                for (Contact con : contacts2)
                    System.out.println(con.getDisplayName() + "," + con.getEmailAddresses().get_Item(0).toString());
            }
        }

~~~
## **Создание контакта**
Следующий фрагмент кода показывает, как создать контакт.



~~~Java
// Создать контакт
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

// Адрес электронной почты
EmailAddress eAddress = new EmailAddress();
eAddress.setAddress("email@gmail.com");
contact.getEmailAddresses().add(eAddress);
String contactUri = client.createContact(contact);
~~~
## **Обновление контакта**
После извлечения контакта его атрибуты могут быть обновлены, и контакт может быть сохранен обратно в учетную запись Gmail. Следующий фрагмент кода показывает, как извлечь контакты из учетной записи Gmail, а затем изменить один из них, который затем сохраняется обратно.



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
## **Удаление контакта**
Для удаления контакта Gmail используется метод DeleteContact клиента Gmail, как показано в следующем примерном фрагменте кода.



~~~Java
client.deleteContact(contact.getId().getGoogleId());
~~~
## **Сохранение контакта**
Aspose.Email позволяет сохранять контакт в различных выходных форматах, таких как MSG и VCF. Метод Save предоставляет возможность достичь этого. Следующий фрагмент кода показывает, как сохранить контакт.



~~~Java
contact.save(dataDir + "contact_out.msg", ContactSaveFormat.Msg);
contact.save(dataDir + "contact_out.vcf", ContactSaveFormat.VCard);
~~~