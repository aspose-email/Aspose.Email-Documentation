---
title: Creating and Saving Outlook Contacts in PHP
ArticleTitle: Creating and Saving Outlook Contacts in PHP
type: docs
weight: 10
url: /java/creating-and-saving-outlook-contacts-in-php/
---

## **Aspose.Email - Creating and Saving Outlook Contacts**
To Create Outlook Contacts using **Aspose.Email Java for PHP**, simply invoke **CreateOutlookContact** module. Here you can see example code.

**PHP Code**

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
## **Download Running Code**
Download **Creating and Saving Outlook Contacts (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookContact.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookContact.php)
