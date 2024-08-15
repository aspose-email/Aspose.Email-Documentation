---
title: "Работа с контактами в файле PST"
url: /ru/net/working-with-contacts-in-pst-file/
weight: 40
type: docs
---


## **Добавление контакта в PST**

Статья [Создайте новый файл PST и добавьте подпапки](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) показывает, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить MapiContact в подпапку «Контакты» созданного или загруженного файла PST. Ниже приведены шаги по добавлению MapiContact в PST:

1. Создайте [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) object.
2. Установите [Свойства контакта MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) используя разные конструкторы и методы.
3. Создайте PST, используя [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Создайте предварительно определенную папку (Контакты) в корне файла PST, открыв корневую папку и вызвав [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

В следующем фрагменте кода показано, как создать MapiContact, а затем добавить его в папку контактов вновь созданного файла PST.

```csharp
// Create three Contacts
var contact1 = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");
var contact2 = new MapiContact("Wichert Kroos", "WichertKroos@teleworm.us", "Grade A Investment");
var contact3 = new MapiContact("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Krauses Sofa Factory", "046-630-4614046-630-4614");

// Contact #4
var contact4 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Margaret", "J.", "Tolle")};
contact4.PersonalInfo.Gender = MapiContactGender.Female;
contact4.ProfessionalInfo = new MapiContactProfessionalPropertySet("Adaptaz", "Recording engineer");
contact4.PhysicalAddresses.WorkAddress.Address = "4 Darwinia Loop EIGHTY MILE BEACH WA 6725";
contact4.ElectronicAddresses.Email1 = new MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com");
contact4.Telephones.BusinessTelephoneNumber = "(08)9080-1183";
contact4.Telephones.MobileTelephoneNumber = "(925)599-3355(925)599-3355";

// Contact #5
var contact5 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Matthew", "R.", "Wilcox")};
contact5.PersonalInfo.Gender = MapiContactGender.Male;
contact5.ProfessionalInfo = new MapiContactProfessionalPropertySet("Briazz", "Psychiatric aide");
contact5.PhysicalAddresses.WorkAddress.Address = "Horner Strasse 12 4421 SAASS";
contact5.Telephones.BusinessTelephoneNumber = "0650 675 73 300650 675 73 30";
contact5.Telephones.HomeTelephoneNumber = "(661)387-5382(661)387-5382";

// Contact #6
var contact6 = new MapiContact
{
    NameInfo = new MapiContactNamePropertySet("Bertha", "A.", "Buell"),
    ProfessionalInfo = new MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant")
};
contact6.PersonalInfo.PersonalHomePage = "B2BTies.com";
contact6.PhysicalAddresses.WorkAddress.Address = "Im Astenfeld 59 8580 EDELSCHROTT";
contact6.ElectronicAddresses.Email1 = new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com");
contact6.Telephones = new MapiContactTelephonePropertySet("06605045265");

using (PersonalStorage personalStorage = PersonalStorage.Create("SampleContacts_out.pst", FileFormatVersion.Unicode))
{
    var contactFolder = personalStorage.CreatePredefinedFolder("Contacts", StandardIpmFolder.Contacts);
    contactFolder.AddMapiMessageItem(contact1);
    contactFolder.AddMapiMessageItem(contact2);
    contactFolder.AddMapiMessageItem(contact3);
    contactFolder.AddMapiMessageItem(contact4);
    contactFolder.AddMapiMessageItem(contact5);
    contactFolder.AddMapiMessageItem(contact6);
}
```

## **Сохраните информацию о контактах из файла PST в формате MSG**

В этой статье описывается, как получить доступ к контактной информации из файла Outlook PST и сохранить контакт на диске в формате MSG. Чтобы получить контактную информацию, выполните следующие действия:

1. Загрузите файл PST в [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) object.
1. Перейдите в папку «Контакты».
1. Получайте содержимое папки «Контакты» с помощью Loop по сообщениям.
1. Убедитесь, что [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) значение свойства соответствует значению «IPM.contact».
1. Позвоните [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) метод получения [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object.
1. Вызовите метод MapiMessage.save (), чтобы сохранить контакт на диске в формате MSG.

В следующем фрагменте кода показано, как извлечь всю контактную информацию из файла PST и сохранить ее на диск в формате MSG.

```csharp
// Load the Outlook PST file
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Get the Contacts folder
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Loop through all the contacts in this folder
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Get the contact information
        var msg = pst.ExtractMessage(messageInfo);
       
        // Save to disk in msg format
        string contactName = msg.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        msg.Save($"{contactName}.msg", SaveOptions.DefaultMsgUnicode);
    }
}
```

## **Сохранить информацию о контактах из файла PST в формате VCF**

В этой статье показано, как получить доступ к контактной информации из файла Microsoft Outlook PST и сохранить контакт на диск в формате vCard (VCF). Используйте [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) классы для получения контактной информации из файла PST. Чтобы получить контактную информацию, выполните следующие действия:

1. Загрузите файл PST в [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class.
1. Перейдите в папку «Контакты».
1. Получайте содержимое папки «Контакты» с помощью Loop по сообщениям.
1. Убедитесь, что [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) значение свойства соответствует значению «IPM.contact».
1. Позвоните [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) метод получения [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object.
1. Позвоните [MapiMessage.ToMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomapimessageitem/) и бросьте [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/) to [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) type.
1. Позвоните [MapiContact.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_1) метод сохранения контакта на диск в формате vCard.

Приведенная ниже программа загружает файл PST с диска и сохраняет все контакты в формате vCard (VCF). Затем файлы VCF можно использовать в любой другой программе, которая может загрузить стандартный файл контактов vCard. Если вы откроете какой-либо файл VCF в Microsoft Outlook, он будет выглядеть так, как показано на скриншоте ниже.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
|: - |
В следующем фрагменте кода показано, как экспортировать контакты из Outlook PST в формат vCard (VCF).

```csharp
// Load the Outlook PST file
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Get the Contacts folder
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Loop through all the contacts in this folder
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Get the contact information
        var msg = pst.ExtractMessage(messageInfo);
        var contact = (MapiContact)msg.ToMapiMessageItem();

        // Display some contents on screen
        Console.WriteLine("Name: " + contact.NameInfo.DisplayName);

        // Save to disk in VCard format
        string contactName = contact.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        contact.Save($"{contactName}.vcf", ContactSaveFormat.VCard);
    }
}
```

См. также: [Работа со списками рассылки](/email//net/working-with-distribution-lists-in-pst/)
