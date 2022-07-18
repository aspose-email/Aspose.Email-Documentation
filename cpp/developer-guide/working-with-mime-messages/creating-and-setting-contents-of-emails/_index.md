---
title: Creating and setting contents of Emails in C++
linktitle: Creating and setting contents of Emails
type: docs
weight: 10
url: /cpp/creating-and-setting-contents-of-emails/
description: To create and set contents of email in C++, use MailMessage class that can create and save the mail message into different formats like EML, MSG and MHTML.
---

## **Create New Email Message**
The MailMessage class represents an email message and allows developers to create new email message. Basic email properties like From, To, Subject and body can be easily attached with the newly created mail message. Similarly we can save the mail message into different formats like EML, MSG and MHTML.

- Create an instance of the MailMessage class.
- Set mail message properties.
- Save mail message in different formats.

The following C++ code snippet shows you how to create a new email with different properties.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CreateNewMailMessage-CreateNewMailMessage.cpp" >}}

## **Changing email addresses to a friendly name**
The programming samples below demonstrate how to change email addresses to friendly names in an email message. A friendly name is a name that is more human-friendly than the email address, for example John Smith instead of js346@domain.com. When sending an email, we can associate a friendly name with an email address in the MailMessage class constructor.

To change email addresses to friendly names in an email message, follow these steps:

- Create an instance of the MailMessage class and specify email addresses in the **To** and **From** fields along with friendly names.
- Specify the Cc and Bcc email addresses along with friendly names by calling the MailMessage class constructor in the MailMessage instance.
- Create an instance of the SmtpClient class and send the email using the Send method.

The following code snippet shows you how to display Names for email addresses.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ChangeEmailAddress-ChangeEmailAddress.cpp" >}}

## **Set Mail Body**
The MailMessage class represents an email message. Instances of the MailMessage class are used to construct email messages that are transmitted to a SMTP server for delivery using the SmtpClient class. A mail body can be specified using the MailMessage class. An email can have multiple bodies. There are two types of mail bodies in MailMessage class:

- HTML body
- Text body

In addition to HtmlBody and TextBody, Aspose.Email has another two read-only properties related to mail body:

- IsBodyText: tells the user whether the body is text.
- IsBodyHtml: tells the user whether the body is HTML or plain text.

This article shows how to define plain text or HTML body text, set alternate text and encode the email body.

### **Setting HTML Body**
[HtmlBody](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) is used to specify the HTML content of a message body. HtmlBody must be enclosed between <html> </html> tags. The following code snippet shows you how to set HTML body.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetHTMLBody-SetHTMLBody.cpp" >}}

### **Setting Alternate Text**
Use the AlternateView class to specify copies of an email message in different format. For example, if you send a message in HTML, you might also want to provide a plain text version in case some of the recipients use email readers that cannot display HTML content. This class has two properties, LinkedResources and BaseUri, which are used to resolve URLs within the content of the email.

- LinkedResources is a collection of LinkedResources objects. When rendered, URLs within the email's content are first matched against the URLs in the Content Link of each LinkedResources object in the LinkedResources collection, and resolved.
- BaseUri is used by the mail reader to resolve relative URLs within the body, and also to resolve relative Content Link URLs, in the LinkedResources collection.

The following C++ code snippet shows you how to set alternate text.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetAlternateText-SetAlternateText.cpp" >}}
