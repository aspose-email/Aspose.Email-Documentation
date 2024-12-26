---
title: Email Security and Encryption in .NET
ArticleTitle: Email Security and Encryption
type: docs
weight: 50
url: /net/encrypt-decrypt-sign-email-messages/
---


## **Encrypt/Decrypt Messages**

Aspose.Email provides the facility to encrypt and decrypt email messages using the X509Certificates. This article shows how an existing or new message can be loaded and encrypted using [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). The [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/encrypt/#encrypt/) and [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/decrypt/#decrypt/) methods return a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object for the applied effects and need to be taken care of while encrypting/decrypting messages. Encrypting and decrypting messages involves the following steps:

1. Create a new message or load an existing one
1. Load an encryption certificate using the X509Certificate object
1. Encrypt the message using the certificate
1. Send the message or save it
1. Decrypt the message as required

The following code snippet shows you how to encrypt and decrypt messages.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}

### **Verify Message Encryption**

Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class allows you to check if a message is encrypted or not. The [IsEncrypted](https://reference.aspose.com/email/net/aspose.email/mailmessage/isencrypted/)property of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) allows you to check this as shown in the following code sample.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}

## **Checking Secure Emails Signature**

The [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) class allows you to check the signature of secure MailMessage objects.

The [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) class stores the results of the check.

The following methods of the [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) class and a code snippet will enable you to process a signature:

- [SecureEmailManager.CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) method.
- [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) method.
- [SecureEmailManager.CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_2) method.

```cs
var eml = MailMessage.Load(fileName);
var result = new SecureEmailManager().CheckSignature(eml);

var certFileName = "cert.pfx";
var cert = new X509Certificate2(certFileName, "pass");
var eml = MailMessage.Load(fileName);
var store = new X509Store();
store.Open(OpenFlags.ReadWrite);
store.Add(cert);
store.Close();

var result = new SecureEmailManager().CheckSignature(eml, cert, store);
```

## **Sign Emails with DKIM**

> **_NOTE:_** The feature is accessible only for the library versions targeting .NET Framework. Versions, targeting .NET Core, do not have this feature.

Aspose.Email allows signing Email with DKIM (DomainKeys Identified Mail). This lets an organization take responsibility for a message that is in transit ([More Info](https://www.dkim.org/)). DKIM adds a digital signature to the email message headers that can be validated by recipients. The public key of the sender enables the receiver to verify that the signature matches the message's contents. The [DKIMSign](https://reference.aspose.com/email/net/aspose.email/mailmessage/dkimsign/#dkimsign) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class is used to set the cryptographic and signature information for signing the message. The following code snippet shows you how to sign emails with DKIM.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Some subject", "Some body text");

string privateKeyFile = "key2.pem";
RSACryptoServiceProvider rsa = PemReader.GetPrivateKey(privateKeyFile);
DKIMSignatureInfo signInfo = new DKIMSignatureInfo("test", "somedomain.com");

var signedEml = eml.DKIMSign(rsa, signInfo);
```