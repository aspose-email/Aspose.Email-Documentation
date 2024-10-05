---
title: "Добавление MapiContact в PST на PHP"
url: /ru/java/adding-mapicontact-to-pst-in-php/
weight: 30
type: docs
---

## **Aspose.Email - Добавление MapiContact в PST**
Чтобы добавить MapiContact в PST с использованием **Aspose.Email Java для PHP**, просто вызовите модуль **AddMapiContactToPST**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 # Создайте экземпляр MapiContact

$mapi_contact = new MapiContact();

\# Контакт #1

$contact1 = new MapiContact("Себастиан Райт", "SebastianWright@dayrep.com");

\# Контакт #2

$contact2 = new MapiContact("Вихерт Кроос", "WichertKroos@teleworm.us", "Инвестиции высшей категории");

\# Контакт #3

$contact3 = new MapiContact("Кристоффер ван де Мееберг", "ChristoffervandeMeeberg@teleworm.us", "Фабрика диванов Крауса", "046-630-4614");

\# Контакт #4

$contact4 = new MapiContact();

$contact4->setNameInfo(new MapiContactNamePropertySet("Маргарет", "Д.", "Толле"));

$mapiContactGender=new MapiContactGender();

$contact4->getPersonalInfo()->setGender($mapiContactGender->Female);

$contact4->setProfessionalInfo(new MapiContactProfessionalPropertySet("Адаптаз", "Записывающий инженер"));

$contact4->getPhysicalAddresses()->getWorkAddress()->setAddress("4 Darwinia Loop EIGHTY MILE BEACH WA 6725");

$contact4->getElectronicAddresses()->setEmail1(new MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com"));

$contact4->getTelephones()->setBusinessTelephoneNumber("(08)9080-1183");

$contact4->getTelephones()->setMobileTelephoneNumber("(925)599-3355");

\# Контакт #5

$contact5 = new MapiContact();

$contact5->setNameInfo(new MapiContactNamePropertySet("Мэтью", "Р.", "Уилкокс"));

$contact5->getPersonalInfo()->setGender($mapiContactGender->Male);

$contact5->setProfessionalInfo(new MapiContactProfessionalPropertySet("Бриазз", "Психиатрический помощник"));

$contact5->getPhysicalAddresses()->getWorkAddress()->setAddress("Horner Strasse 12 4421 SAASS");

$contact5->getTelephones()->setBusinessTelephoneNumber("0650 675 73 30");

$contact5->getTelephones()->setHomeTelephoneNumber("(661)387-5382");

\# Контакт #6

$contact6 = new MapiContact();

$contact6->setNameInfo(new MapiContactNamePropertySet("Берта", "А.", "Буэлл"));

$contact6->setProfessionalInfo(new MapiContactProfessionalPropertySet("Awthentikz", "Ассистент по социальной работе"));

$contact6->getPersonalInfo()->setPersonalHomePage("B2BTies.com");

$contact6->getPhysicalAddresses()->getWorkAddress()->setAddress("Im Astenfeld 59 8580 EDELSCHROTT");

$contact6->getElectronicAddresses()->setEmail1(new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"));

$contact6->setTelephones(new MapiContactTelephonePropertySet("06605045265"));

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$standardIpmFolder=new StandardIpmFolder();

$pst = $personalStorage->create($dataDir . "MapiContactToPST1.pst", $fileFormatVersion->Unicode);

$contactFolder = $pst->createPredefinedFolder("Контакты", $standardIpmFolder->Contacts);

$contactFolder->addMapiMessageItem($contact1);

$contactFolder->addMapiMessageItem($contact2);

$contactFolder->addMapiMessageItem($contact3);

$contactFolder->addMapiMessageItem($contact4);

$contactFolder->addMapiMessageItem($contact5);

$contactFolder->addMapiMessageItem($contact6);

print "MapiContacts добавлены успешно.".PHP_EOL;

```
## **Скачать рабочий код**
Скачайте **Добавление MapiContact в PST (Aspose.Email)** с любого из нижеупомянутых сайтов для социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiContactToPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiContactToPST.php)