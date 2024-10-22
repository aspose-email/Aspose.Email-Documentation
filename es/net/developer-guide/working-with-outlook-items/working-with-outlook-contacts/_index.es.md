---
title: "Trabajando con Contactos de Outlook"
url: /es/net/working-with-outlook-contacts/
weight: 90
type: docs
---


## **Crear, Guardar y Leer Contactos**

Al igual que MapiMessage, Aspose.Email te permite crear contactos de Outlook. La clase [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) proporciona todas las propiedades relacionadas con el contacto necesarias para crear un contacto de Outlook. Este artículo muestra cómo crear, guardar y leer un contacto de Outlook utilizando la clase [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

### **Crear y Guardar un Contacto de Outlook**

Para crear un contacto y guardarlo en disco:

1. Instancia un nuevo objeto de la clase [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).
1. Ingresa la información de las propiedades del contacto.
1. Agrega datos de foto (si los hay).
1. Guarda el contacto en formato MSG o VCard.

El siguiente fragmento de código te muestra cómo crear y guardar un contacto de Outlook.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateAndSaveOutlookContact-CreateAndSaveOutlookContact.cs" >}}

### **Guardar Lista de Distribución Mapi en un Solo Archivo VCF de Múltiples Contactos**

El siguiente ejemplo de código demuestra cómo guardar una lista de distribución en un archivo VCF de múltiples contactos:

```cs
// convierte el objeto `msg` a un objeto `MapiMessage`
var dlist = (MapiDistributionList)msg.ToMapiMessageItem();

//guardar la lista de distribución
var options = new MapiDistributionListSaveOptions(ContactSaveFormat.VCard);
dlist.Save("distribution_list.vcf", options);
```

### **Guardar Contacto en Formato VCF Versión 3**

Para guardar el contacto en formato VCF versión 3, utiliza el enumerado [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) para establecer la propiedad [VCardSaveOptions.Version](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/). El siguiente código de ejemplo demuestra el uso del enumerado [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardversion/) para guardar el contacto en formato VCF versión 3:

```cs

```

### **Leer un MapiContact**

La clase [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) se puede utilizar para cargar tanto contactos de Outlook en formato MSG como VCard. El siguiente fragmento de código te muestra cómo cargar contactos de Outlook guardados como MSG y VCF en un [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/).

#### **Cargar un Contacto desde MSG**

El siguiente fragmento de código muestra cómo cargar contactos desde MSG.

#### **Cargar un Contacto desde VCard**

El siguiente fragmento de código muestra cómo cargar contactos desde VCard.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCard-LoadingContactFromVCard.cs" >}}

#### **Cargar un Contacto desde VCard con Codificación Especificada**

El siguiente fragmento de código muestra cómo cargar contactos desde VCard con la codificación especificada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.cs" >}}

#### **Guardar Elementos de Contacto VCard con Codificación Especificada**

Personaliza el comportamiento de guardado al trabajar con archivos VCard utilizando la clase [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class). La propiedad [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) de la clase especificará la codificación que se utilizará al guardar elementos de contacto VCard.

El siguiente ejemplo de código muestra cómo implementar esta propiedad en tu proyecto:

```cs
var cont = VCardContact.Load(fileName, Encoding.UTF8);
var opt = new VCardSaveOptions();
opt.PreferredTextEncoding = Encoding.UTF8;
cont.Save("my.vcard", opt);
```

#### **Guardar Archivos VCard con Campos Extendidos**

La propiedad [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/#vcardsaveoptionsuseextensions-property) te permite controlar si se pueden utilizar campos extendidos al guardar archivos vCard. Cuando se establece en verdadero (valor predeterminado), se permiten extensiones, proporcionando compatibilidad con campos personalizados y información adicional del contacto.

### **Leer Múltiples Contactos en Formato VCard**

Nuestra biblioteca hace posible obtener la lista de todos los contactos de un VCard. Esto se puede hacer utilizando los siguientes métodos y pasos:

```cs
// Verifica si la secuencia de origen del VCard contiene múltiples contactos.
VCardContact.IsMultiContacts(Stream stream)

// Carga la lista de todos los contactos desde el archivo VCard.
VCardContact.LoadAsMultiple(string filePath, Encoding encoding)

// Carga la lista de todos los contactos desde la secuencia VCard.
VCardContact.LoadAsMultiple(Stream stream, Encoding encoding)
```
El siguiente fragmento de código demuestra cómo manejar archivos VCard que contienen múltiples contactos:

```cs
using (FileStream stream = new FileStream("test.vcf", FileMode.Open, FileAccess.Read))
{
    if(VCardContact.IsMultiContacts(stream))
    {
        List<VCardContact> contacts = VCardContact.LoadAsMultiple(stream, Encoding.UTF8);
    }
}
```

## **Renderizar Información del Contacto en MHTML**

El contacto de Outlook se puede convertir a MHTML utilizando la API de Aspose.Email. Este ejemplo muestra cómo se carga un VCard en [MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/) y luego se convierte a MHTML con la ayuda de la API de [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.cs" >}}