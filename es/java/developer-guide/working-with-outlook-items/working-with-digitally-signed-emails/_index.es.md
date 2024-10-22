---
title: "Gestionando Mensajes Firmados Digitalmente"
url: /es/java/working-with-outlook-notes/
weight: 100
type: docs
---

Aspose.Email implementa el algoritmo completo del objeto de correo S/MIME. Esto le da a la API el poder completo para agregar firmas digitales a los mensajes de correo electrónico, preservarlas al convertir mensajes entre formatos, eliminarlas, etc.

## **Adjuntar una Firma a un Correo Electrónico**

El método [SecureEmailManager.attachSignature](https://reference.aspose.com/email/java/com.aspose.email/secureemailmanager/#attachSignature-com.aspose.email.MapiMessage-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-com.aspose.email.SignatureOptions-) permite adjuntar firmas digitales a mensajes de correo electrónico. Después de adjuntar la firma, verifique los resultados a través de propiedades como [IsSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--), [MessageClass](https://reference.aspose.com/email/java/com.aspose.email/knownpropertylist/#MESSAGE-CLASS) y detalles del adjunto.

Puede proporcionar un MailMessage o MapiMessage, un certificado privado y opciones de firma para personalizar el proceso de adjuntar la firma con la clase [SignatureOptions](https://reference.aspose.com/email/java/com.aspose.email/signatureoptions/) que permite a los usuarios especificar varias opciones para la adjunta de firma, incluyendo firmas separadas o no separadas.

El siguiente ejemplo de código te mostrará cómo cargar un mensaje desde un archivo, adjuntar una firma digital separada y no separada usando un certificado privado, y luego verificar si las firmas se adjuntaron con éxito.

```java
String fileName = "message.msg";
String privateCertFile = "certFile.pfx";
X509Certificate2 privateCert = new X509Certificate2(privateCertFile, "password");

MapiMessage msg = MapiMessage.load(fileName);

SignatureOptions opt = new SignatureOptions();
opt.setDetached(true);
MapiMessage signedDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedDetached.isSigned()) {
    System.out.println("Firma Separada Adjunta Correctamente.");
}

opt.setDetached(false);
MapiMessage signedNonDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedNonDetached.isSigned()) {
    System.out.println("Firma No Separada Adjunta Correctamente.");
}
```

## **Preservar la Firma al Convertir de EML a MSG**

Aspose.Email preserva la firma digital al convertir de EML a MSG. El siguiente fragmento de código te muestra cómo convertir de EML a MSG.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

// Cargar mensaje de correo
MailMessage message = MailMessage.load(dataDir + "Message.eml", new EmlLoadOptions());
// Guardar como MSG
message.save(dataDir + "ConvertEMLToMSG_out.msg", SaveOptions.getDefaultMsgUnicode());
~~~

## **Eliminar Firma de un Archivo de Mensaje de Outlook**

Si te enfrentas a la necesidad de eliminar la firma de un mensaje en formato MAPI, por ejemplo, por motivos de compatibilidad, Aspose.Email ofrece el método [MapiMessage.removeSignature](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#removeSignature--) y la propiedad [MapiMessage.isSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--). 

El siguiente fragmento de código muestra cómo cargar un mensaje MAPI desde un archivo, verificar si está firmado digitalmente y, si es así, crear un nuevo mensaje sin la firma digital: 

```java
MapiMessage msg = MapiMessage.load(fileName);

if (msg.isSigned()) {
    MapiMessage unsignedMsg = msg.removeSignature();
}
```

## **Convertir Mensajes S/MIME de MSG a EML**

Aspose.Email preserva la firma digital al convertir de MSG a EML como se muestra en el siguiente fragmento de código.

~~~Java
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-Java
// La ruta al directorio de archivos.
String dataDir = "outlook/";

MailMessage msg = MailMessage.load(dataDir + "message.eml");
MapiMessage mapi = MapiMessage.fromMailMessage(msg, new MapiConversionOptions(OutlookMessageFormat.Unicode));
// Guardar archivo en disco
mapi.save(dataDir + "ConvertMIMEMessagesFromMSGToEML_out.msg");
~~~

## **Descifrar un Archivo MSG con Certificado**

Si tienes mensajes MAPI cifrados y necesitas descifrarlos usando la clave privada almacenada en un certificado, las siguientes características de Aspose.Email pueden ser útiles:

- [MapiMessage.isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isEncrypted--) - Obtiene un valor que indica si el mensaje está cifrado.
- [MapiMessage.decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt--) - Descifra este mensaje (el método busca en las tiendas de certificados del usuario y computadora actuales el certificado y clave privada apropiados).
- [MapiMessage.decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Descifra este mensaje con el certificado.

El siguiente fragmento de código muestra cómo trabajar con mensajes MAPI cifrados:

```java
X509Certificate2 privateCert = new X509Certificate2("privateCertFile", "password");
MapiMessage msg = MapiMessage.load("encrypted.msg");

if (msg.isEncrypted()) {
    MapiMessage decryptedMsg = msg.decrypt(privateCert);
    //MapiMessage decryptedMsg = msg.decrypt(/*byte[]*/rawPrivateCert, "password");
}
```