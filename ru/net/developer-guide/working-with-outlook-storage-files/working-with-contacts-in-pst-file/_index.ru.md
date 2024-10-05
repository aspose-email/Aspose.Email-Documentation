---
title: "Работа с контактами в файле PST"
url: /ru/net/working-with-contacts-in-pst-file/
weight: 40
type: docs
---


## **Добавление контакта в PST**

Статья [Создание нового PST файла и добавление подпапок](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) показывает, как создать PST файл и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiContact в подпапку Контакты PST файла, который вы создали или загрузили. Ниже приведены шаги для добавления MapiContact в PST:

1. Создайте объект [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
2. Установите [свойства MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) с помощью различных конструкторов и методов.
3. Создайте PST с помощью метода [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Создайте предопределенную папку (Контакты) в корне файла PST, обратившись к корневой папке и затем вызвав метод [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

Следующий фрагмент кода показывает, как создать MapiContact и затем добавить его в папку контактов нового PST файла.

```csharp
// Создайте три контакта 
var contact1 = new MapiContact("Себастьян Урайт", "SebastianWright@dayrep.com");
var contact2 = new MapiContact("Вихерт Кроос", "WichertKroos@teleworm.us", "Инвестиции класса A");
var contact3 = new MapiContact("Кристоффер ван де Миберг", "ChristoffervandeMeeberg@teleworm.us", "Фабрика диванов Краузес", "046-630-4614046-630-4614");

// Контакт #4
var contact4 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Маргарет", "J.", "Толле")};
contact4.PersonalInfo.Gender = MapiContactGender.Female;
contact4.ProfessionalInfo = new MapiContactProfessionalPropertySet("Адаптаз", "Звукорежиссёр");
contact4.PhysicalAddresses.WorkAddress.Address = "4 Дурвиния Луп EIGHTY MILE BEACH WA 6725";
contact4.ElectronicAddresses.Email1 = new MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com");
contact4.Telephones.BusinessTelephoneNumber = "(08)9080-1183";
contact4.Telephones.MobileTelephoneNumber = "(925)599-3355(925)599-3355";

// Контакт #5
var contact5 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Мэтью", "R.", "Уилкокс")};
contact5.PersonalInfo.Gender = MapiContactGender.Male;
contact5.ProfessionalInfo = new MapiContactProfessionalPropertySet("Бриазз", "Психиатрический помощник");
contact5.PhysicalAddresses.WorkAddress.Address = "Хорнер Штрассе 12 4421 SAASS";
contact5.Telephones.BusinessTelephoneNumber = "0650 675 73 300650 675 73 30";
contact5.Telephones.HomeTelephoneNumber = "(661)387-5382(661)387-5382";

// Контакт #6
var contact6 = new MapiContact
{
    NameInfo = new MapiContactNamePropertySet("Берта", "A.", "Бюэлл"),
    ProfessionalInfo = new MapiContactProfessionalPropertySet("Awthentikz", "Помощник социального работника")
};
contact6.PersonalInfo.PersonalHomePage = "B2BTies.com";
contact6.PhysicalAddresses.WorkAddress.Address = "Im Astenfeld 59 8580 EDELSCHROTT";
contact6.ElectronicAddresses.Email1 = new MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com");
contact6.Telephones = new MapiContactTelephonePropertySet("06605045265");

using (PersonalStorage personalStorage = PersonalStorage.Create("SampleContacts_out.pst", FileFormatVersion.Unicode))
{
    var contactFolder = personalStorage.CreatePredefinedFolder("Контакты", StandardIpmFolder.Contacts);
    contactFolder.AddMapiMessageItem(contact1);
    contactFolder.AddMapiMessageItem(contact2);
    contactFolder.AddMapiMessageItem(contact3);
    contactFolder.AddMapiMessageItem(contact4);
    contactFolder.AddMapiMessageItem(contact5);
    contactFolder.AddMapiMessageItem(contact6);
}
```

## **Сохранение информации о контактах из PST файла в формате MSG**

В этой статье объясняется, как получить информацию о контактах из файла Outlook PST и сохранить контакт на диск в формате MSG. Шаги для получения информации о контакте следующие:

1. Загрузите файл PST в объекте [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Просмотрите папку Контактов.
1. Получите содержимое папки Контактов, пройдя по сообщениям.
1. Убедитесь, что значение свойства [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) соответствует "IPM.Contact".
1. Вызовите метод [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) для получения объекта [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
1. Вызовите метод MapiMessage.Save() для сохранения контакта на диск в формате MSG.

Следующий фрагмент кода показывает, как извлечь всю информацию о контактах из файла PST и сохранить на диск в формате MSG.

```csharp
// Загрузите файл Outlook PST
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Получите папку Контактов
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Пройдите по всем контактам в этой папке
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Получите информацию о контакте
        var msg = pst.ExtractMessage(messageInfo);
        
        // Сохраните на диск в формате msg
        string contactName = msg.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        msg.Save($"{contactName}.msg", SaveOptions.DefaultMsgUnicode);
    }
}
```

## **Сохранение информации о контактах из PST файла в формате VCF**

Эта статья показывает, как получить информацию о контактах из файла Microsoft Outlook PST и сохранить контакт на диск в формате vCard (VCF). Используйте классы [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) и [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/), чтобы получить информацию о контактах из файла PST. Для получения информации о контакте:

1. Загрузите файл PST в классе [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Просмотрите папку Контактов.
1. Получите содержимое папки Контактов, пройдя по сообщениям.
1. Убедитесь, что значение свойства [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) соответствует "IPM.Contact".
1. Вызовите метод [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) для получения объекта [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
1. Вызовите метод [MapiMessage.ToMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomapimessageitem/) и приведите [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/) к типу [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Вызовите метод [MapiContact.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_1), чтобы сохранить контакт на диск в формате VCard.

Программа ниже загружает файл PST с диска и сохраняет все контакты в формате vCard (VCF). Файлы VCF затем можно использовать в любой другой программе, которая может загрузить стандартный файл контакта vCard. Если открыть любой файл VCF в Microsoft Outlook, он будет выглядеть как в ниже приведенном скриншоте.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
Следующий фрагмент кода показывает, как экспортировать контакты из Outlook PST в формат vCard (VCF).

```csharp
// Загрузите файл Outlook PST
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Получите папку Контактов
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Пройдите по всем контактам в этой папке
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Получите информацию о контакте
        var msg = pst.ExtractMessage(messageInfo);
        var contact = (MapiContact)msg.ToMapiMessageItem();

        // Отобразите некоторые содержимое на экране
        Console.WriteLine("Имя: " + contact.NameInfo.DisplayName);

        // Сохраните на диск в формате VCard
        string contactName = contact.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        contact.Save($"{contactName}.vcf", ContactSaveFormat.VCard);
    }
}
```

См. также: [Работа с Распределительными Списками](/email//net/working-with-distribution-lists-in-pst/)