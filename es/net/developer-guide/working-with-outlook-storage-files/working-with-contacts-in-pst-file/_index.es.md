---
title: "Trabajando con Contactos en Archivos PST"
url: /es/net/working-with-contacts-in-pst-file/
weight: 40
type: docs
---


## **Agregar Contacto a PST**

El artículo [Crear un nuevo archivo PST y agregar subcarpetas](https://docs.aspose.com/email/es/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) muestra cómo crear un archivo PST y agregarle una subcarpeta. Con Aspose.Email, puedes agregar un MapiContact a la subcarpeta de Contactos de un archivo PST que has creado o cargado. A continuación se presentan los pasos para agregar un MapiContact a un PST:

1. Crear un objeto [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
2. Establecer las [propiedades de MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) utilizando diferentes constructores y métodos.
3. Crear un PST utilizando el método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crear una carpeta predefinida (Contactos) en la raíz del archivo PST accediendo a la carpeta raíz y luego llamando al método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

El siguiente fragmento de código muestra cómo crear un MapiContact y luego agregarlo a la carpeta de contactos de un archivo PST recién creado.

```csharp
// Crear tres Contactos 
var contact1 = new MapiContact("Sebastian Wright", "SebastianWright@dayrep.com");
var contact2 = new MapiContact("Wichert Kroos", "WichertKroos@teleworm.us", "Grade A Investment");
var contact3 = new MapiContact("Christoffer van de Meeberg", "ChristoffervandeMeeberg@teleworm.us", "Krauses Sofa Factory", "046-630-4614046-630-4614");

// Contacto #4
var contact4 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Margaret", "J.", "Tolle")};
contact4.PersonalInfo.Gender = MapiContactGender.Female;
contact4.ProfessionalInfo = new MapiContactProfessionalPropertySet("Adaptaz", "Recording engineer");
contact4.PhysicalAddresses.WorkAddress.Address = "4 Darwinia Loop EIGHTY MILE BEACH WA 6725";
contact4.ElectronicAddresses.Email1 = new MapiContactElectronicAddress("Hisen1988", "SMTP", "MargaretJTolle@dayrep.com");
contact4.Telephones.BusinessTelephoneNumber = "(08)9080-1183";
contact4.Telephones.MobileTelephoneNumber = "(925)599-3355(925)599-3355";

// Contacto #5
var contact5 = new MapiContact{NameInfo = new MapiContactNamePropertySet("Matthew", "R.", "Wilcox")};
contact5.PersonalInfo.Gender = MapiContactGender.Male;
contact5.ProfessionalInfo = new MapiContactProfessionalPropertySet("Briazz", "Psychiatric aide");
contact5.PhysicalAddresses.WorkAddress.Address = "Horner Strasse 12 4421 SAASS";
contact5.Telephones.BusinessTelephoneNumber = "0650 675 73 300650 675 73 30";
contact5.Telephones.HomeTelephoneNumber = "(661)387-5382(661)387-5382";

// Contacto #6
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

## **Guardar información de contactos del archivo PST en formato MSG**

Este artículo explica cómo acceder a la información de contactos de un archivo PST de Outlook y guardar el contacto en un disco en formato MSG. Los pasos para obtener la información del contacto son:

1. Cargar el archivo PST en el objeto [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Examinar la carpeta de Contactos.
1. Obtener el contenido de la carpeta de Contactos mediante un bucle a través de los mensajes.
1. Verificar que el valor de la propiedad [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) coincida con "IPM.Contact".
1. Llamar al método [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) para obtener el objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
1. Llamar al método MapiMessage.Save() para guardar el contacto en el disco en formato MSG.

El siguiente fragmento de código muestra cómo recuperar toda la información de contacto del archivo PST y guardar en el disco en formato MSG.

```csharp
// Cargar el archivo PST de Outlook
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Obtener la carpeta de Contactos
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Recorrer todos los contactos en esta carpeta
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Obtener la información del contacto
        var msg = pst.ExtractMessage(messageInfo);
        
        // Guardar en disco en formato msg
        string contactName = msg.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        msg.Save($"{contactName}.msg", SaveOptions.DefaultMsgUnicode);
    }
}
```

## **Guardar información de contactos del archivo PST en formato VCF**

Este artículo muestra cómo acceder a la información de contacto de un archivo PST de Microsoft Outlook y guardar el contacto en el disco en formato vCard (VCF). Utilice las clases [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) y [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) para obtener información de contacto del archivo PST. Para obtener la información de contacto:

1. Cargar el archivo PST en la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Examinar la carpeta de Contactos.
1. Obtener el contenido de la carpeta de Contactos mediante un bucle a través de los mensajes.
1. Verificar que el valor de la propiedad [MessageInfo.MessageClass](https://reference.aspose.com/email/net/aspose.email.storage.pst/messageinfo/messageclass/) coincida con "IPM.Contact".
1. Llamar al método [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) para obtener el objeto [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/).
1. Llamar al método [MapiMessage.ToMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomapimessageitem/) y lanzar el [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/) al tipo [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Llamar al método [MapiContact.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_1) para guardar el contacto en el disco en formato VCard.

El programa a continuación carga un archivo PST desde el disco y guarda todos los contactos en formato vCard (VCF). Los archivos VCF se pueden usar en cualquier otro programa que pueda cargar el archivo de contacto estándar vCard. Si abres cualquier archivo VCF en Microsoft Outlook, se verá como el de la captura de pantalla a continuación.

|![todo:image_alt_text](working-with-contacts-in-pst-file_1.png)|
| :- |
El siguiente fragmento de código muestra cómo exportar contactos de Outlook PST a formato vCard (VCF).

```csharp
// Cargar el archivo PST de Outlook
var pst = PersonalStorage.FromFile("SampleContacts.pst");

// Obtener la carpeta de Contactos
var contactsFolder = pst.RootFolder.GetSubFolder("Contacts");

// Recorrer todos los contactos en esta carpeta
foreach (MessageInfo messageInfo in contactsFolder.EnumerateMessages())
{
    if (messageInfo.MessageClass == "IPM.Contact")
    {
        // Obtener la información del contacto
        var msg = pst.ExtractMessage(messageInfo);
        var contact = (MapiContact)msg.ToMapiMessageItem();

        // Mostrar algunos contenidos en pantalla
        Console.WriteLine("Nombre: " + contact.NameInfo.DisplayName);

        // Guardar en disco en formato VCard
        string contactName = contact.Subject.Replace(":", " ").Replace("\\", " ").Replace("?", " ").Replace("/", " ");
        contact.Save($"{contactName}.vcf", ContactSaveFormat.VCard);
    }
}
```

Ver también: [Trabajando con Listas de Distribución](/email//net/working-with-distribution-lists-in-pst/)