---
title: "Agregar MapiContact a PST en Python"
url: /es/java/adding-mapicontact-to-pst-in-python/
weight: 20
type: docs
---

## **Aspose.Email - Agregar MapiContact a PST**
Para agregar MapiContact a PST utilizando **Aspose.Email Java para Python**, use el siguiente código.

**Código en Python**

```python



\# Crear una instancia de MapiContact

mapi_contact = self.MapiContact()

\# Contacto #1

contact1 = self.MapiContact("Sebastian Wright", "SebastianWright@dayrep.com")

\# Contacto #2

contact2 = self.MapiContact("Wichert Kroos", "WichertKroos@teleworm.us", "Inversión de Grado A")

\# Contacto #3

contact3 = self.MapiContact("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Fábrica de Sofás Krauses", "046-630-4614")

\# Contacto #4

contact4 = self.MapiContact()

contact4.setNameInfo(self.MapiContactNamePropertySet("Margaret", "J.", "Tolle"))

mapiContactGender = self.MapiContactGender

contact4.getPersonalInfo().setGender(mapiContactGender.Female)

contact4.setProfessionalInfo(self.MapiContactProfessionalPropertySet("Adaptaz", "Ingeniero de grabación"))

contact4.getPhysicalAddresses().getWorkAddress().setAddress("4 Darwinia Loop EIGHTY MILE BEACH WA 6725")

contact4.getElectronicAddresses().setEmail1(self.MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com"))

contact4.getTelephones().setBusinessTelephoneNumber("(08)9080-1183")

contact4.getTelephones().setMobileTelephoneNumber("(925)599-3355")

\# Contacto #5

contact5 = self.MapiContact()

contact5.setNameInfo(self.MapiContactNamePropertySet("Matthew", "R.", "Wilcox"))

contact5.getPersonalInfo().setGender(mapiContactGender.Male)

contact5.setProfessionalInfo(self.MapiContactProfessionalPropertySet("Briazz", "Asistente psiquiátrico"))

contact5.getPhysicalAddresses().getWorkAddress().setAddress("Horner Strasse 12 4421 SAASS")

contact5.getTelephones().setBusinessTelephoneNumber("0650 675 73 30")

contact5.getTelephones().setHomeTelephoneNumber("(661)387-5382")

\# Contacto #6

contact6 = self.MapiContact()

contact6.setNameInfo(self.MapiContactNamePropertySet("Bertha", "A.", "Buell"))

contact6.setProfessionalInfo(self.MapiContactProfessionalPropertySet("Awthentikz", "Asistente de trabajo social"))

contact6.getPersonalInfo().setPersonalHomePage("B2BTies.com")

contact6.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT")

contact6.getElectronicAddresses().setEmail1(self.MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"))

contact6.setTelephones(self.MapiContactTelephonePropertySet("06605045265"))

personalStorage = self.PersonalStorage

fileFormatVersion = self.FileFormatVersion

standardIpmFolder = self.StandardIpmFolder

pst = personalStorage.create(self.dataDir + "MapiContactToPST1.pst", fileFormatVersion.Unicode)

contactFolder = pst.createPredefinedFolder("Contactos", standardIpmFolder.Contacts)

contactFolder.addMapiMessageItem(contact1)

contactFolder.addMapiMessageItem(contact2)

contactFolder.addMapiMessageItem(contact3)

contactFolder.addMapiMessageItem(contact4)

contactFolder.addMapiMessageItem(contact5)

contactFolder.addMapiMessageItem(contact6)

print "MapiContacts agregados con éxito."

```
## **Descargar Código en Ejecución**
Descargue **Agregar MapiContact a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)