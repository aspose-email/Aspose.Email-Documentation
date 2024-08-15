---
title: "Características de la utilidad - MailMessage"
url: /es/java/utility-features-mailmessage/
weight: 50
type: docs
---

## **Cifrado y descifrado de mensajes**

Aspose.Email ofrece la posibilidad de cifrar y descifrar mensajes de correo electrónico. Este tema muestra cómo se puede cargar y cifrar un mensaje nuevo o existente mediante [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). El [encrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) and [decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt--) los métodos devuelven el **MailMessage** objeto de los efectos aplicados y debe tenerse en cuenta al cifrar/descifrar los mensajes. El cifrado y descifrado de los mensajes implica los siguientes pasos:

1. Crea un mensaje nuevo o carga uno existente
2. Cifre el mensaje con el archivo de certificado
3. Enviar el mensaje o guardarlo
4. Descifra el mensaje según sea necesario

El siguiente fragmento de código muestra cómo cifrar y descifrar mensajes.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.java" >}}

### **Comprobar el cifrado de un mensaje**

Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) La clase permite comprobar si un mensaje está cifrado o no. El [isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isEncrypted--) propiedad de **MailMessage** permite comprobar esto como se muestra en el siguiente ejemplo de código.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CheckMessageForEncryption-CheckMessageForEncryption.java" >}}

## **Cifrado de mensajes con certificado X509**

Aspose.Email proporciona la API para trabajar con mensajes cifrados con el certificado X509:

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) la clase tiene los siguientes métodos para trabajar con el cifrado de mensajes:

- mensaje de correo público [Adjuntar firma (certificado X509 Certificate2, booleano separado)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-boolean-) - Crea un mensaje firmado.
- mensaje de correo público [Adjuntar firma (certificado X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Crea un mensaje firmado.
- certificado X509 público [2] [checkSignatureCert()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkSignatureCert--) - Comprueba la firma existente en MailMessage.
- mensaje de correo público [descifrar (certificado X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- mensaje de correo público [cifrar (certificado X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- mensaje de correo público [cifrar (certificados X509 Certificate2 [])](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2---)


## **Configurar las opciones de configuración regional para Aspose.Email**

Puedes usar [LocaleOptions](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/) clasifique en caso de que la configuración regional predeterminada no se reconozca y establezca la configuración regional más adecuada para Aspose Email lib. Ofrece los siguientes métodos para realizar la tarea:

- [getLocale()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#getLocale--) - Devuelve la configuración regional predeterminada de Aspose.Email.
- [setLocale (Configuración regional)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.util.Locale-) and [setLocale (nombre de la cadena LocaleName)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.lang.String-) - Establezca la configuración regional predeterminada relacionada con Aspose.Email.
- [clear()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#clear--) - Borra la configuración regional predeterminada de Aspose.Email. Se utilizará la configuración regional predeterminada para Java.

El siguiente ejemplo de código muestra cómo cargar un mensaje de correo desde un archivo con la configuración regional especificada:

```java
final Locale locale = new Locale("en", "DE");
Locale.setDefault(locale);

// set Locale for Aspose Email lib
LocaleOptions.setLocale("en-US");
// or
//LocaleOptions.setLocale(new Locale("en", "US"));

MailMessage.load("document.msg");
```
Este código garantiza que la aplicación y la biblioteca Aspose.Email utilicen las configuraciones regionales especificadas para gestionar las convenciones lingüísticas, nacionales y culturales.

## **Mensajes de correo que contienen archivos adjuntos de TNEF**

El formato de encapsulación neutral para el transporte (TNEF) es un formato patentado de archivos adjuntos de correo electrónico que utilizan Microsoft Outlook y Microsoft Exchange Server. La API Aspose.Email le permite leer los mensajes de correo electrónico que tienen archivos adjuntos en TNEF y modificar su contenido. Luego, el correo electrónico se puede guardar como un correo electrónico normal o en el mismo formato, conservando los archivos adjuntos de TNEF. En este artículo se muestran diferentes ejemplos de código para trabajar con mensajes que contienen archivos adjuntos de TNEF.

### **Lectura de un mensaje conservando los archivos adjuntos del TNEF**

El siguiente fragmento de código muestra cómo leer un mensaje conservando los archivos adjuntos de TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.java" >}}

### **Actualización de recursos en un archivo adjunto TNEF y conservación del formato TNEF**

El siguiente fragmento de código muestra cómo actualizar los recursos de un archivo adjunto TNEF y conservar el formato TNEF.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-UpdateTNEFAttachments-UpdateTNEFAttachments.java" >}}

### **Agregar nuevos archivos adjuntos al mensaje principal que contiene TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-AddNewAttachmentToMessageContainingTNEF.java" >}}

### **Creación de TNEF EML a partir de MSG**

Los mensajes de Outlook a veces contienen información como tablas y estilos de texto que pueden alterarse si se convierten a EML. La creación de mensajes TNEF a partir de estos archivos MSG nos permite conservar el formato e incluso enviar dichos mensajes a través de los clientes de correo electrónico que conservan el formato. 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreatingTNEFEMLFromMSG.java" >}}

Para crear el TNEF, se puede usar el siguiente código de ejemplo.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreateTNEF.java" >}}

### **Detectar si un mensaje es TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-DetectIfAMessageIsTNEF.java" >}}

## **Procesamiento de mensajes devueltos**

Es muy común que un mensaje enviado a un destinatario rebote por cualquier motivo, como una dirección de destinatario no válida. La API Aspose.Email tiene la capacidad de procesar un mensaje de este tipo para comprobar si se trata de un correo electrónico devuelto o de un mensaje de correo electrónico normal. La [CheckBounced](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkBounced--) método del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) La clase devuelve un resultado válido si el mensaje de correo electrónico es un correo devuelto.

Este artículo muestra el uso de [BounceResult](https://reference.aspose.com/email/java/com.aspose.email/bounceresult/) clase que proporciona la capacidad de comprobar si un mensaje es un correo electrónico devuelto. Además, proporciona información detallada sobre los destinatarios, las medidas adoptadas y el motivo de la notificación.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ProcessBouncedMessages-.java" >}}

## **Ignorar excepciones**

La biblioteca ofrece un [ExceptionManager](https://reference.aspose.com/email/java/com.aspose.email/exceptionmanager/) clase para implementar la capacidad de ignorar excepciones en la funcionalidad de su aplicación. El siguiente fragmento de código muestra cómo configurar una devolución de llamada para gestionar las excepciones:

```java
 ExceptionManager.setIgnoreExceptionsHandler( new IgnoreExceptionsCallback() {

   //exception path: {Module}\{Method}\{Action}\{GUID}

   //example: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598

   public boolean invoke(AsposeException ex, String path) {

       //Ignore all exceptions on MailMessage.Load

       return path.equals("MailMessage\\Load");

   }

});
```
O usa un **alternative**:

```java
 ExceptionManager.setIgnoreAll(true);
```
Además, puede configurar una devolución de llamada para ignorados **registro de excepciones**:

```java
ExceptionManager.setIgnoreExceptionsLogHandler( new IgnoreExceptionsLogCallback() {

   public void invoke(String message) {

        System.out.println("=== EXCEPTION IGNORED === " + message);

   }

});
```
Se notificará al usuario que la excepción puede ignorarse mediante un mensaje de error. Por ejemplo:

Excepción en el mensaje:

```java
AsposeArgumentException: properties should not be empty.
```

Si desea ignorar una excepción y desea continuar, puede usar:
```java
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")

Invalid TNEF Attachment will be interpreted as regular attachment.
```

## **Analizador bayesiano de spam**

Aspose.Email ofrece la posibilidad de filtrar el correo electrónico mediante el analizador de spam Bayes. Proporciona la [SpamAnalyzer](https://reference.aspose.com/email/java/com.aspose.email/spamanalyzer/) clase para este propósito. Este artículo muestra cómo entrenar el filtro para que distinga entre el correo basura y el correo normal basándose en la base de datos de palabras.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-BayesianSpamAnalyzer-.java" >}}

## **Obtención del preámbulo y el epílogo de los mensajes EML**

En el formato MIME, el *preamble* es el texto que aparece después de los encabezados y antes del primer límite multiparte. El *epilogue* es el texto que aparece después del último límite y antes del final del mensaje. Los usuarios de los lectores de correo no suelen ver este texto, pero algunas implementaciones de MIME pueden usarlo para insertar notas para los destinatarios que leen el mensaje mediante programas que no son compatibles con MIME.

El siguiente fragmento de código muestra cómo obtener el preámbulo y el epílogo de un mensaje EML, lo que se puede lograr con los métodos correspondientes del [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class:

- [setPreamble (valor de cadena)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setPreamble-java.lang.String-) - Obtiene o establece un texto de preámbulo.
- [setEpilogue (valor de cadena)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setEpilogue-java.lang.String-) - Obtiene o establece un texto de epílogo.

```java
// Gets or sets a preamble text.
public String getPreamble, setPreamble

// Gets or sets an epilogue text.
public String getEpilogue, setEpilogue
```

