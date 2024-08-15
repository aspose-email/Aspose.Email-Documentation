---
title: Managing Digitally Signed Messages
type: docs
weight: 100
url: /java/working-with-outlook-notes/
---

Aspose.Email implements the complete S/MIME email object algorithm. This gives the API complete power to add digital signatures to email messages, preserve them while converting messages between formats, remove them, etc.

## **Attach a Signature to an Email**

The [SecureEmailManager.attachSignature](https://reference.aspose.com/email/java/com.aspose.email/secureemailmanager/#attachSignature-com.aspose.email.MapiMessage-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-com.aspose.email.SignatureOptions-) method allows you to attach digital signatures to email messages. After attaching the signature, verify the results through properties like [IsSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--), [MessageClass](https://reference.aspose.com/email/java/com.aspose.email/knownpropertylist/#MESSAGE-CLASS), and attachment details.

You can provide a MailMessage or MapiMessage, a private certificate, and signature options to customize the signature attachment process with the [SignatureOptions](https://reference.aspose.com/email/java/com.aspose.email/signatureoptions/) class which enables users to specify various options for the signature attachment, including detached or non-detached signatures.

The following code sample will show you how to load a message from a file, attach a detached and non-detached digital signature using a private certificate, and then check if the signatures were attached successfully.

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

## **Preserving Signature when Converting from EML to MSG**

Aspose.Email preserves the digital signature when converting from EML to MSG. The following code snippet shows you how to convert from EML to MSG.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

// Load mail message
MailMessage message = MailMessage.load(dataDir + "Message.eml", new EmlLoadOptions());
// Save as MSG
message.save(dataDir + "ConvertEMLToMSG_out.msg", SaveOptions.getDefaultMsgUnicode());
~~~
## **Remove Signature from an Outlook Message File**

If you're facing the necessity to remove the signature from a message in a MAPI format, for example for compatibility purposes, Aspose.Email offers the [MapiMessage.removeSignature](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#removeSignature--) method and the [MapiMessage.isSigned](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isSigned--) property. 

The following code snippet shows how to load a MAPI message from a file, check if it is digitally signed, and if so, create a new message without the digital signature: 

```java
MapiMessage msg = MapiMessage.load(fileName);

if (msg.isSigned()) {
    MapiMessage unsignedMsg = msg.removeSignature();
}
```
## **Converting S/MIME Messages from MSG to EML**

Aspose.Email preserves the digital signature when converting from MSG to EML as shown in the following code snippet.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "outlook/";

MailMessage msg = MailMessage.load(dataDir + "message.eml");
MapiMessage mapi = MapiMessage.fromMailMessage(msg, new MapiConversionOptions(OutlookMessageFormat.Unicode));
// Save File to disk
mapi.save(dataDir + "ConvertMIMEMessagesFromMSGToEML_out.msg");
~~~

## **Decrypt an MSG File with Certificate**

If you have encrypted MAPI messages and need to decrypt them using the private key stored in a certificate, the following features of Aspose.Email can be useful:

- [MapiMessage.isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#isEncrypted--) - Gets a value indicating whether the message is encrypted.
- [MapiMessage.decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt--) - Decrypts this message (method searches the current user and computer My stores for the appropriate certificate and private key).
- [MapiMessage.decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Decrypts this message with certificate.

The following code snippet shows how to work with encrypted MAPI messages:

```java
X509Certificate2 privateCert = new X509Certificate2("privateCertFile", "password");
MapiMessage msg = MapiMessage.load("encrypted.msg");

if (msg.isEncrypted()) {
    MapiMessage decryptedMsg = msg.decrypt(privateCert);
    //MapiMessage decryptedMsg = msg.decrypt(/*byte[]*/rawPrivateCert, "password");
}
```
