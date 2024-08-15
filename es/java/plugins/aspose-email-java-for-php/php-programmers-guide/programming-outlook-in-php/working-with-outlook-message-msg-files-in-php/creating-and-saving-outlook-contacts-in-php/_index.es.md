---
title: "Crear y guardar contactos de Outlook en PHP"
url: /es/java/creating-and-saving-outlook-contacts-in-php/
weight: 10
type: docs
---

## **Aspose.Email - Creación y almacenamiento de contactos de Outlook**
Para crear contactos de Outlook mediante **Aspose.Email Java para PHP**, simplemente invoca **CreateOutlookContact** módulo. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 $contact = new MapiContact();

\# Set different properties of this Contact Item.

\# Set Name properties using MapiContactNamePropertySet

$name_prop_set = new MapiContactNamePropertySet();

$name_prop_set->setSurname("Mellissa");

$name_prop_set->setGivenName("MacBeth");

$contact->setNameInfo($name_prop_set);

\# Set professional properties using MapiContactProfessionalPropertySet

$prof_prop_set = new MapiContactProfessionalPropertySet();

$prof_prop_set->setTitle("Account Representative");

$prof_prop_set->setCompanyName("Contoso Ltd.");

$prof_prop_set->setOfficeLocation("36/2529");

$contact->setProfessionalInfo($prof_prop_set);

\# Telephones

$telephone = new MapiContactTelephonePropertySet();

$telephone->setAssistantTelephoneNumber("(831) 758-7214");

$telephone->setBusiness2TelephoneNumber("(831) 759-2518");

$telephone->setBusinessTelephoneNumber("(831) 758-7285");

$telephone->setCallbackTelephoneNumber("(831) 758-7321 (After hours");

$telephone->setCarTelephoneNumber("(831) 758-7201");

$telephone->setCompanyMainTelephoneNumber("(831) 758-7368");

$telephone->setHome2TelephoneNumber("(831) 758-7256");

$telephone->setHomeTelephoneNumber("(831) 758-7257");

$telephone->setIsdnNumber("(831) 758-7381");

$telephone->setMobileTelephoneNumber("(831) 758-7368");

$telephone->setOtherTelephoneNumber("(831) 758-7201");

$telephone->setPagerTelephoneNumber("(831) 758-7368");

$telephone->setPrimaryTelephoneNumber("(831) 758-7334");

$telephone->setRadioTelephoneNumber("(831) 758-7234");

$telephone->setTelexNumber("(831) 758-7408");

$telephone->setTtyTddPhoneNumber("(800) 806-4474");

$contact->setTelephones($telephone);

\# Set Physical Address using MapiContactPhysicalAddress and MapiContactPhysicalAddressPropertySet

$phys_addrss = new MapiContactPhysicalAddress();

$phys_addrss->setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908");

$phys_addr_prop_set = new MapiContactPhysicalAddressPropertySet();

$phys_addr_prop_set->setWorkAddress($phys_addrss);

$contact->setPhysicalAddresses($phys_addr_prop_set);

\# Set email information using MapiContactElectronicAddress and MapiContactElectronicAddressPropertySet

$email = new MapiContactElectronicAddress();

$email->setAddressType("SMTP");

$email->setDisplayName("Melissa MacBeth (mellissa@contoso.com)");

$email->setEmailAddress("melissa@contoso.com");

$elec_addr_prop_set = new MapiContactElectronicAddressPropertySet();

$elec_addr_prop_set->setEmail1($email);

$contact->setElectronicAddresses($elec_addr_prop_set);

$contactSaveFormat=new ContactSaveFormat();

$contact->save($dataDir . "OutlookContact.vcf", $contactSaveFormat->VCard);

print "Created outlook contact successfully.".PHP_EOL;

```
## **Descargar Running Code**
Download **Creación y almacenamiento de contactos de Outlook (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookContact.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookContact.php)
