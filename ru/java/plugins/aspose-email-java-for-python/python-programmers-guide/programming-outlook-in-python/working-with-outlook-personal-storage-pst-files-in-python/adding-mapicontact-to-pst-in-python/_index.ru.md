---
title: "Добавление MapiContact в PST с помощью Python"
url: /ru/java/adding-mapicontact-to-pst-in-python/
weight: 20
type: docs
---

## **Aspose.Email - Добавление MapiContact в PST**
Чтобы добавить MapiContact в PST с помощью **Aspose.Email Java для Python**, используйте следующий код.

**Код на Python**

```python



\# Создайте экземпляр MapiContact

mapi_contact = self.MapiContact()

\# Контакт #1

contact1 = self.MapiContact("Sebastian Wright", "SebastianWright@dayrep.com")

\# Контакт #2

contact2 = self.MapiContact("Wichert Kroos", "WichertKroos@teleworm.us", "Grade A Investment")

\# Контакт #3

contact3 = self.MapiContact("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Krauses Sofa Factory", "046-630-4614")

\# Контакт #4

contact4 = self.MapiContact()

contact4.setNameInfo(self.MapiContactNamePropertySet("Margaret", "J.", "Tolle"))

mapiContactGender = self.MapiContactGender

contact4.getPersonalInfo().setGender(mapiContactGender.Female)

contact4.setProfessionalInfo(self.MapiContactProfessionalPropertySet("Adaptaz", "Recording engineer"))

contact4.getPhysicalAddresses().getWorkAddress().setAddress("4 Darwinia Loop EIGHTY MILE BEACH WA 6725")

contact4.getElectronicAddresses().setEmail1(self.MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com"))

contact4.getTelephones().setBusinessTelephoneNumber("(08)9080-1183")

contact4.getTelephones().setMobileTelephoneNumber("(925)599-3355")

\# Контакт #5

contact5 = self.MapiContact()

contact5.setNameInfo(self.MapiContactNamePropertySet("Matthew", "R.", "Wilcox"))

contact5.getPersonalInfo().setGender(mapiContactGender.Male)

contact5.setProfessionalInfo(self.MapiContactProfessionalPropertySet("Briazz", "Psychiatric aide"))

contact5.getPhysicalAddresses().getWorkAddress().setAddress("Horner Strasse 12 4421 SAASS")

contact5.getTelephones().setBusinessTelephoneNumber("0650 675 73 30")

contact5.getTelephones().setHomeTelephoneNumber("(661)387-5382")

\# Контакт #6

contact6 = self.MapiContact()

contact6.setNameInfo(self.MapiContactNamePropertySet("Bertha", "A.", "Buell"))

contact6.setProfessionalInfo(self.MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant"))

contact6.getPersonalInfo().setPersonalHomePage("B2BTies.com")

contact6.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT")

contact6.getElectronicAddresses().setEmail1(self.MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"))

contact6.setTelephones(self.MapiContactTelephonePropertySet("06605045265"))

personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

standardIpmFolder = self.StandardIpmFolder

pst = personalStorage.create(self.dataDir + "MapiContactToPST1.pst", fileFormatVersion.Unicode)

contactFolder = pst.createPredefinedFolder("Контакты", standardIpmFolder.Contacts)

contactFolder.addMapiMessageItem(contact1)

contactFolder.addMapiMessageItem(contact2)

contactFolder.addMapiMessageItem(contact3)

contactFolder.addMapiMessageItem(contact4)

contactFolder.addMapiMessageItem(contact5)

contactFolder.addMapiMessageItem(contact6)

print "MapiContacts успешно добавлены."

```
## **Скачать работающий код**
Скачайте **Добавление MapiContact в PST (Aspose.Email)** с любого из указанных ниже сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)