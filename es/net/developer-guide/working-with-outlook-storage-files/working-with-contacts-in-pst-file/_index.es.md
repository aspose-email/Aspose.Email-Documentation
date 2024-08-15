---
title: "Trabajar con contactos en un archivo PST"
url: /es/net/working-with-contacts-in-pst-file/
weight: 40
type: docs
---


## **Agregar un contacto a PST**

El artículo [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email puede agregar un MapiContact a la subcarpeta Contactos de un archivo PST que haya creado o cargado. A continuación se detallan los pasos para agregar MapiContact a un PST:

1. Crea un [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) object.
2. Configure el [Propiedades de MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) utilizando diferentes constructores y métodos.
3. Cree un PST con el [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Cree una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

El siguiente fragmento de código muestra cómo crear un MapiContact y, a continuación, añadirlo a la carpeta de contactos de un archivo PST recién creado.

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

## **Guarde la información de contactos del archivo PST en formato MSG**

En este artículo se explica cómo acceder a la información de contacto desde un archivo PST de Outlook y guardar el contacto en un disco en formato MSG. Los pasos para obtener la información de contacto son los siguientes:

1. Cargue el archivo PST en [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) object.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos recorriendo los mensajes.
1. Compruebe que el [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) el valor de la propiedad coincide con «IPM.Contact».
1. Llame al [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) método para obtener el [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object.
1. Llame al método mapiMessage.save () para guardar el contacto en el disco en formato MSG.

El siguiente fragmento de código muestra cómo recuperar toda la información de contacto del archivo PST y guardarla en el disco en formato MSG.

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

## **Guarde la información de contactos del archivo PST en formato VCF**

Este artículo muestra cómo acceder a la información de contacto desde un archivo PST de Microsoft Outlook y guardar el contacto en un disco en formato vCard (VCF). Utilice el [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) clases para obtener información de contacto del archivo PST. Para obtener la información de contacto:

1. Cargue el archivo PST en [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class.
1. Navega por la carpeta Contactos.
1. Obtenga el contenido de la carpeta Contactos recorriendo los mensajes.
1. Compruebe que el [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) el valor de la propiedad coincide con «IPM.Contact».
1. Llame al [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) método para obtener el [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) object.
1. Llame al [MapiMessage.ToMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomapimessageitem/) y lanza el [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/) to [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) type.
1. Llame al [MapiContact.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_1) método para guardar el contacto en el disco en formato vCard.

El siguiente programa carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF se pueden usar entonces en cualquier otro programa que pueda cargar el archivo de contactos vCard estándar. Si abres cualquier archivo VCF en Microsoft Outlook, tendrá el mismo aspecto que el de la siguiente captura de pantalla.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
|: - |
El siguiente fragmento de código muestra cómo exportar contactos del formato PST de Outlook al formato vCard (VCF).

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

Véase también: [Trabajando con listas de distribución](/email//net/working-with-distribution-lists-in-pst/)
