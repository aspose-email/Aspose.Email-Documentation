---
title: Utility Features - MailMessage
type: docs
weight: 50
url: /net/utility-features-mailmessage/
---


## **Encrypting and Decrypting Messages**

Aspose.Email provides the facility to encrypt and decrypt email messages using the X509Certificates. This article shows how an existing or new message can be loaded and encrypted using [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/). The [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/encrypt/#encrypt/) and [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/decrypt/#decrypt/) methods return a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) object for the applied effects and need to be taken care of while encrypting/decrypting messages. Encrypting and decrypting messages involves the following steps:

1. Create a new message or load an existing one
1. Load an encryption certificate using the X509Certificate object
1. Encrypt the message using the certificate
1. Send the message or save it
1. Decrypt the message as required

The following code snippet shows you how to encrypt and decrypt messages.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}

### **Check a Message for Encryption**

Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class allows you to check if a message is encrypted or not. The [IsEncrypted ](https://reference.aspose.com/email/net/aspose.email/mailmessage/isencrypted/)property of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) allows you to check this as shown in the following code sample.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}

## **Email messages containing TNEF attachments**

Transport Neutral Encapsulation Format (TNEF) is a proprietary email attachment format used by Microsoft Outlook and Microsoft Exchange Server. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify the contents of the attachment. The email can then be saved as a normal email or to the same format, preserving TNEF attachments. This article shows different code samples for working with messages containing TNEF attachments. This article also shows how to create TNEF EML files from Outlook MSG files.

### **Read a Message Preserving TNEF Attachments**

The following code snippet shows you how to read a message preserving TNEF attachments.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}

### **Read a Message without Preserving TNEF Attachments**

The following code snippet shows you how to read a message without preserving TNEF attachments.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}

### **Updating Resources in a TNEF Attachment and Preserving TNEF Format**

The following code snippet shows you how to update resources in a TNEF attachment and preserve TNEF format.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}

### **Adding New Attachments to the Main Message Containing TNEF**

The following code snippet shows you how to add new attachments to the main message containing TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}

### **Creating TNEF EML from MSG**

Outlook MSGs sometimes contain information such as tables and text styles that may get disturbed if these are converted to EML. Creating TNEF messages from such MSG files allows to retain the formatting and even send such messages via the email clients retaining the formatting. The [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/convertastnef/) property is used to achieve this. The following code snippet shows you how to create TNEF EML from MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}

For creating the TNEF, the following sample code can be used.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}

### **Detect If a Message is TNEF**

The following code snippet shows you how to detect if a message is TNEF.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}

### **Check whether Attachment is in TNEF format**

The [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/#attachmentistnef-property) property allows to detect whether the message attachment is TNEF formatted message.

```cs
var eml = MailMessage.Load(fileName);

foreach (attachment in eml.Attachments)
{
    Console.WriteLine($"Is Attachment TNEF?: {attachment.IsTnef}");
}
```

## **Processing Bounced Messages**

It is very common that a message sent to a recipient may bounce for any reason such as an invalid recipient address. Aspose.Email API has the capability to process such a message for checking if it is a bounced email or a regular email message. The [CheckBounced](https://reference.aspose.com/email/net/aspose.email/mailmessage/checkbounced/#checkbounced) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class returns a valid result if the email message is a bounced email. This article shows the usage of the [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/) class that provides the capability of checking if a message is a bounced email. It further gives detailed information about the recipients, action taken and the reason for the notification. The following code snippet shows you how to process bounced messages.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckBouncedMessage-CheckBouncedMessage.cs" >}}


## **Bayesian Spam Analyzer**

Aspose.Email provides email filtering using a Bayesian spam analyzer. It provides the [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) class for this purpose. This article shows how to train the filter to distinguish between spam and regular emails based on the words database.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-BayesianSpamAnalyzer-BayesianSpamAnalyzer.cs" >}}

## **Obtaining preamble and epilogue from eml messages**

An email message may contain some hidden information as a plain text before the message body (i.e. preamble) or after the body (i.e. epilogue). It is typically some additional information or context to the recipient before or after they read the main content of the email. You can obtain this information using [MailMessage.Preamble](https://reference.aspose.com/email/net/aspose.email/mailmessage/preamble/) or/and [MailMessage.Epilogue](https://reference.aspose.com/email/net/aspose.email/mailmessage/epilogue/#mailmessageepilogue-property) properties respectively. 

The following code snippet shows how to obtain the preamble and epilogue texts:

```cs
// Gets or sets a preamble text.
public string Preamble

// Gets or sets an epilogue text.
public string Epilogue
```
