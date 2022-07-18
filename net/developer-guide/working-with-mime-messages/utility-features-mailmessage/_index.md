---
title: Utility Features - MailMessage
type: docs
weight: 50
url: /net/utility-features-mailmessage/
---


## **Encrypting and Decrypting Messages**
Aspose.Email provides the facility to encrypt and decrypt email messages using the X509Certificates. This article shows how an existing or new message can be loaded and encrypted using [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage). The [Encrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/encrypt/index) and [Decrypt()](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/decrypt/index) methods return a [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) object for the applied effects and need to be taken care of while encrypting/decrypting messages. Encrypting and decrypting messages involves the following steps:

1. Create a new message or load an existing one
1. Load an encryption certificate using the X509Certificate object
1. Encrypt the message using the certificate
1. Send the message or save it
1. Decrypt the message as required

The following code snippet shows you how to encrypt and decrypt messages.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.cs" >}}
### **Checking a Message for Encryption**
Aspose.Email [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class allows checking if a message is encrypted or not. The [IsEncrypted ](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/isencrypted)property of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) allows checking this as shown in the following code sample.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckMessageForEncryption-CheckMessageForEncryption.cs" >}}
## **Email messages containing TNEF attachments**
Transport Neutral Encapsulation Format (TNEF) is a proprietary email attachment format used by Microsoft Outlook and Microsoft Exchange Server. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify the contents of the attachment. The email can then be saved as a normal email or to the same format, preserving TNEF attachments. This article shows different code samples for working with messages containing TNEF attachments. This article also shows working with creating TNEF EML files from Outlook MSG files.
### **Reading Message by Preserving TNEF Attachments**
The following code snippet shows you how to read a message by preserving TNEF attachments.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cs" >}}
### **Reading Message without Preserving TNEF Attachments**
The following code snippet shows you how to read a message without preserving TNEF attachments.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadingMessageByPreservingTNEFAttachments-ReadingMessageByPreservingTNEFAttachments.cs" >}}
### **Updating Resources in a TNEF Attachment and Preserving TNEF Format**
The following code snippet shows you how to updating resources in a TNEF attachment and preserving TNEF format.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-UpdateTNEFAttachments-UpdateTNEFAttachments.cs" >}}
### **Adding New Attachments to Main Message Containing TNEF**
The following code snippet shows you how to add new attachments to the main message containing TNEF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-AddNewAttachments-AddNewAttachments.cs" >}}
### **Creating TNEF EML from MSG**
Outlook MSGs sometimes contain information such as tables and text styles that may get disturbed if these are converted to EML. Creating TNEF messages from such MSG files allows to retain the formatting and even send such messages via the email clients retaining the formatting. The [MailConversionOptions.ConvertAsTnef](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/properties/convertastnef)[ ](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/properties/convertastnef)property is used to achieve this. The following code snippet shows you how to create TNEF EML from MSG.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEFEMLFromMSG-CreateTNEFEMLFromMSG.cs" >}}



For creating the TNEF, the following sample code can be used.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CreateTNEF-CreateTNEF.cs" >}}
### **Detect If a Message is TNEF**
The following code snippet shows you how to detect If a message is TNEF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DetectMessageIsTNEF-DetectMessageIsTNEF.cs" >}}
## **Processing of Bounced Messages**
It is very common that a message sent to a recipient may bounce for any reason such as an invalid recipient address. Aspose.Email API has the capability to process such a message for checking if it is a bounced email or a regular email message. The [CheckBounced](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/checkbounced) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class returns a valid result if the email message is a bounced email. This article shows the usage of the [BounceResult](https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult) class that provides the capability of checking if a message is a bounced email. It further gives detailed information about the recipients, action taken and the reason for the notification. The following code snippet shows you how to process bounced messages.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-CheckBouncedMessage-CheckBouncedMessage.cs" >}}
## **Bayesian Spam Analyzer**
Aspose.Email provides email filtering using a Bayesian spam analyzer. It provides the [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer) class for this purpose. This article shows how to train the filter to distinguish between spam and regular emails based on the words database.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-BayesianSpamAnalyzer-BayesianSpamAnalyzer.cs" >}}
