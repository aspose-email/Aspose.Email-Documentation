---
title: Utility Features - MailMessage
type: docs
weight: 50
url: /java/utility-features-mailmessage/
---

## **Encrypting and Decrypting Messages**

Aspose.Email provides facility to Encrypt and decrypt Email messages. This topic shows how an existing or new message can be loaded and encrypted using [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). The [encrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) and [decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt--) methods return the **MailMessage** object for the applied effects and needs to be taken care of while encrypting/decrypting messages. Encrypting and decrypting messages involves the following steps:

1. Create a new message or load an existing one
2. Encrypt the message using the certificate file
3. Send the message or save it
4. Decrypt the message as required

The following code snippet shows you how to encrypt and decrypt messages.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.java" >}}

### **Checking a Message for Encryption**

Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-byte---java.lang.String-) class allows checking a message if it is encrypted or not. The [isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isEncrypted--) property of **MailMessage** allows checking this as shown in the following code sample.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CheckMessageForEncryption-CheckMessageForEncryption.java" >}}

## **Message Encryption with X509Certificate**

Aspose.Email provides the API for working with Encrypted Messages with X509Certificate:

[MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class has the following methods to work with message encryption:

- public MailMessage [attachSignature(X509Certificate2 certificate, boolean detached)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-boolean-) - Creates a signed message.
- public MailMessage [attachSignature(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#attachSignature-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-) - Creates a signed message.
- public X509Certificate2[] [checkSignatureCert()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkSignatureCert--) - Checks signature exsisting MailMessage.
- public MailMessage [decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#decrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- public MailMessage [encrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2-)
- public MailMessage [encrypt(X509Certificate2[] certificates)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#encrypt-com.aspose.ms.System.Security.Cryptography.X509Certificates.X509Certificate2---)


## **Configure Locale Options for Aspose.Email**

You can use [LocaleOptions](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/) class in case of unrecognised default locale and set most appropriate locale for Aspose Email lib. It offers the following methods to perform the task:

- [getLocale()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#getLocale--) - Returns default Locale for Aspose.Email.
- [setLocale(Locale locale)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.util.Locale-) and [setLocale(String localeName)](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#setLocale-java.lang.String-) - Set default locale related for Aspose.Email.
- [clear()](https://reference.aspose.com/email/java/com.aspose.email/localeoptions/#clear--) - Clears default locale for Aspose.Email. Will be used locale default for Java.

The following code sample demonstrates how to load a mail message from a file using the specified locale settings:

```java
final Locale locale = new Locale("en", "DE");
Locale.setDefault(locale);

// set Locale for Aspose Email lib
LocaleOptions.setLocale("en-US");
// or
//LocaleOptions.setLocale(new Locale("en", "US"));

MailMessage.load("document.msg");
```
This code ensures that the application and the Aspose.Email library use the specified locales for handling language, country, and cultural conventions.

## **MailMessages Containing TNEF attachments**

Transport Neutral Encapsulation Format (TNEF) is a proprietary email attachment format used by Microsoft Outlook and Microsoft Exchange Server. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify the contents of them. The email can then be saved as a normal email or to the same format, preserving TNEF attachments. This article shows different code samples for working with messages containing TNEF attachments.

### **Reading a Message by Preserving TNEF Attachments**

The following code snippet shows you how to read a message by preserving TNEF attachments.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.java" >}}

### **Updating Resources in a TNEF Attachment and Preserving TNEF Format**

The following code snippet shows you how to update resources in a TNEF attachment and preserve the TNEF format.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-UpdateTNEFAttachments-UpdateTNEFAttachments.java" >}}

### **Adding New Attachments to Main Message Containing TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-AddNewAttachmentToMessageContainingTNEF.java" >}}

### **Creating TNEF EML from MSG**

Outlook MSGs sometimes contain information such as tables and text styles that may get disturbed if these are converted to EML. Creating TNEF messages from such MSG files allows us to retain the formatting and even send such messages via the email clients retaining the formatting. 

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreatingTNEFEMLFromMSG.java" >}}

To create the TNEF, the following sample code can be used.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-CreateTNEF.java" >}}

### **Detect if a Message is TNEF**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-TNEFAttachment-DetectIfAMessageIsTNEF.java" >}}

## **Processing Bounced Messages**

It is very common that a message sent to a recipient may bounce for any reason such as an invalid recipient address. Aspose.Email API has the capability to process such a message for checking if it is a bounced email or a regular email message. The [CheckBounced](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#checkBounced--) method of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class returns a valid result if the email message is a bounced email.

This article shows the usage of [BounceResult](https://reference.aspose.com/email/java/com.aspose.email/bounceresult/) class that provides the capability of checking if a message is a bounced email. It further gives detailed information about the recipients, action taken and the reason for the notification.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ProcessBouncedMessages-.java" >}}

## **Ignore exceptions**

The library offers an [ExceptionManager](https://reference.aspose.com/email/java/com.aspose.email/exceptionmanager/) class to implement ignore exceptions ability into your application functionality. The code snippet below demonstrates how to set a callback to handle exceptions:

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
Or use an **alternative**:

```java
 ExceptionManager.setIgnoreAll(true);
```
Also, you can set a callback for ignored **exceptions log**:

```java
ExceptionManager.setIgnoreExceptionsLogHandler( new IgnoreExceptionsLogCallback() {

   public void invoke(String message) {

        System.out.println("=== EXCEPTION IGNORED === " + message);

   }

});
```
The user will be notified, that the exception can be ignored by an error message. For example:

Exception in message:

```java
AsposeArgumentException: properties should not be empty.
```

If you want to ignore an exception and want to proceed further then you can use:
```java
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")

Invalid TNEF Attachment will be interpreted as regular attachment.
```

## **Bayesian Spam Analyzer**

Aspose.Email provides the facility of e-mail filtering using the Bayes spam analyzer. It provides the [SpamAnalyzer](https://reference.aspose.com/email/java/com.aspose.email/spamanalyzer/) class for this purpose. This article shows how to train the filter to distinguish between the spam and regular emails based on the words database.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-BayesianSpamAnalyzer-.java" >}}

## **Obtaining Preamble and Epilogue from EML Messages**

In the MIME format, the *preamble* is the text that appears after the headers and before the first multipart boundary. The *epilogue* is the text that appears after the last boundary and before the end of the message. This text is usually not visible to users in mail readers, but some MIME implementations may use it to insert notes for recipients who read the message using non-MIME-compliant programs. 

The following code snippet shows how to obtain preamble and epilogue from an EML message which can be achieved with the corresponding methods of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class:

- [setPreamble(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setPreamble-java.lang.String-) - Gets or sets a preamble text.
- [setEpilogue(String value)](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#setEpilogue-java.lang.String-) - Gets or sets an epilogue text.

```java
// Gets or sets a preamble text.
public String getPreamble, setPreamble

// Gets or sets an epilogue text.
public String getEpilogue, setEpilogue
```

