---
title: "Trabajar con contactos de Outlook"
url: /es/net/working-with-outlook-contacts/
weight: 90
type: docs
---


## **Crear, guardar y leer contactos**

Al igual que MapiMessage, Aspose.Email te permite crear contactos de Outlook. El [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) La clase proporciona todas las propiedades relacionadas con los contactos necesarias para crear un contacto de Outlook. En este artículo se muestra cómo crear, guardar y leer un contacto de Outlook mediante [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.

### **Crear y guardar contactos de Outlook**

Para crear un contacto y guardarlo en un disco:

1. Crea una instancia de un nuevo objeto del [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) class.
1. Introduzca la información de contacto de la propiedad.
1. Agregue datos fotográficos (si los hay).
1. Guarda el contacto en formato MSG o vCard.

El siguiente fragmento de código muestra cómo crear y guardar contactos de Outlook.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cs" >}}

### **Guarde la lista de distribución de Mapi en un único archivo VCF de múltiples contactos**

El ejemplo de código que aparece a continuación muestra cómo guardar una lista de distribución en un archivo VCF con varios contactos:

```cs
// convert the `msg` object to a `MapiMessage` object
var dlist = (MapiDistributionList)msg.ToMapiMessageItem();

//save the distribution list
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.Save("distribution_list.vcf", options);
```


### **Guardar contacto en formato VCF de la versión 3**

Para guardar el contacto en el formato VCF de la versión 3, utilice [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) enumerable para establecer el [VCardSaveOptions.Version](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) propiedad. El siguiente código de ejemplo demuestra el uso de [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) enumerable para guardar el formato VCF versión 3 del contacto:

```cs

```

### **Lectura de un MapiContact**

The [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) la clase se puede usar para cargar contactos en formato MSG y vCard de Outlook. El siguiente fragmento de código muestra cómo cargar los contactos de Outlook guardados como MSG y VCF en un [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

#### **Cargar un contacto desde MSG**

El siguiente fragmento de código muestra cómo cargar contactos desde MSG.

#### **Cargar un contacto desde vCard**

El siguiente fragmento de código muestra cómo cargar contactos desde vCard.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cs" >}}

#### **Carga de un contacto desde vCard con codificación especificada**

El siguiente fragmento de código muestra cómo cargar contactos desde vCard con la codificación especificada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.cs" >}}

#### **Guardar elementos de contacto de vCard con una codificación especificada**

Personalice el comportamiento de guardado cuando trabaje con archivos vCard mediante [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) clase. El [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) La propiedad de la clase especificará la codificación que se utilizará al guardar los elementos de contacto de vCard.

El siguiente ejemplo de código muestra cómo implementar esta propiedad en su proyecto:

```cs
var cont = VCardContact.Load(fileName, Encoding.UTF8);
var opt = new VCardSaveOptions();
opt.PreferredTextEncoding = Encoding.UTF8;
cont.Save("my.vcard", opt);
```

#### **Guardar archivos vCard con campos extendidos**

The [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/#vcardsaveoptionsuseextensions-property) La propiedad le permite controlar si los campos extendidos se pueden usar al guardar archivos vCard. Si se establece en verdadero (valor predeterminado), se permiten las extensiones, lo que proporciona compatibilidad con campos personalizados e información de contacto adicional.

### **Lectura de varios contactos en formato vCard**

Nuestra biblioteca permite obtener la lista de todos los contactos desde una vCard. Puede hacerlo siguiendo los siguientes métodos y pasos:

```cs
// Checks whether VCard source stream contains multiple contacts.
VCardContact.IsMultiContacts(Stream stream)

// Loads list of all contacts from VCard file.
VCardContact.LoadAsMultiple(string filePath, Encoding encoding)

// Loads list of all contacts from VCard stream.
VCardContact.LoadAsMultiple(Stream stream, Encoding encoding)
```
El siguiente fragmento de código muestra cómo gestionar los archivos vCard que contienen varios contactos:

```cs
using (FileStream stream = new FileStream("test.vcf", FileMode.Open, FileAccess.Read))
{
    if(VCardContact.IsMultiContacts(stream))
    {
        List<VCardContact> contacts = VCardContact.LoadAsMultiple(stream, Encoding.UTF8);
    }
}
```

## **Representación de la información de contacto en MHTML**

Outlook Contact se puede convertir a MHTML mediante la API Aspose.Email. Este ejemplo muestra cómo se carga una vCard en [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) y luego se convirtió a MHTML con la ayuda de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) API.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.cs" >}}
