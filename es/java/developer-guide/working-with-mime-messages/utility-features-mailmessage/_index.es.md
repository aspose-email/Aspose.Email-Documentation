---
title: "Características de Utilidad - MailMessage"
url: /es/java/utility-features-mailmessage/
weight: 50
type: docs
---

## **Encriptación y Desencriptación de Mensajes**

Aspose.Email proporciona la posibilidad de encriptar y desencriptar mensajes de correo electrónico. Este tema muestra cómo se puede cargar y encriptar un mensaje existente o nuevo utilizando [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). Los métodos [encrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) y [decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt--) devuelven el objeto **MailMessage** para los efectos aplicados y se debe tener en cuenta al encriptar/desencriptar mensajes. Encriptar y desencriptar mensajes implica los siguientes pasos:

1. Crear un nuevo mensaje o cargar uno existente
2. Encriptar el mensaje utilizando el archivo de certificado
3. Enviar el mensaje o guardarlo
4. Desencriptar el mensaje según sea necesario

El siguiente fragmento de código muestra cómo encriptar y desencriptar mensajes.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.java" >}}

### **Verificando un Mensaje para Encriptación**

La clase Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) permite verificar si un mensaje está encriptado o no. La propiedad [isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isEncrypted--) de **MailMessage** permite comprobar esto como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CheckMessageForEncryption-CheckMessageForEncryption.java" >}}

## **Encriptación de Mensajes con X509Certificate**

Aspose.Email proporciona la API para trabajar con Mensajes Encriptados con X509Certificate:

La clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) tiene los siguientes métodos para trabajar con la encriptación de mensajes:

- public MailMessage [attachSignature(X509Certificate2 certificate, boolean detached)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-boolean-) - Crea un mensaje firmado.
- public MailMessage [attachSignature(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Crea un mensaje firmado.
- public X509Certificate2[] [checkSignatureCert()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkSignatureCert--) - Verifica si hay firma en el MailMessage existente.
- public MailMessage [decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- public MailMessage [encrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- public MailMessage [encrypt(X509Certificate2[] certificates)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2---)


## **Configurar Opciones de Localización para Aspose.Email**

Puedes usar la clase [LocaleOptions](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/) en caso de que la localización predeterminada no sea reconocida y establecer la localización más apropiada para la biblioteca de Aspose Email. Ofrece los siguientes métodos para realizar la tarea:

- [getLocale()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#getLocale--) - Devuelve la localización predeterminada para Aspose.Email.
- [setLocale(Locale locale)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.util.Locale-) y [setLocale(String localeName)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.lang.String-) - Establecen la localización predeterminada relacionada con Aspose.Email.
- [clear()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#clear--) - Limpia la localización predeterminada para Aspose.Email. Se utilizará la localización predeterminada para Java.

El siguiente ejemplo de código demuestra cómo cargar un mensaje de correo desde un archivo utilizando la configuración de localización especificada:

```java
final Locale locale = new Locale("es", "ES");
Locale.setDefault(locale);

// establecer localización para la biblioteca Aspose Email
LocaleOptions.setLocale("es-ES");
// o
//LocaleOptions.setLocale(new Locale("es", "ES"));

MailMessage.load("document.msg");
```
Este código asegura que la aplicación y la biblioteca Aspose.Email usen las localizaciones especificadas para manejar el idioma, el país y las convenciones culturales.

## **MailMessages que contienen archivos adjuntos TNEF**

El Formato de Encapsulación Neutral de Transporte (TNEF) es un formato de archivo adjunto de correo electrónico propietario utilizado por Microsoft Outlook y Microsoft Exchange Server. La API de Aspose.Email permite leer mensajes de correo electrónico que tienen archivos adjuntos TNEF y modificar su contenido. El correo electrónico puede guardarse luego como un correo electrónico normal o en el mismo formato, preservando los archivos adjuntos TNEF. Este artículo muestra diferentes ejemplos de código para trabajar con mensajes que contienen archivos adjuntos TNEF.

### **Leer un Mensaje Preservando Archivos Adjuntos TNEF**

El siguiente fragmento de código muestra cómo leer un mensaje preservando archivos adjuntos TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.java" >}}

### **Actualizar Recursos en un Archivo Adjunto TNEF y Preservar el Formato TNEF**

El siguiente fragmento de código muestra cómo actualizar recursos en un archivo adjunto TNEF y preservar el formato TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-UpdateTNEFAttachments-UpdateTNEFAttachments.java" >}}

### **Agregar Nuevos Archivos Adjuntos al Mensaje Principal que Contiene TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-AddNewAttachmentToMessageContainingTNEF.java" >}}

### **Crear TNEF EML desde MSG**

Los MSG de Outlook a veces contienen información como tablas y estilos de texto que pueden verse alterados si se convierten a EML. Crear mensajes TNEF a partir de tales archivos MSG nos permite mantener el formato e incluso enviar tales mensajes a través de clientes de correo electrónico conservando el formato. 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreatingTNEFEMLFromMSG.java" >}}

Para crear el TNEF, se puede utilizar el siguiente código de ejemplo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreateTNEF.java" >}}

### **Detectar si un Mensaje es TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-DetectIfAMessageIsTNEF.java" >}}

## **Procesar Mensajes Rebotados**

Es muy común que un mensaje enviado a un destinatario pueda rebotar por cualquier razón, como una dirección de destinatario no válida. La API de Aspose.Email tiene la capacidad de procesar tal mensaje para verificar si es un correo electrónico rebotado o un mensaje de correo electrónico regular. El método [CheckBounced](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkBounced--) de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) devuelve un resultado válido si el mensaje de correo electrónico es un correo electrónico rebotado.

Este artículo muestra el uso de la clase [BounceResult](https://reference.aspose.com/email/java/com.aspose.email/bounceresult/) que proporciona la capacidad de verificar si un mensaje es un correo electrónico rebotado. Además, ofrece información detallada sobre los destinatarios, la acción tomada y la razón de la notificación.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ProcessBouncedMessages-.java" >}}

## **Ignorar excepciones**

La biblioteca ofrece una clase [ExceptionManager](https://reference.aspose.com/email/java/com.aspose.email/exceptionmanager/) para implementar la capacidad de ignorar excepciones en la funcionalidad de tu aplicación. El siguiente fragmento de código demuestra cómo establecer un callback para manejar excepciones:

```java
 ExceptionManager.setIgnoreExceptionsHandler( new IgnoreExceptionsCallback() {

   //ruta de la excepción: {Módulo}\{Método}\{Acción}\{GUID}

   //ejemplo: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598

   public boolean invoke(AsposeException ex, String path) {

       //Ignorar todas las excepciones en MailMessage.Load

       return path.equals("MailMessage\\Load");

   }

});
```
O utilizar una **alternativa**:

```java
 ExceptionManager.setIgnoreAll(true);
```
Además, puedes establecer un callback para el **registro de excepciones ignoradas**:

```java
ExceptionManager.setIgnoreExceptionsLogHandler( new IgnoreExceptionsLogCallback() {

   public void invoke(String message) {

        System.out.println("=== EXCEPCIÓN IGNORADA === " + message);

   }

});
```
Se notificará al usuario que la excepción puede ser ignorada mediante un mensaje de error. Por ejemplo:

Excepción en el mensaje:

```java
AsposeArgumentException: las propiedades no deben estar vacías.
```

Si deseas ignorar una excepción y continuar, puedes usar:
```java
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")

El archivo adjunto TNEF no válido se interpretará como un archivo adjunto regular.
```

## **Analizador de Spam Bayesiano**

Aspose.Email proporciona la facilidad de filtrado de correos electrónicos utilizando el analizador de spam Bayesiano. Proporciona la clase [SpamAnalyzer](https://reference.aspose.com/email/java/com.aspose.email/spamanalyzer/) para este propósito. Este artículo muestra cómo entrenar el filtro para distinguir entre spam y correos electrónicos regulares basados en la base de datos de palabras.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-BayesianSpamAnalyzer-.java" >}}

## **Obteniendo Preamble y Epilogue de Mensajes EML**

En el formato MIME, el *preamble* es el texto que aparece después de los encabezados y antes del primer límite de múltiples partes. El *epilogue* es el texto que aparece después del último límite y antes del final del mensaje. Este texto generalmente no es visible para los usuarios en los lectores de correo, pero algunas implementaciones MIME pueden usarlo para insertar notas para los destinatarios que leen el mensaje usando programas no conformes a MIME.

El siguiente fragmento de código muestra cómo obtener el preámbulo y el epílogo de un mensaje EML, lo que se puede lograr con los métodos correspondientes de la clase [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/):

- [setPreamble(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setPreamble-java.lang.String-) - Obtiene o establece un texto de preámbulo.
- [setEpilogue(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setEpilogue-java.lang.String-) - Obtiene o establece un texto de epílogo.

```java
// Obtiene o establece un texto de preámbulo.
public String getPreamble, setPreamble

// Obtiene o establece un texto de epílogo.
public String getEpilogue, setEpilogue
```