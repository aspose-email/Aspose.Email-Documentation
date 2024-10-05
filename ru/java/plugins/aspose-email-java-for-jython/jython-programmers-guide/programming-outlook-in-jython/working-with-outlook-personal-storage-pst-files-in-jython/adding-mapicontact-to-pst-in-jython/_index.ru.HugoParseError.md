---
title: Добавление MapiContact в PST в Jython
type: docs
weight: 30
url: /java/adding-mapicontact-to-pst-in-jython/
---

## **Aspose.Email - Добавление MapiContact в PST**
Для добавления MapiContact в PST с использованием **Aspose.Email Java для Jython** просто вызовите модуль **AddMapiContactToPST**. Здесь вы можете увидеть пример кода.

**Код Jython**

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



        # Создание экземпляра MapiContact

        mapi_contact = MapiContact()

        # Контакт #1

        contact1 = MapiContact("Себастьян Райт", "SebastianWright@dayrep.com")

        # Контакт #2

        contact2 = MapiContact("Вихерт Кроос", "WichertKroos@teleworm.us", "Инвестиции класса A")

        # Контакт #3

        contact3 = MapiContact("Кристофер ван де Мееберг", "ChristoffervandeMeeberg@teleworm.us", "Фабрика диванов Краус")
        # "046-630-4614"

        # Контакт #4

        contact4 = MapiContact()

        contact4.setNameInfo(MapiContactNamePropertySet("Маргарет", "Д.", "Толле"))

        mapiContactGender=MapiContactGender

        contact4.getPersonalInfo().setGender(mapiContactGender.Female)

        contact4.setProfessionalInfo(MapiContactProfessionalPropertySet("Адаптаз", "Звукорежиссер"))

        contact4.getPhysicalAddresses().getWorkAddress().setAddress("4 Darwinia Loop EIGHTY MILE BEACH WA 6725")

        contact4.getElectronicAddresses().setEmail1(MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com"))

        contact4.getTelephones().setBusinessTelephoneNumber("(08)9080-1183")

        contact4.getTelephones().setMobileTelephoneNumber("(925)599-3355")

        # Контакт #5

        contact5 = MapiContact()

        contact5.setNameInfo(MapiContactNamePropertySet("Мэттью", "Р.", "Уилкокс"))

        contact5.getPersonalInfo().setGender(mapiContactGender.Male)

        contact5.setProfessionalInfo(MapiContactProfessionalPropertySet("Бриазз", "Помощник психиатра"))

        contact5.getPhysicalAddresses().getWorkAddress().setAddress("Horner Strasse 12 4421 SAASS")

        contact5.getTelephones().setBusinessTelephoneNumber("0650 675 73 30")

        contact5.getTelephones().setHomeTelephoneNumber("(661)387-5382")

        # Контакт #6

        contact6 = MapiContact()

        contact6.setNameInfo(MapiContactNamePropertySet("Берта", "А.", "Бьюэлл"))

        contact6.setProfessionalInfo(MapiContactProfessionalPropertySet("Awthentikz", "Помощник социального работника"))

        contact6.getPersonalInfo().setPersonalHomePage("B2BTies.com")

        contact6.getPhysicalAddresses().getWorkAddress().setAddress("Im Astenfeld 59 8580 EDELSCHROTT")

        contact6.getElectronicAddresses().setEmail1(MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com"))

        contact6.setTelephones(MapiContactTelephonePropertySet("06605045265"))

        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        standardIpmFolder=StandardIpmFolder

        pst = personalStorage.create(dataDir + "MapiContactToPST1.pst", fileFormatVersion.Unicode)

        contactFolder = pst.createPredefinedFolder("Контакты", standardIpmFolder.Contacts)

        contactFolder.addMapiMessageItem(contact1)

        contactFolder.addMapiMessageItem(contact2)

        contactFolder.addMapiMessageItem(contact3)

        contactFolder.addMapiMessageItem(contact4)

        contactFolder.addMapiMessageItem(contact5)

        contactFolder.addMapiMessageItem(contact6)

        print "МapiКонтакты успешно добавлены."





if __name__ == '__main__':        

    AddMapiContactToPST()

```
## **Скачать работающий код**
Скачать **Добавление MapiContact в PST (Aspose.Email)** из любого из нижеупомянутых сайтов социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)