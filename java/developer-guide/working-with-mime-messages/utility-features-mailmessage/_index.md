---
title: Utility Features - MailMessage
type: docs
weight: 50
url: /java/utility-features-mailmessage/
---

## **Encrypting and Decrypting Messages**
Aspose.Email provides facility to Encrypt and decrypt Email messages. This topic shows how an existing or new message can be loaded and encrypted using [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage). The encrypt() and [decrypt()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage#decrypt\(\)) methods return the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) object for the applied effects and needs to be taken care of while encrypting/decrypting messages. Encrypting and decrypting messages involves the following steps:

1. Create a new message or load an existing one
1. Encrypt the message using the certificate file
1. Send the message or save it
1. Decrypt the message as required

The following code snippet shows you how to encrypt and decrypt messages.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EncryptAndDecryptMessage-EncryptAndDecryptMessage.java" >}}
### **Checking a Message for Encryption**
Aspose.Email [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) class allows checking a message if it is encrypted or not. The [isEncrypted](https://reference.aspose.com/email/java/com.aspose.email/mailmessage#isEncrypted\(\)) property of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) allows checking this as shown in the following code sample.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-CheckMessageForEncryption-CheckMessageForEncryption.java" >}}
## **MailMessages Containing TNEF attachments**
Transport Neutral Encapsulation Format (TNEF) is a proprietary email attachment format used by Microsoft Outlook and Microsoft Exchange Server. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify the contents of them. The email can then be saved as a normal email or to the same format, preserving TNEF attachments. This article shows different code samples for working with messages containing TNEF attachments.
### **Reading Message by Preserving TNEF Attachments**
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
## **Processing of Bounced Messages**
It is very common that a message sent to a recipient may bounce for any reason such as an invalid recipient address. Aspose.Email API has the capability to process such a message for checking if it is a bounced email or a regular email message. The [CheckBounced](https://reference.aspose.com/email/java/com.aspose.email/mailmessage#checkBounced\(\)) method of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage) class returns a valid result if the email message is a bounced email.

This article shows the usage of [BounceResult](https://reference.aspose.com/email/java/com.aspose.email/BounceResult) class that provides the capability of checking if a message is a bounced email. It further gives detailed information about the recipients, action taken and the reason for the notification.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ProcessBouncedMessages-.java" >}}
## **Bayesian Spam Analyzer**
Aspose.Email provides the facility of e-mail filtering using the Bayes spam analyzer. It provides the [SpamAnalyzer](https://reference.aspose.com/email/java/com.aspose.email/SpamAnalyzer) class for this purpose. This article shows how to train the filter to distinguish between the spam and regular emails based on the words database.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-BayesianSpamAnalyzer-.java" >}}
