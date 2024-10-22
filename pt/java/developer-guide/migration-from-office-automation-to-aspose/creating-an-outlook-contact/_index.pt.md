---
title: "Criando um Contato do Outlook"
url: /pt/java/creating-an-outlook-contact/
weight: 70
type: docs
---


{{% alert color="primary" %}} 

Esta dica de migração mostra como criar um contato do Microsoft Outlook usando [Automação do Microsoft Office](#office-automation) e [Aspose.Email](#asposeemail-for-java). O exemplo de código mostra como definir diferentes informações de um Contato, como informações Pessoais, Profissionais e Empresariais. Criar um contato do Outlook consiste nas seguintes etapas:

1. Criar um objeto Contato.
1. Preencher ou definir as várias propriedades do objeto.
1. Salvar o objeto.

{{% /alert %}} 
## **Automação do Office**
Para usar a Automação do Office, o Microsoft Outlook deve estar instalado na máquina onde o código é executado. Também é necessária uma referência ao Outlook.interop.dll.
### **Exemplos de Programação**
O seguinte trecho de código cria um contato do Outlook em formato VCard e o salva no disco usando a Automação do Office.

**C#**

~~~cs

 Microsoft.Office.Interop.Outlook._Application OutlookObject = new Microsoft.Office.Interop.Outlook.Application();

//Criar um novo Item de Contato

Microsoft.Office.Interop.Outlook.ContactItem contact = OutlookObject.CreateItem(

                        Microsoft.Office.Interop.Outlook.OlItemType.olContactItem);

//Definir diferentes propriedades deste Item de Contato.

contact.FirstName = "Mellissa";

contact.LastName = "MacBeth";

contact.JobTitle = "Representante de Contas";

contact.CompanyName = "Contoso Ltd.";

contact.OfficeLocation = "36/2529";

contact.BusinessTelephoneNumber = "4255551212 x432";

contact.BusinessAddressStreet = "1 Microsoft Way";

contact.BusinessAddressCity = "Redmond";

contact.BusinessAddressState = "WA";

contact.BusinessAddressPostalCode = "98052";

contact.BusinessAddressCountry = "Estados Unidos da América";

contact.Email1Address = "melissa@contoso.com";

contact.Email1AddressType = "SMTP";

contact.Email1DisplayName = "Melissa MacBeth (mellissa@contoso.com)";

//Salvar o Contato no disco

contact.SaveAs("OutlookContact.vcf", OlSaveAsType.olVCard); 

~~~
## **Aspose.Email for Java**
Os exemplos abaixo utilizam o Aspose.Email para criar o contato do Outlook em formato VCard e salvá-lo no disco. O exemplo mostra como criar um contato usando a classe [MapiContact](https://apireference.aspose.com/email/java/com.aspose.email/MapiContact) e definindo os detalhes do contato no objeto antes de salvar o contato.
### **Exemplos de Programação**

~~~Java

//Criar um novo Objeto MapiContact
MapiContact mapiContact = new MapiContact();

//Definir diferentes propriedades deste objeto Contato
mapiContact.setNameInfo(new MapiContactNamePropertySet("Mellissa", "", "MacBeth"));
mapiContact.getProfessionalInfo().setTitle("Representante de Contas");
mapiContact.getProfessionalInfo().setCompanyName("Contoso Ltd.");
mapiContact.getProfessionalInfo().setOfficeLocation("36/2529");
mapiContact.getTelephones().setBusinessTelephoneNumber("4255551212 x432");
mapiContact.getPhysicalAddresses().getWorkAddress().setStreet("1 Microsoft Way");
mapiContact.getPhysicalAddresses().getWorkAddress().setCity("Redmond");
mapiContact.getPhysicalAddresses().getWorkAddress().setStateOrProvince("WA");
mapiContact.getPhysicalAddresses().getWorkAddress().setPostalCode("98052");
mapiContact.getPhysicalAddresses().getWorkAddress().setCountry("Estados Unidos da América");
mapiContact.getElectronicAddresses().getEmail1().setEmailAddress("milissa@contoso.com");
mapiContact.getElectronicAddresses().getEmail1().setAddressType("SMTP");
mapiContact.getElectronicAddresses().getEmail1().setDisplayName("Melissa MacBeth (mellissa@contoso.com)");

//Salvar o objeto Contato no disco
mapiContact.save("Contact.vcf", ContactSaveFormat.VCard);

~~~