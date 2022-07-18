---
title: Utility Features - SMTP Client
type: docs
weight: 30
url: /net/utility-features-smtp-client/
---

# Utility Features - SMTP Client
## **Listing Extension Servers using Smtp Client**
Aspose.Email's [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT, QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/methods/getcapabilities) method returns the supported extension types in the form of a string array.
### **Retrieving Server Extensions**
The following code snippet shows you how to retrieve server extensions.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-RetreiveServerExtensions-RetreiveSMTPServerExtensions.cs" >}}
## **Working with Signed Message**
Aspose.Email API provides the capability to create Signed messages using certificates. The [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/attachsignature/index) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class can be used to sign a message for saving or even sending it using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient).
### **Sign a Message**
The following code snippet shows you how to Sign a Message.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SignAMessage-SignAMessage.cs" >}}
### **Using Detached Certificate Option**
Web-based email clients may not be able to display body contents of a Signed message. This can be taken care of by detaching the certificate before sending it to web-based email clients. The detached flag in the overloaded method of [AttachSignature](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/attachsignature/index) can be used to achieve this. If set to **true**, the certificate is detached from the email and vice versa. To see Signed Message body in Web-based clients, you need to create [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) with detached signature. The following code snippet shows you how to use detached certificate option.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-UsingDetachedCertificate-UsingDetachedCertificate.cs" >}}
