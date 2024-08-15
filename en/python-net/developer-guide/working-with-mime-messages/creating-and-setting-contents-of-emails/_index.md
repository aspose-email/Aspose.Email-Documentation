---
title: Creating and setting contents of Emails
type: docs
weight: 10
url: /python-net/creating-and-setting-contents-of-emails/
---


## **Create New Email Message**
The MailMessage class represents an email message and allows developers to create new email message. Basic email properties like From, To, Subject and body can be easily attached with the newly created mail message. Similarly we can save the mail message into different formats like EML, MSG and MHTML.

- Create an instance of the MailMessage class.
- Set mail message properties.
- Save mail message in different formats.

The following code snippet shows you how to create a new email with different properties.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-CreateNewMailMesssage-CreateNewMailMesssage.py" >}}
## **Specifying Multiple Recipients**
The MailMessage represents an email message. Instances of the MailMessage class are used to construct email messages that are transmitted to an SMTP server using the SmtpClient class. This topic demonstrates how to specify more than one email addresses. Email addresses can be specified using the MailMessage class. The email addresses used in the MailMessage class are:

- **To** - Recipient addresses can be specified in the 'To' field. The 'To' field recipients are the primary message audience. There can be more then one recipient address
- **Cc** - CC stands for "carbon copy", or "courtesy copy", and lets you add email recipients who need to see the email but who are not necessarily expected to act on it. Managers, for example, or members of your team who need to be aware of a conversation. With Aspose.Email, CC addresses can be specified in your code. This way, automated emails, or all emails to a specific address, can be copied to relevant personnel.
- **Bcc** - Bcc, blind carbon copy, lets you send an email to a recipient that is hidden from other recipients. Where a CC appears in the email information that the main recipients see, a Bcc doesn't. It is meant for hidden notification. 

To specify multiple email addresses in an email message, follow these steps:

1. Create an instance of the MailMessage class.
1. Specify the From and multiple To, Cc and Bcc addresses using the MailMessage instance.
1. Create an instance of the SmtpClient class and send the email using the Send method.

The code sample below shows how multiple To, CC and BCC addresses can be specified.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SpecifyRecipientAddresses-SpecifyRecipientAddresses.py" >}}
## **Changing email addresses to a friendly name**
The programming samples below demonstrate how to change email addresses to friendly names in an email message. A friendly name is a name that is more human-friendly than the email address, for example John Smith instead of js346@domain.com. When sending an email, we can associate a friendly name with an email address in the MailMessage class constructor.

To change email addresses to friendly names in an email message, follow these steps:

- Create an instance of the MailMessage class and specify email addresses in the **To** and **From** fields along with friendly names.
- Specify the Cc and Bcc email addresses along with friendly names by calling the MailMessage class constructor in the MailMessage instance.
- Create an instance of the SmtpClient class and send the email using the Send method.

The following code snippet shows you how to display Names for email addresses.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ChangeEmailAddress-ChangeEmailAddress.py" >}}
## **Set Mail Body**
The MailMessage class represents an email message. Instances of the MailMessage class are used to construct email messages that are transmitted to a SMTP server for delivery using the SmtpClient class. A mail body can be specified using the MailMessage class. An email can have multiple bodies. There are two types of mail bodies in MailMessage class:

- HTML body
- Text body

In addition to HtmlBody and TextBody, Aspose.Email has another two read-only properties related to mail body:

- IsBodyText: tells the user whether the body is text.
- IsBodyHtml: tells the user whether the body is HTML or plain text.

This article shows how to define plain text or HTML body text, set alternate text and encode the email body.
### **Setting HTML Body**
HtmlBody is used to specify the HTML content of a message body. HtmlBody must be enclosed between <html> </html> tags. The following code snippet shows you how to set HTML body.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-SetHTMLBody-SetHTMLBody.py" >}}
### **Setting Alternate Text**
Use the AlternateView class to specify copies of an email message in different format. For example, if you send a message in HTML, you might also want to provide a plain text version in case some of the recipients use email readers that cannot display HTML content. This class has two properties, LinkedResources and BaseUri, which are used to resolve URLs within the content of the email.

- LinkedResources is a collection of LinkedResources objects. When rendered, URLs within the email's content are first matched against the URLs in the Content Link of each LinkedResources object in the LinkedResources collection, and resolved.
- BaseUri is used by the mail reader to resolve relative URLs within the body, and also to resolve relative Content Link URLs, in the LinkedResources collection.

The following code snippet shows you how to set alternate text.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-AlternateText-AlternateText.py" >}}
## **MailMessage Features**
The [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class represents the content of an email message. Instances of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class are used to construct an email message that is transmitted to a SMTP server for delivery using the [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) class. This article shows how to use [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class utility features for controlling the following email features:

- **Date and time** - Through the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class Date property we get or set an email's date and time.
- **Message priority** - The [MailPriority](https://apireference.aspose.com/email/net/aspose.email/mailpriority) class specifies priority levels for sending an email message. It can be low, normal or high. Priority influences transmission speed and delivery.
- **Message sensitivity** - The [MailSensitivity](https://apireference.aspose.com/email/net/aspose.email/mailsensitivity) class specifies five levels of sensitivity.
- **Delivery notification** - Delivery notifications let senders know that the email they sent have been delivered to the recipient's inbox.

By default, the date is the actual date that the message was sent, and time is the time it was sent, as displayed by Microsoft Outlook. However, the real email delivery time is added by the SMTP server itself in the mail header. For example, below is a common mail header, where Date sets the field Date.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-DateAndTime-DateAndTime.py" >}}



The code snippet below illustrates how each of the feature discussed above can be used.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-MailMessageFeatures-MailMessageFeatures.py" >}}
## **Requesting a Read Receipt**
The programming samples below show how you can request a read receipt. The [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) Enumeration property describes the delivery notification options for an email. To request a read receipt after sending an email, follow these steps:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class.
1. Specify the sender, receiver and HTML body for the email in the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instance.
1. Specify the [DeliveryNotificationOptions](https://apireference.aspose.com/email/net/aspose.email/deliverynotificationoptions) in other [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instances.
1. Create an instance of the [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) class and send the email using Send method.

Read receipt requests may not be always honored because:

- A mail client may not implement that functionality.
- The end user may have that functionality turned off.
- The end user may choose not to send one.

The following code snippet shows you how to request a read receipt.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-RequestReadReceipt-RequestReadReceipt.py" >}}
## **Set Email Headers**
Email headers represent an Internet standard and RFC define header fields which are included in Internet email messages. An email header can be specified using the MailMessage class. Common header types are defined in the HeaderType class. It is a sealed class working like a normal enumeration.

Normally an email header contains these fields:

- To: Recipient addresses can be specified in the **To** field. The **To** field recipients are the message's primary audience. There can be more then one recipient addresses.
- From: This field presents the email address of the message sender.
- Cc: Allows users to send a message as a "Carbon Copy" or "Courtesy Copy". That is, the receiver is not expected to reply or act. Typically, supervisory personnel are notified with CC.
- Bcc: It stands for Blind Carbon Copy, refers to the practice of sending a message to multiple recipients in such a way that what they receive does not contain the complete list of recipients. It is meant for hidden notification.
- ReplyTo: This header field is meant to indicate where the sender wants replies to go.
- Subject: Title, heading, subject. Often used as thread indicator for messages replying to or commenting on other messages.
- Date: This header specifies a date (and time). Normally this is the date at which message was composed and sent.
- XMailer: Information about the client software of the originator. Example: X-Mailer: Aspose.Email. XMailer is used by mail clients. Different mail clients will have different XMailer values. MS Outlook's XMailer value is Microsoft Office Outlook, Build 11.0.5510. It is ignored by the email receiver or email reader.

Normally, an email header looks something like this:

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: guangzhou@guangzhoo.com

Subject: test mail

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

```

To customize an email header, follow these steps:

- Create an instance of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class.
- Specify To, From, CC, Bcc, ReplyTo, Subject, Date & XMailer using an instance of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage).
- Create an instance of the [MimeHeader](https://apireference.aspose.com/email/net/aspose.email.mime/mimeheader) class and specify secret header.
- Add the secret header to the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instance.

The following code snippet shows you how to set email headers.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SetEmailHeaders-SetEmailHeaders.py" >}}



The above code snippet produces an email header in the following format. This can be observed by opening the resultant file "MsgHeaders.msg" in Microsoft Outlook and then view the Properties.

``` cs

 Reply-To: reply@reply.com

From: sender@sender.com

To: receiver1@receiver.com

CC: receiver2@receiver.com

BCC: receiver3@receiver.com

Subject: test mail

Date: 6 Mar 2006 8:2:2 +0800

X-Mailer: Aspose.Email

secret-header: mystery

```
### **Insert Header at Specific Location**
The [Add](https://apireference.aspose.com/email/net/aspose.email.mime.headercollection/add/methods/1) method of [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection) class inserts the header at the end of the collection. However, it may sometimes be necessary to insert a header at a specific location. In such case, the [Add](https://apireference.aspose.com/email/net/aspose.email.mime.headercollection/add/methods/1) method won't be of help. To achieve this, use the [Insert](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection/methods/insert) method of the [HeadersCollection](https://apireference.aspose.com/email/net/aspose.email.mime/headercollection). If collection contains headers with the same name, this header will be inserted before other headers with the same name. The following code snippet shows you how to insert header at specific location.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-InsertHeaderAtSpecificLocation-InsertHeaderAtSpecificLocation.py" >}}
### **Adding Custom headers to email**
The programming samples below demonstrates how to specify a custom header in an email message. An email header can be specified using the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class. To specify a custom header in an email message, please follow these steps:

1. Create an instance of the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) class.
1. Specify the to, from and subject values using the MailMessage instance.
1. Add the secret header into the [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) instance.
1. Create an instance of the SmtpClient class and send the email using the Send method.

The following code snippet shows you how to add custom headers to email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SpecifyCustomHeader-SpecifyCustomHeader.py" >}}
