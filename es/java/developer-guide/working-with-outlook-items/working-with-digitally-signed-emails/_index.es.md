---
title: "Administración de mensajes firmados digitalmente"
url: /es/java/working-with-outlook-notes/
weight: 100
type: docs
---

Aspose.Email implementa el algoritmo completo de objetos de correo electrónico S/MIME. Esto le da a la API el poder total para agregar firmas digitales a los mensajes de correo electrónico, conservarlas mientras convierte los mensajes de un formato a otro, eliminarlos, etc.

## **Adjuntar una firma a un correo electrónico**

The [SecureEmailManager.attachSignature](https://reference.aspose.com/email/java/com.aspose.email/secureemailmanager/#attachSignature-com.aspose.email.MapiMessage-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-com.aspose.email.SignatureOptions-) El método le permite adjuntar firmas digitales a los mensajes de correo electrónico. Después de adjuntar la firma, verifique los resultados mediante propiedades como [IsSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--), [MessageClass](https://reference.aspose.com/email/java/com.aspose.email/knownpropertylist/#MESSAGE-CLASS), y detalles de los archivos adjuntos.

Puedes proporcionar un MailMessage o un mapiMessage, un certificado privado y opciones de firma para personalizar el proceso de adjuntar firmas con el [SignatureOptions](https://reference.aspose.com/email/java/com.aspose.email/signatureoptions/) clase que permite a los usuarios especificar varias opciones para el adjunto de la firma, incluidas las firmas separadas o no separadas.

El siguiente ejemplo de código le mostrará cómo cargar un mensaje desde un archivo, adjuntar una firma digital separada y no separada mediante un certificado privado y, a continuación, comprobar si las firmas se adjuntaron correctamente.

```java
String fileName = "message.msg";
String privateCertFile = "certFile.pfx";
X509Certificate2 privateCert = new X509Certificate2(privateCertFile, "password");

MapiMessage msg = MapiMessage.load(fileName);

SignatureOptions opt = new SignatureOptions();
opt.setDetached(true);
MapiMessage signedDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedDetached.isSigned()) {
    System.out.println("Detached Signature Attached Successfully.");
}

opt.setDetached(false);
MapiMessage signedNonDetached = new SecureEmailManager().attachSignature(msg, privateCert, opt);

if (signedNonDetached.isSigned()) {
    System.out.println("Non-Detached Signature Attached Successfully.");
}
```

## **Preservar la firma al convertir de EML a MSG**

Aspose.Email conserva la firma digital al convertir de EML a MSG. El siguiente fragmento de código muestra cómo convertir de EML a MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Load mail message
MailMessage message = MailMessage.load(dataDir + "Message.eml", new EmlLoadOptions());
// Save as MSG
message.save(dataDir + "ConvertEMLToMSG_out.msg", SaveOptions.getDefaultMsgUnicode());
~~~
## **Eliminar la firma de un archivo de mensajes de Outlook**

Si tienes que eliminar la firma de un mensaje en formato MAPI, por ejemplo por motivos de compatibilidad, Aspose.Email ofrece la [MapiMessage.removeSignature](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#removeSignature--) método y el [MapiMessage.isSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--) property.

El siguiente fragmento de código muestra cómo cargar un mensaje MAPI desde un archivo, comprobar si está firmado digitalmente y, de ser así, crear un mensaje nuevo sin la firma digital:

```java
MapiMessage msg = MapiMessage.load(fileName);

if (msg.isSigned()) {
    MapiMessage unsignedMsg = msg.removeSignature();
}
```
## **Conversión de mensajes S/MIME de MSG a EML**

Aspose.Email conserva la firma digital al convertir de MSG a EML, como se muestra en el siguiente fragmento de código.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage msg = MailMessage.load(dataDir + "message.eml");
MapiMessage mapi = MapiMessage.fromMailMessage(msg, new MapiConversionOptions(OutlookMessageFormat.Unicode));
// Save File to disk
mapi.save(dataDir + "ConvertMIMEMessagesFromMSGToEML_out.msg");
~~~

## **Descifrar un archivo MSG con certificado**

Si tiene mensajes MAPI cifrados y necesita descifrarlos con la clave privada almacenada en un certificado, las siguientes funciones de Aspose.Email pueden resultar útiles:

- [MapiMessage.isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isEncrypted--) - Obtiene un valor que indica si el mensaje está cifrado.
- [MapiMessage.decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt--) - Descifra este mensaje (el método busca en el usuario y la computadora actuales de My stores el certificado y la clave privada apropiados).
- [MapiMessage.decrypt (certificado X509 Certificate2)](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Descifra este mensaje con un certificado.

El siguiente fragmento de código muestra cómo trabajar con mensajes MAPI cifrados:

```java
X509Certificate2 privateCert = new X509Certificate2("privateCertFile", "password");
MapiMessage msg = MapiMessage.load("encrypted.msg");

if (msg.isEncrypted()) {
    MapiMessage decryptedMsg = msg.decrypt(privateCert);
    //MapiMessage decryptedMsg = msg.decrypt(/*byte[]*/rawPrivateCert, "password");
}
```
