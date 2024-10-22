---
title: "Agregar MapiContact a PST en Jython"
url: /es/java/adding-mapicontact-to-pst-in-jython/
weight: 30
type: docs
---

## **Aspose.Email - Agregar MapiContact a PST**
Para agregar MapiContact a PST usando **Aspose.Email Java para Jython**, simplemente invoque el módulo **AddMapiContactToPST**. Aquí puede ver un ejemplo de código.

**Código Jython**

```python

 from aspose-email import Settings

from com.aspose.email import MapiContact

from com.aspose.email import MapiContactNamePropertySet

from com.aspose.email import MapiContactGender

from com.aspose.email import MapiContactProfessionalPropertySet

from com.aspose.email import MapiContactElectronicAddress

from com.aspose.email import MapiContactTelephonePropertySet

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

class AddMapiContactToPST:

    def __init__(self):

        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiContactToPST/'

        # Crear una instancia de MapiContact

        mapi_contact = MapiContact()

        # Contacto #1

        contact1 = MapiContact("Sebastian Wright", "SebastianWright@dayrep.com")

        # Contacto #2

        contact2 = MapiContact("Wichert Kroos", "WichertKroos@teleworm.us", "Grade A Investment")

        # Contacto #3

        contact3 = MapiContact("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Krauses Sofa Factory", "046-630-4614")

        # Contacto #4

        contact4 = MapiContact()

        contact4.setNameInfo(MapiContactNamePropertySet("Margaret", "J.", "Tolle"))

        mapiContactGender=MapiContactGender

        contact4.getPersonalInfo().setGender(mapiContactGender.Female)

        contact4.setProfessionalInfo(MapiContactProfessionalPropertySet("Adaptaz", "Recording engineer"))

        contact4.getPhysicalAddresses().getWorkAddress().setAddress("4 Darwinia Loop EIGHTY MILE BEACH WA 6725")

        contact4.getElectronicAddresses().setEmail1(MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com"))

        contact4.getTelephones().setBusinessTelephoneNumber("(08)9080-1183")

        contact4.getTelephones().setMobileTelephoneNumber("(925)599-3355")

        # Contacto #5

        contact5 = MapiContact()

        contact5.setNameInfo(MapiContactNamePropertySet("Matthew", "R.", "Wilcox"))

        contact5.getPersonalInfo().setGender(mapiContactGender.Male)

        contact5.setProfessionalInfo(MapiContactProfessionalPropertySet("Briazz", "Psychiatric aide"))

        contact5.getPhysicalAddresses().getWorkAddress().setAddress("Horner Strasse 12 4421 SAASS")

        contact5.getTelephones().setBusinessTelephoneNumber("0650 675 73 30")

        contact5.getTelephones().setHomeTelephoneNumber("(661)387-5382")

        # Contacto #6

        contact6 = MapiContact()

        contact6.setNameInfo(MapiContactNamePropertySet("Bertha", "A.", "Buell"))

        contact6.setProfessionalInfo(MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant"))

        contact6.getPersonalInfo().setPersonalHomePage("B2BTies.com")

        contact6.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT")

        contact6.getElectronicAddresses().setEmail1(MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"))

        contact6.setTelephones(MapiContactTelephonePropertySet("06605045265"))

        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        standardIpmFolder=StandardIpmFolder

        pst = personalStorage.create(dataDir + "MapiContactToPST1.pst", fileFormatVersion.Unicode)

        contactFolder = pst.createPredefinedFolder("Contactos", standardIpmFolder.Contacts)

        contactFolder.addMapiMessageItem(contact1)

        contactFolder.addMapiMessageItem(contact2)

        contactFolder.addMapiMessageItem(contact3)

        contactFolder.addMapiMessageItem(contact4)

        contactFolder.addMapiMessageItem(contact5)

        contactFolder.addMapiMessageItem(contact6)

        print "MapiContacts agregados exitosamente."

if __name__ == '__main__':        

    AddMapiContactToPST()

```
## **Descargar Código Funcionando**
Descargue **Agregando MapiContact a PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)