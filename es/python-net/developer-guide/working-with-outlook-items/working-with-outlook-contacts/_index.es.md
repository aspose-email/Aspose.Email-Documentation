---
title: "Trabajando con Contactos de Outlook"
url: /es/python-net/working-with-outlook-contacts/
weight: 90
type: docs
---

## **Crear, Guardar y Leer Contactos**
Al igual que MapiMessage, Aspose.Email te permite crear contactos de Outlook. La clase MapiContact proporciona todas las propiedades relacionadas con los contactos necesarias para crear un contacto de Outlook. Este artículo muestra cómo crear, guardar y leer un contacto de Outlook utilizando la clase MapiContact.
### **Crear y Guardar Contacto de Outlook**
Para crear un contacto y guardarlo en disco:

1. Instancia un nuevo objeto de la clase MapiContact.
1. Ingresa la información de las propiedades del contacto.
1. Agrega datos de foto (si los hay).
1. Guarda el contacto como formato MSG o VCard.

El siguiente fragmento de código te muestra cómo crear y guardar un contacto de Outlook.

```py
import aspose.email as ae

data_dir = "path/to/data/directory"

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
contact.professional_info = ae.mapi.MapiContactProfessionalPropertySet("Awthentikz", "Asistente de trabajo social")
contact.personal_info.personal_home_page = "B2BTies.com"
contact.physical_addresses.work_address.address = "Im Astenfeld 59 8580 EDELSCHROTT"
contact.electronic_addresses.email1 = ae.mapi.MapiContactElectronicAddress("Experwas", "SMTP", "BerthaABuell@armyspy.com")
contact.telephones = ae.mapi.MapiContactTelephonePropertySet("06605045265")
contact.personal_info.children = ["child1", "child2", "child3"]
contact.categories = ["category1", "category2", "category3"]
contact.mileage = "Algunos kilómetros de prueba"
contact.billing = "Información de facturación de prueba"
contact.other_fields.journal = True
contact.other_fields.private = True
contact.other_fields.reminder_topic = "Tema de prueba"
contact.other_fields.user_field1 = "CampoUsuarioContacto1"
contact.other_fields.user_field2 = "CampoUsuarioContacto2"
contact.other_fields.user_field3 = "CampoUsuarioContacto3"
contact.other_fields.user_field4 = "CampoUsuarioContacto4"

# Agregar una foto
with open(data_dir + "Desert.jpg", "rb") as file:
    buffer = file.read()
    contact.photo = ae.mapi.MapiContactPhoto(buffer, ae.mapi.MapiContactPhotoImageFormat.Jpeg)

# Guardar el Contacto en formato MSG
contact.save(data_dir + "MapiContact_out.msg", ae.mapi.ContactSaveFormat.MSG)

# Guardar el Contacto en formato VCF
contact.save(data_dir + "MapiContact_out.vcf", ae.mapi.ContactSaveFormat.V_CARD)
```

### **Guardar Contacto en Formato VCF Versión 3**

Para guardar un contacto en formato VCF Versión 3, utiliza la propiedad *version* de la clase [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class). Crea una nueva instancia de la clase VCardSaveOptions, establece la propiedad version del objeto VCardSaveOptions a VCardVersion.V30. Esto establece la versión de vCard a 3.0, llama al método *save* del objeto MapiContact, pasando el nombre del archivo "contact.vcf" y el objeto VCardSaveOptions como parámetros. Esto guarda el contacto como un archivo vCard con el nombre de archivo y opciones especificados. El siguiente fragmento de código te muestra cómo guardar un contacto en formato VCF Versión 3:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.version = ae.personalinfo.vcard.VCardVersion.V30
contact.save("contact.vcf", options)
```

### **Leer un MapiContact**
La clase MapiContact puede usarse para cargar contactos en formato MSG y VCard de Outlook. El siguiente fragmento de código te muestra cómo cargar contactos de Outlook guardados como MSG y VCF en un MapiContact.
#### **Cargar un Contacto desde MSG**
El siguiente fragmento de código te muestra cómo cargar un contacto desde MSG.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromMSG-LoadingContactFromMSG.py" >}}
#### **Cargar un Contacto desde VCard**
El siguiente fragmento de código te muestra cómo cargar un contacto desde vCard.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCF-LoadingContactFromVCF.py" >}}
#### **Cargar un Contacto desde VCard con Codificación Especificada**
El siguiente fragmento de código te muestra cómo cargar un contacto desde vCard con codificación especificada.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-LoadingContactFromVCardWithSpecifiedEncoding-LoadingContactFromVCardWithSpecifiedEncoding.py" >}}

#### **Guardar Elementos de Contacto VCard con Codificación Especificada**

Al guardar un archivo vCard, es posible especificar la codificación de caracteres a utilizar para garantizar la compatibilidad con caracteres no ASCII. Establece la propiedad *preferred_text_encoding* del objeto VCardSaveOptions a "utf-8". El siguiente fragmento de código muestra cómo implementar esta función en tu proyecto:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.preferred_text_encoding = "utf-8"
contact.save("contact.vcf", options)
```

#### **Guardar Archivos VCard con Campos Extendidos**

Al guardar un archivo vCard, también puedes especificar opciones que incluyan el uso de campos extendidos, que son propiedades o atributos adicionales que se pueden agregar a una vCard más allá del conjunto estándar de campos definidos por la especificación de vCard. La propiedad *use_extensions* de la clase [VCardSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.personalinfo.vcard/vcardsaveoptions/#vcardsaveoptions-class) te permite hacerlo. El siguiente fragmento de código te muestra cómo guardar un archivo VCard con campos extendidos:

```python
import aspose.email as ae

contact = ae.mapi.MapiContact()
contact.name_info = ae.mapi.MapiContactNamePropertySet("Bertha", "A.", "Buell")
options = ae.personalinfo.vcard.VCardSaveOptions()
options.use_extensions = True
contact.save("contact.vcf", options)
```
#### **Leer Múltiples Contactos en Formato VCard**

Necesitarás los siguientes métodos para obtener la lista de todos los contactos de un VCard:

```
# Verifica si la secuencia de origen VCard contiene múltiples contactos.
aspose.email.personalinfo.vcard.VCardContact.is_multi_contacts(stream)

# Carga la lista de todos los contactos del archivo VCard.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(file_path, encoding)

# Carga la lista de todos los contactos de la secuencia VCard.
aspose.email.personalinfo.vcard.VCardContact.load_as_multiple(stream, encoding)
```
El siguiente fragmento de código demostrará el proceso de leer múltiples contactos desde un archivo VCard:

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

## **Renderizar Información de Contacto a MHTML**
Un contacto de Outlook puede ser convertido a MHTML utilizando la API de Aspose.Email. Este ejemplo muestra cómo un VCard se carga en MapiContact y luego se convierte a MHTML con la ayuda de la API de MailMessage.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.py" >}}