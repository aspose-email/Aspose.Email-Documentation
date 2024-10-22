---
title: "Agregando MapiContact a PST en PHP"
url: /es/java/adding-mapicontact-to-pst-in-php/
weight: 30
type: docs
---

## **Aspose.Email - Agregando MapiContact a PST**
Para agregar MapiContact a PST usando **Aspose.Email Java para PHP**, simplemente invoca el módulo **AddMapiContactToPST**. Aquí puedes ver un ejemplo de código.

**Código PHP**

``` php

 # Crear una instancia de MapiContact

$mapi_contact = new MapiContact();

\# Contacto #1

$contact1 = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");

\# Contacto #2

$contact2 = new MapiContact("Wichert Kroos", "WichertKroos@teleworm.us", "Inversión de Grado A");

\# Contacto #3

$contact3 = new MapiContact("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Krauses Sofa Factory", "046-630-4614");

\# Contacto #4

$contact4 = new MapiContact();

$contact4->setNameInfo(new MapiContactNamePropertySet("Margaret", "J.", "Tolle"));

$mapiContactGender=new MapiContactGender();

$contact4->getPersonalInfo()->setGender($mapiContactGender->Female);

$contact4->setProfessionalInfo(new MapiContactProfessionalPropertySet("Adaptaz", "Ingeniero de grabación"));

$contact4->getPhysicalAddresses()->getWorkAddress()->setAddress("4 Darwinia Loop EIGHTY MILE BEACH WA 6725");

$contact4->getElectronicAddresses()->setEmail1(new MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com"));

$contact4->getTelephones()->setBusinessTelephoneNumber("(08)9080-1183");

$contact4->getTelephones()->setMobileTelephoneNumber("(925)599-3355");

\# Contacto #5

$contact5 = new MapiContact();

$contact5->setNameInfo(new MapiContactNamePropertySet("Matthew", "R.", "Wilcox"));

$contact5->getPersonalInfo()->setGender($mapiContactGender->Male);

$contact5->setProfessionalInfo(new MapiContactProfessionalPropertySet("Briazz", "Asistente psiquiátrico"));

$contact5->getPhysicalAddresses()->getWorkAddress()->setAddress("Horner Strasse 12 4421 SAASS");

$contact5->getTelephones()->setBusinessTelephoneNumber("0650 675 73 30");

$contact5->getTelephones()->setHomeTelephoneNumber("(661)387-5382");

\# Contacto #6

$contact6 = new MapiContact();

$contact6->setNameInfo(new MapiContactNamePropertySet("Bertha", "A.", "Buell"));

$contact6->setProfessionalInfo(new MapiContactProfessionalPropertySet("Awthentikz", "Asistente de trabajo social"));

$contact6->getPersonalInfo()->setPersonalHomePage("B2BTies.com");

$contact6->getPhysicalAddresses()->getWorkAddress()->setAddress("Im Astenfeld 59 8580 EDELSCHROTT");

$contact6->getElectronicAddresses()->setEmail1(new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"));

$contact6->setTelephones(new MapiContactTelephonePropertySet("06605045265"));

$personalStorage=new PersonalStorage();

$fileFormatVersion=new FileFormatVersion();

$standardIpmFolder=new StandardIpmFolder();

$pst = $personalStorage->create($dataDir . "MapiContactToPST1.pst", $fileFormatVersion->Unicode);

$contactFolder = $pst->createPredefinedFolder("Contactos", $standardIpmFolder->Contacts);

$contactFolder->addMapiMessageItem($contact1);

$contactFolder->addMapiMessageItem($contact2);

$contactFolder->addMapiMessageItem($contact3);

$contactFolder->addMapiMessageItem($contact4);

$contactFolder->addMapiMessageItem($contact5);

$contactFolder->addMapiMessageItem($contact6);

print "MapiContacts añadidos exitosamente.".PHP_EOL;

```
## **Descargar Código en Ejecución**
Descarga **Agregando MapiContact a PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiContactToPST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiContactToPST.php)