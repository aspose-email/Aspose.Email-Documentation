---
title: "Создание и сохранение контактов Outlook в PHP"
url: /ru/java/creating-and-saving-outlook-contacts-in-php/
weight: 10
type: docs
---

## **Aspose.Email - Создание и сохранение контактов Outlook**
Чтобы создать контакты Outlook с помощью **Aspose.Email Java для PHP**, просто вызовите модуль **CreateOutlookContact**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 $contact = new MapiContact();

\# Установите разные свойства этого Контактного Элемента.

\# Установите свойства Имени, используя MapiContactNamePropertySet

$name_prop_set = new MapiContactNamePropertySet();

$name_prop_set->setSurname("Мелисса");

$name_prop_set->setGivenName("Макбет");

$contact->setNameInfo($name_prop_set);

\# Установите профессиональные свойства, используя MapiContactProfessionalPropertySet

$prof_prop_set = new MapiContactProfessionalPropertySet();

$prof_prop_set->setTitle("Представитель по аккаунтам");

$prof_prop_set->setCompanyName("Contoso Ltd.");

$prof_prop_set->setOfficeLocation("36/2529");

$contact->setProfessionalInfo($prof_prop_set);

\# Телефоны

$telephone = new MapiContactTelephonePropertySet();

$telephone->setAssistantTelephoneNumber("(831) 758-7214");

$telephone->setBusiness2TelephoneNumber("(831) 759-2518");

$telephone->setBusinessTelephoneNumber("(831) 758-7285");

$telephone->setCallbackTelephoneNumber("(831) 758-7321 (после работы");

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

\# Установите физический адрес, используя MapiContactPhysicalAddress и MapiContactPhysicalAddressPropertySet

$phys_addrss = new MapiContactPhysicalAddress();

$phys_addrss->setPostOfficeBox("144 Hitchcock Rd, Salinas, CA 93908");

$phys_addr_prop_set = new MapiContactPhysicalAddressPropertySet();

$phys_addr_prop_set->setWorkAddress($phys_addrss);

$contact->setPhysicalAddresses($phys_addr_prop_set);

\# Установите информацию по электронной почте, используя MapiContactElectronicAddress и MapiContactElectronicAddressPropertySet

$email = new MapiContactElectronicAddress();

$email->setAddressType("SMTP");

$email->setDisplayName("Мелисса Макбет (mellissa@contoso.com)");

$email->setEmailAddress("melissa@contoso.com");

$elec_addr_prop_set = new MapiContactElectronicAddressPropertySet();

$elec_addr_prop_set->setEmail1($email);

$contact->setElectronicAddresses($elec_addr_prop_set);

$contactSaveFormat=new ContactSaveFormat();

$contact->save($dataDir . "OutlookContact.vcf", $contactSaveFormat->VCard);

print "Контакт Outlook успешно создан.".PHP_EOL;

```
## **Скачать работающий код**
Скачайте **Создание и сохранение контактов Outlook (Aspose.Email)** с любого из ниже упомянутых социальных кодировочных сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookContact.php)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaphp#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookMessageFiles/CreateOutlookContact.php)