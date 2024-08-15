---
title: "Trabajar con contactos de Outlook"
url: /es/java/working-with-outlook-contacts/
weight: 80
type: docs
---

## **Crear contacto de Outlook**

Aspose.Email para Java admite la creación de contactos de Outlook (vCards) mediante [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class. [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) contiene muchos métodos, algunos de los cuales se detallan a continuación.

- [MapiContactElectronicAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) contiene un conjunto de [MapiContactElectronicAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/).
- [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--)
- [MapiContactNamePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--)
- [MapiContactPersonalInfoPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--)
- [MapiContactPhysicalAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) contiene un conjunto de [MapiContactPhysicalAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--).
- [MapiContactProfessionalPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
- [MapiContactTelephonePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--)
 
### **Estructura de contactos en Aspose.Email para Java**

A continuación se muestra la jerarquía implementada para los contactos en Aspose.Email para Java. El nombre de la clase correspondiente se indica junto a cada propiedad. Se proporcionan hipervínculos a la documentación en línea para obtener más información.

1. [Contact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) (MapiContact)
   1. [Direcciones electrónicas](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) (MapiContactElectronicAddressPropertySet)
      1. [Email1](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/) (MapiContactElectronicAddress)
         1. Tipo de dirección
         1. Nombre para mostrar
         1. Dirección de correo electrónico
         1. Número de fax
      1. Email2
      1. Email3
      1. Fax a domicilio
      1. Fax principal
      1. Fax empresarial
   1. [Events](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) (`MapiContactEventPropertySet`). A continuación se muestra un ejemplo de cómo configurar eventos.
      1. Birthday
      1. Aniversario de boda
   1. [Información de nombre](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--) (`MapiContactNamePropertySet`)
      1. Nombre para mostrar
      1. Prefijo de nombre para mostrar
      1. Archivar en
      1. Archivo con ID
      1. Generation
      1. Nombre de pila
      1. Initials
      1. Segundo nombre
      1. Nombre de apodo
      1. Surname
   1. [Información personal](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--) (MapiContactPersonalInfoPropertySet)
      1. Account
      1. Página principal de la empresa
      1. Nombre de red informática
      1. ID de cliente
      1. Ubicación comercial gratuita
      1. Sitio FTP
      1. Gender
      1. Número de identificación gubernamental
      1. Hobbies
      1. HTML
      1. Dirección de mensajería instantánea
      1. Language
      1. Location
      1. Notes
      1. Número de identificación de la organización
      1. Página de inicio personal
      1. Referido por nombre
      1. Nombre del cónyuge
   1. [Dirección física](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) (MapiContactPhysicalAddressPropertySet)
      1. [Domicilio](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--) (MapiContactPhysicalAddress)
         1. Address
         1. City
         1. Country
         1. Código de país
         1. Código postal
         1. Apartado de correos
         1. Estado o provincia
      1. Otra dirección
      1. Dirección de trabajo
   2. [Información profesional](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
      1. Assistant
      2. Nombre de la empresa
      3. Nombre de salida
      4. Nombre del gerente
      5. Ubicación de la oficina
      6. Profession
      7. Title
   3. [Telephones](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--) (MapiContactTelephonePropertySet)
      1. Número de teléfono del asistente
      2. Número de teléfono de Business2
      3. Número de teléfono comercial
      4. Número de teléfono de devolución de llamada
      5. Número de teléfono del coche
      6. Número de teléfono principal de la empresa
      7. Número de teléfono de Home2
      8. Número de teléfono residencial
      9. Número ISDN
      10. Número de teléfono móvil
      11. Otro número de teléfono
      12. Número de teléfono del localizador
      13. Número de teléfono principal
      14. Número de teléfono de radio
      15. Número de télex
      16. Número de teléfono TTY/TDD

El siguiente código usa Aspose.Email para crear un contacto de Outlook y lo rellena con el nombre, las propiedades profesionales, la dirección física y el correo electrónico. También muestra cómo agregar [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) al contacto.

|![todo:image_alt_text](https://i.imgur.com/D4jXgXo.png)|
|: - |
|**Figura: Un contacto de Microsoft Outlook codificado con Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-CreateOutlookContact.java" >}}

### **Agregar información de eventos de contacto a un MapiContact**

Microsoft Outlook permite a los usuarios agregar información de eventos a un contacto. El evento celebra el cumpleaños y el aniversario de boda. Aspose.Email proporciona la [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/) clase para agregar esta información a un contacto. Esto se explica en el siguiente ejemplo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-AddingContactEventInformationToAMapiContact.java" >}}

## **Crear, guardar y leer contactos de Outlook**

Aspose.Email permite a los desarrolladores crear contactos de Microsoft Outlook y mensajes de correo electrónico. El [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) La clase proporciona todas las propiedades de contacto necesarias para crear un contacto de Outlook. En este artículo se muestra cómo crear, guardar y leer un contacto de Outlook mediante [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.

### **Crear y guardar un MapiContact**

Se pueden seguir los pasos siguientes para crear y guardar un contacto en un disco:

1. Crea una instancia de un nuevo objeto del [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.
1. Introduzca la información relacionada con las distintas propiedades del contacto.
1. Agrega datos de fotos al contacto, si los hay.
1. Guarda el contacto en formato MSG o vCard.
 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-CreatingAndSavingAMapiContact.java" >}}

### **Guardar contacto en formato VCF de la versión 3**

Para guardar el contacto en el formato VCF de la versión 3, utilice [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) enumerable para establecer el [VCardSaveOptions.Version](https://reference.aspose.com/email/java/com.aspose.email/vcardsaveoptions/#getVersion--) propiedad. El siguiente código de ejemplo demuestra el uso de [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) enumerable para guardar el formato VCF versión 3 del contacto.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateV30Contact-1.java" >}}

### **Leer un MapiContact**

The [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) La clase se puede usar para cargar tanto archivos MSG de Microsoft Outlook como contactos en formato vCard. Los siguientes ejemplos de código muestran cómo cargar los contactos de Outlook guardados como MSG y VCF en [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

#### **Cargar un contacto desde MSG**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromMSG.java" >}}

#### **Cargar un contacto desde vCard**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromVCard.java" >}}

#### **Cargar vCard Contact con la codificación especificada**

Método compatible: [MapiContact.fromvCard (cadena, codificación)](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/#fromVCard-java.lang.String-java.nio.charset.Charset-)

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingVCardContactWithSpecifiedEncoding.java" >}}

## **Representación de la información de contacto en MHTML**

Outlook Contact se puede convertir a MHTML mediante la API Aspose.Email. Este ejemplo muestra cómo se carga una vCard en [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) y luego se convirtió a MHTML con la ayuda de [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) API.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.java" >}}
