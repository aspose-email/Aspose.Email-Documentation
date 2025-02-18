---
title: "Añadiendo MapiContact a PST en Ruby"
url: /es/java/adding-mapicontact-to-pst-in-ruby/
weight: 30
type: docs
---

## **Aspose.Email - Añadiendo MapiContact a PST**
Para añadir MapiContact a PST usando **Aspose.Email Java for Ruby**, simplemente invoca el módulo **AddMapiContactToPST**. Aquí puedes ver un código de ejemplo.

**Código en Ruby**

```ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Crear una instancia de MapiContact

mapi_contact = Rjb::import('com.aspose.email.MapiContact')

\# Contacto #1

contact1 = mapi_contact.new("Sebastian Wright", "SebastianWright@dayrep.com")

\# Contacto #2

contact2 = mapi_contact.new("Wichert Kroos", "WichertKroos@teleworm.us", "Inversión de Grado A")

\# Contacto #3

contact3 = mapi_contact.new("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Krauses Sofa Factory", "046-630-4614")

\# Contacto #4

contact4 = Rjb::import('com.aspose.email.MapiContact').new

contact4.setNameInfo(Rjb::import('com.aspose.email.MapiContactNamePropertySet').new("Margaret", "J.", "Tolle"))

contact4.getPersonalInfo().setGender(Rjb::import('com.aspose.email.MapiContactGender').Female)

contact4.setProfessionalInfo(Rjb::import('com.aspose.email.MapiContactProfessionalPropertySet').new("Adaptaz", "Ingeniero de grabación"))

contact4.getPhysicalAddresses().getWorkAddress().setAddress("4 Darwinia Loop EIGHTY MILE BEACH WA 6725")

contact4.getElectronicAddresses().setEmail1(Rjb::import('com.aspose.email.MapiContactElectronicAddress').new("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com"))

contact4.getTelephones().setBusinessTelephoneNumber("(08)9080-1183")

contact4.getTelephones().setMobileTelephoneNumber("(925)599-3355")

\# Contacto #5

contact5 = Rjb::import('com.aspose.email.MapiContact').new

contact5.setNameInfo(Rjb::import('com.aspose.email.MapiContactNamePropertySet').new("Matthew", "R.", "Wilcox"))

contact5.getPersonalInfo().setGender(Rjb::import('com.aspose.email.MapiContactGender').Male)

contact5.setProfessionalInfo(Rjb::import('com.aspose.email.MapiContactProfessionalPropertySet').new("Briazz", "Ayudante psiquiátrico"))

contact5.getPhysicalAddresses().getWorkAddress().setAddress("Horner Strasse 12 4421 SAASS")

contact5.getTelephones().setBusinessTelephoneNumber("0650 675 73 30")

contact5.getTelephones().setHomeTelephoneNumber("(661)387-5382")

\# Contacto #6

contact6 = Rjb::import('com.aspose.email.MapiContact').new

contact6.setNameInfo(Rjb::import('com.aspose.email.MapiContactNamePropertySet').new("Bertha", "A.", "Buell"))

contact6.setProfessionalInfo(Rjb::import('com.aspose.email.MapiContactProfessionalPropertySet').new("Awthentikz", "Asistente de trabajo social"))

contact6.getPersonalInfo().setPersonalHomePage("B2BTies.com")

contact6.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT")

contact6.getElectronicAddresses().setEmail1(Rjb::import('com.aspose.email.MapiContactElectronicAddress').new("Experwas", "SMTP", "BerthaABuell@armyspy.com"))

contact6.setTelephones(Rjb::import('com.aspose.email.MapiContactTelephonePropertySet').new("06605045265"))

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "MapiContactToPST.pst", Rjb::import('com.aspose.email.FileFormatVersion').Unicode)

contactFolder = pst.createPredefinedFolder("Contactos", Rjb::import('com.aspose.email.StandardIpmFolder').Contacts)

contactFolder.addMapiMessageItem(contact1)

contactFolder.addMapiMessageItem(contact2)

contactFolder.addMapiMessageItem(contact3)

contactFolder.addMapiMessageItem(contact4)

contactFolder.addMapiMessageItem(contact5)

contactFolder.addMapiMessageItem(contact6)

puts "MapiContacts añadidos con éxito."

```
## **Descargar Código en Ejecución**
Descarga **Añadiendo MapiContact a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/addmapicontacttopst.rb)