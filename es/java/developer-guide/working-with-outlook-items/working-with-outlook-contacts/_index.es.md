---
title: "Trabajando con Contactos de Outlook"
url: /es/java/working-with-outlook-contacts/
weight: 80
type: docs
---

## **Crear Contacto de Outlook**

Aspose.Email para Java soporta la creación de contactos de Outlook (VCards) utilizando la clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/). [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) contiene muchos métodos, algunos de los cuales se indican a continuación.

- [MapiContactElectronicAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) contiene un conjunto de [MapiContactElectronicAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/).
- [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--)
- [MapiContactNamePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--)
- [MapiContactPersonalInfoPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--)
- [MapiContactPhysicalAddressPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) contiene un conjunto de [MapiContactPhysicalAddress](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--).
- [MapiContactProfessionalPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
- [MapiContactTelephonePropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--)

### **Estructura de Contacto en Aspose.Email para Java**

A continuación se muestra la jerarquía implementada para contactos en Aspose.Email para Java. El nombre de la clase relevante se indica junto a cada propiedad. Se proporcionan hipervínculos a la documentación en línea para referencia adicional.

1. [Contact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) (MapiContact)
   1. [Direcciones Electrónicas](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddresspropertyset/#MapiContactElectronicAddressPropertySet--) (MapiContactElectronicAddressPropertySet)
      1. [Email1](https://reference.aspose.com/email/java/com.aspose.email/mapicontactelectronicaddress/) (MapiContactElectronicAddress)
         1. Tipo de Dirección
         1. Nombre para Mostrar
         1. Dirección de Correo Electrónico
         1. Número de Fax
      1. Email2
      1. Email3
      1. Fax en Casa
      1. Fax Primario
      1. Fax de Negocios
   1. [Eventos](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) (`MapiContactEventPropertySet`). A continuación se muestra un ejemplo de cómo establecer eventos.
      1. Cumpleaños
      1. Aniversario de Boda
   1. [Información del Nombre](https://reference.aspose.com/email/java/com.aspose.email/mapicontactnamepropertyset/#MapiContactNamePropertySet--) (`MapiContactNamePropertySet`)
      1. Nombre para Mostrar
      1. Prefijo del Nombre para Mostrar
      1. Archivo Bajo
      1. Archivo Bajo ID
      1. Generación
      1. Nombre de Pila
      1. Iniciales
      1. Segundo Nombre
      1. Apodo
      1. Apellido
   1. [Información Personal](https://reference.aspose.com/email/java/com.aspose.email/mapicontactpersonalinfopropertyset/#MapiContactPersonalInfoPropertySet--) (MapiContactPersonalInfoPropertySet)
      1. Cuenta
      1. Página de Inicio de Negocios
      1. Nombre de Red de Computadora
      1. ID del Cliente
      1. Ubicación de Negocios Libre
      1. Sitio FTP
      1. Género
      1. Número de Identificación del Gobierno
      1. Pasatiempos
      1. HTML
      1. Dirección de Mensajería Instantánea
      1. Idioma
      1. Ubicación
      1. Notas
      1. Número de Identificación Organizacional
      1. Página de Inicio Personal
      1. Referido por Nombre
      1. Nombre del Cónyuge
   1. [Dirección Física](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdresspropertyset/#MapiContactPhysicalAddressPropertySet--) (MapiContactPhysicalAddressPropertySet)
      1. [Dirección de Casa](https://reference.aspose.com/email/java/com.aspose.email/mapicontactphysicaladdress/#MapiContactPhysicalAddress--) (MapiContactPhysicalAddress)
         1. Dirección
         1. Ciudad
         1. País
         1. Código del País
         1. Código Postal
         1. Apartado de Correos
         1. Estado o Provincia
      1. Otra Dirección
      1. Dirección de Trabajo
   2. [Información Profesional](https://reference.aspose.com/email/java/com.aspose.email/mapicontactprofessionalpropertyset/#MapiContactProfessionalPropertySet--)
      1. Asistente
      2. Nombre de la Empresa
      3. Nombre del Departamento
      4. Nombre del Gerente
      5. Ubicación de la Oficina
      6. Profesión
      7. Título
   3. [Teléfonos](https://reference.aspose.com/email/java/com.aspose.email/mapicontacttelephonepropertyset/#MapiContactTelephonePropertySet--) (MapiContactTelephonePropertySet)
      1. Número de Teléfono del Asistente
      2. Número de Teléfono de Negocios2
      3. Número de Teléfono de Negocios
      4. Número de Teléfono de Callback
      5. Número de Teléfono del Automóvil
      6. Número de Teléfono Principal de la Empresa
      7. Número de Teléfono de Casa2
      8. Número de Teléfono de Casa
      9. Número ISDN
      10. Número de Teléfono Móvil
      11. Otro Número de Teléfono
      12. Número de Teléfono de Buscador
      13. Número de Teléfono Primario
      14. Número de Teléfono de Radio
      15. Número de Telex
      16. Número de Teléfono TTY/TDD

El siguiente código utiliza Aspose.Email para crear un contacto de Outlook y lo llena con nombre, propiedades profesionales, dirección física y correo electrónico. También muestra cómo agregar [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/#MapiContactEventPropertySet--) al contacto.

|![todo:image_alt_text](https://i.imgur.com/D4jXgXo.png)|
| :- |
|**Figura: Un contacto de Microsoft Outlook codificado con Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-CreateOutlookContact.java" >}}

### **Agregar Información de Evento de Contacto a un MapiContact**

Microsoft Outlook permite a los usuarios agregar información de eventos a un contacto. El evento contiene el cumpleaños y el aniversario de boda. Aspose.Email proporciona la clase [MapiContactEventPropertySet](https://reference.aspose.com/email/java/com.aspose.email/mapicontacteventpropertyset/) para agregar esta información a un contacto. Esto se elabora en el siguiente ejemplo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateOutlookContact-AddingContactEventInformationToAMapiContact.java" >}}

## **Crear, Guardar y Leer Contactos de Outlook**

Aspose.Email permite a los desarrolladores crear contactos de Microsoft Outlook así como mensajes de correo electrónico. La clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) proporciona todas las propiedades de contacto necesarias para crear un contacto de Outlook. Este artículo muestra cómo crear, guardar y leer un contacto de Outlook utilizando la clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

### **Crear y Guardar un MapiContact**

Los siguientes pasos se pueden usar para crear y guardar un contacto en disco:

1. Instanciar un nuevo objeto de la clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Ingresar información relacionada con varias propiedades del contacto.
1. Agregar datos de foto al contacto, si los hay.
1. Guardar el contacto en formato MSG o VCard.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-CreatingAndSavingAMapiContact.java" >}}

### **Guardar Contacto en Formato VCF Versión 3**

Para guardar el contacto en formato VCF versión 3, use el enumerable [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) para establecer la propiedad [VCardSaveOptions.Version](https://reference.aspose.com/email/java/com.aspose.email/vcardsaveoptions/#getVersion--). El siguiente código de ejemplo demuestra el uso del enumerable [VCardVersion](https://reference.aspose.com/email/java/com.aspose.email/vcardversion/) para guardar el contacto en formato VCF versión 3.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateV30Contact-1.java" >}}

### **Leer un MapiContact**

La clase [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) se puede utilizar para cargar tanto archivos MSG de Microsoft Outlook como contactos en formato VCard. Los siguientes ejemplos de código muestran cómo cargar contactos de Outlook guardados como MSG y VCF en [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).

#### **Cargar un Contacto desde MSG**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromMSG.java" >}}

#### **Cargar un Contacto desde VCard**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingAContactFromVCard.java" >}}

#### **Cargar Contacto VCard con Codificación Especificada**

Método Soportado: [MapiContact.fromVCard(String, Encoding)](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/#fromVCard-java.lang.String-java.nio.charset.Charset-)

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-CreateSaveAndReadOutlookContact-LoadingVCardContactWithSpecifiedEncoding.java" >}}

## **Renderizando Información de Contacto a MHTML**

El contacto de Outlook puede ser convertido a MHTML utilizando la API de Aspose.Email. Este ejemplo muestra cómo se carga un VCard en [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) y luego se convierte a MHTML con la ayuda de la API [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/).

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-msg-RenderingContactInformationToMhtml-RenderingContactInformationToMhtml.java" >}}