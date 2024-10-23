---
title: "Trabalhando com Contatos do Gmail"
url: /pt/java/trabalhando-com-contatos-do-gmail/
weight: 30
type: docs
---


Aspose.Email suporta trabalhar com contatos do Gmail. Usando a interface [IGmailClient](https://apireference.aspose.com/email/java/com.aspose.email/IGmailClient), os usuários podem recuperar contatos de uma conta do Gmail, criar novos contatos e atualizar, bem como excluir contatos existentes. O Gmail permite que os desenvolvedores realizem todas essas ações usando sua API pública para desenvolvedores. As seguintes informações do usuário são necessárias para trabalhar com contatos do Gmail:
Nome de usuário, endereço de e-mail, senha, ID do cliente, segredo do cliente, token de atualização.

## **Acessando Contatos do Gmail**
A seguir está um aplicativo de exemplo que pode ser usado para acessar os detalhes dos contatos em todos os grupos.



~~~Java
        try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {
            Contact[] contacts = client.getAllContacts();
            for (Contact contact : contacts)
                System.out.println(contact.getDisplayName() + ", " + contact.getEmailAddresses().get_Item(0));

            // Buscar contatos de um grupo específico
            ContactGroupCollection groups = client.getAllGroups();
            GoogleContactGroup group = null;
            for (GoogleContactGroup g : groups) {
                if ("TestGroup".equals(g.getTitle())) {
                    group = g;
                }
            }

            // Recuperar contatos do Grupo
            if (group != null) {
                Contact[] contacts2 = client.getContactsFromGroup(group.getId());
                for (Contact con : contacts2)
                    System.out.println(con.getDisplayName() + "," + con.getEmailAddresses().get_Item(0).toString());
            }
        }

~~~
## **Criando Contato**
O seguinte trecho de código mostra como criar um contato.



~~~Java
// Criar um Contato
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

// Endereço de E-mail
EmailAddress eAddress = new EmailAddress();
eAddress.setAddress("email@gmail.com");
contact.getEmailAddresses().add(eAddress);
String contactUri = client.createContact(contact);
~~~
## **Atualizando Contato**
Uma vez que um contato é recuperado, seus atributos podem ser atualizados e o contato pode ser salvo de volta na conta do Gmail. O seguinte trecho de código mostra como recuperar contatos de uma conta do Gmail e, em seguida, modifica um desses que é salvo de volta.



~~~Java
try (IGmailClient client = GmailClient.getInstance(accessToken, email)) {

    Contact[] contacts = client.getAllContacts();
    Contact contact = contacts[0];
    contact.setJobTitle("Gerente de TI");
    contact.setDepartmentName("Suporte ao Cliente");
    contact.setCompanyName("Aspose");
    contact.setProfession("Desenvolvedor de Software");
    client.updateContact(contact);
}
~~~
## **Excluindo Contato**
Para excluir um contato do Gmail, o método DeleteContact do cliente Gmail é utilizado, conforme mostrado no seguinte trecho de exemplo.



~~~Java
client.deleteContact(contact.getId().getGoogleId());
~~~
## **Salvando Contato**
Aspose.Email permite salvar contatos em vários formatos de saída, como MSG e VCF. O método Save oferece a capacidade de alcançar isso. O seguinte trecho de código mostra como salvar um contato.



~~~Java
contact.save(dataDir + "contato_saida.msg", ContactSaveFormat.Msg);
contact.save(dataDir + "contato_saida.vcf", ContactSaveFormat.VCard);
~~~