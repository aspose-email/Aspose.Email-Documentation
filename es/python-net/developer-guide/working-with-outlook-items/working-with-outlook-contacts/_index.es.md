---
title: "Trabajar con contactos de Outlook"
url: /es/python-net/working-with-outlook-contacts/
weight: 90
type: docs
---


## **Crear, guardar y leer contactos**
Al igual que MapiMessage, Aspose.Email te permite crear contactos de Outlook. La clase MapiContact proporciona todas las propiedades relacionadas con los contactos necesarias para crear un contacto de Outlook. En este artículo se muestra cómo crear, guardar y leer un contacto de Outlook mediante la clase MapiContact.
### **Crear y guardar contactos de Outlook**
Para crear un contacto y guardarlo en un disco:

1. Cree una instancia de un objeto nuevo de la clase MapiContact.
1. Introduzca la información de contacto de la propiedad.
1. Agregue datos fotográficos (si los hay).
1. Guarda el contacto en formato MSG o vCard.

El siguiente fragmento de código muestra cómo crear y guardar contactos de Outlook.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
contact.professional_info = ae.mapi.MapiContactProfessionalPropertySet("Awthentikz", "Social work assistant")
contact.personal_info.personal_home_page = "B2BTies.com"
contact.physical_addresses.work_address.address = "Im Astenfeld 59 8580 EDELSCHROTT"
contact.electronic_addresses.email1 = ae.mapi.MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com")
contact.telephones = ae.mapi.MapiContactTelephonePropertySet("06605045265")
contact.personal_info.children = ["child1", "child2", "child3"]
contact.categories = ["category1", "category2", "category3"]
contact.mileage = "Some test mileage"
contact.billing = "Test billing information"
contact.other_fields.journal = True
contact.other_fields.private = True
contact.other_fields.reminder_topic = "Test topic"
contact.other_fields.user_field1 = "ContactUserField1"
contact.other_fields.user_field2 = "ContactUserField2"
contact.other_fields.user_field3 = "ContactUserField3"
contact.other_fields.user_field4 = "ContactUserField4"

# Add a photo
with open(data_dir + "Desert.jpg", "rb") as file:
    buffer = file.read()
    contact.photo = ae.mapi.MapiContactPhoto(buffer, ae.mapi.MapiContactPhotoImageFormat.Jpeg)

# Save the Contact in MSG format
contact.save(data_dir + "MapiContact_out.msg", ae.mapi.ContactSaveFormat.MSG)

# Save the Contact in VCF format
contact.save(data_dir + "MapiContact_out.vcf", ae.mapi.ContactSaveFormat.V_CARD)
```

### **Guardar contacto en formato VCF, versión 3**

Para guardar un contacto en la versión 3 del formato VCF, utilice el *version* propiedad del [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) clase. Cree una nueva instancia de la clase vCardSaveOptions y establezca la propiedad de versión del objeto vCardSaveOptions en vCardVersion.v30. Esto establece la versión de vCard en 3.0., llame al *save* método del objeto MAPIContact, pasando el nombre de archivo «contact.vcf» y el objeto vCardSaveOptions como parámetros. Esto guarda el contacto como un archivo vCard con el nombre de archivo y las opciones especificadas. El siguiente fragmento de código muestra cómo guardar un contacto en la versión 3 del formato VCF:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.version = ae.personalinfo.vcard.VCardVersion.V30
contact.save("contact.vcf", options)
```

### **Lectura de un MapiContact**
La clase MapiContact se puede usar para cargar contactos en formato MSG y vCard de Outlook. El siguiente fragmento de código muestra cómo cargar los contactos de Outlook guardados como MSG y VCF en un MapiContact.
#### **Cargar un contacto desde MSG**
El siguiente fragmento de código muestra cómo cargar un contacto desde MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
#### **Cargar un contacto desde vCard**
El siguiente fragmento de código muestra cómo cargar un contacto desde vCard.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCF-LoadingContactFromVCF.py" >}}
#### **Carga de un contacto desde vCard con codificación especificada**
El siguiente fragmento de código muestra cómo cargar un contacto desde vcard con la codificación especificada.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.py" >}}

#### **Guardar elementos de contacto de vCard con una codificación especificada**

Al guardar un archivo vCard, es posible especificar la codificación de caracteres que se utilizará para garantizar la compatibilidad con caracteres que no sean ASCII. Configure el *preferred_text_encoding* propiedad del objeto vCardSaveOptions para «utf-8\". El siguiente fragmento de código muestra cómo implementar esta función en tu proyecto:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.preferred_text_encoding = "utf-8"
contact.save("contact.vcf", options)
```

#### **Guardar archivos vCard con campos extendidos**

Al guardar un archivo vCard, también puede especificar opciones, incluido el uso de campos extendidos, es decir, propiedades o atributos adicionales que se pueden agregar a una vCard más allá del conjunto estándar de campos definido por la especificación vCard. El *use_extensions* propiedad del [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) la clase te permite hacerlo. El siguiente fragmento de código muestra cómo guardar un archivo vCard con campos extendidos:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)
```
#### **Lectura de varios contactos en formato vCard**

Necesitará los siguientes métodos para obtener la lista de todos los contactos de una vCard:

```
# Checks whether VCard source stream contains multiple contacts.
aspose.email.personalinfo.vcard.VCardContact.is_multi_contacts(stream)

# Loads list of all contacts from VCard file.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(file_path, encoding)

# Loads list of all contacts from VCard stream.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(stream, encoding)
```
El siguiente fragmento de código mostrará el proceso de lectura de varios contactos de un archivo vCard:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)

if ae.personalinfo.vcard.VCardContact.is_multi_contacts("contact.vcf"):
    ae.personalinfo.vcard.VCardContact.load_as_multiple("contact.vcf")
```

## **Representación de la información de contacto en MHTML**
Outlook Contact se puede convertir a MHTML mediante la API Aspose.Email. Este ejemplo muestra cómo se carga una vCard en MapiContact y, a continuación, se convierte a MHTML con la ayuda de la API MailMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.py" >}}
