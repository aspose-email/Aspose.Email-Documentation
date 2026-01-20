---
title: Create and Customize Email Messages Using Aspose.Email for C++
ArticleTitle: Create and Customize Email Messages Using Aspose.Email for C++
linktitle: Creating and setting contents of Emails
type: docs
weight: 10
url: /cpp/create-and-customize-email-messages/
description: .
keywords: c++ send email
---


**Aspose.Email for C++** provides the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class to create, customize, and save email messages in different formats. This class allows you to define essential properties such as sender, recipients, subject, and body, and supports saving messages in EML, MSG, and MHTML formats.


## **Create a New Email Message**

The following code sample demonstrates how to create and configure a new email message using Aspose.Email for C++.

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class.
2. Set message properties such as From, To, Cc, Subject, and HtmlBody.
3. Optionally, save the message in multiple formats (EML, MSG, MHTML, etc.).


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CreateNewMailMessage-CreateNewMailMessage.cpp" >}}


## **Using Friendly Names for Email Addresses**

A **friendly name** makes an email address more readable. For example, `John Smith <jsmith@domain.com>` instead of just `jsmith@domain`.com. 

You can associate friendly names with addresses when constructing an email using the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class.

The code sample below demonstrates how to add friendly names:

1. Create a new instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class.
2. Add `To`, `Cc`, and `Bcc` recipients with both an address and a friendly name.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ChangeEmailAddress-ChangeEmailAddress.cpp" >}}

## **Set Mail Body Content**

The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class allows you to define the email body in **HTML** format. You can also provide **alternate views** for different email clients using the [AlternateView](https://reference.aspose.com/email/cpp/class/aspose.email.alternate_view) class.


### **Setting HTML Body**

The following code sample demonstrates how to set the HTML content of the email message by assigning an HTML string to the [set_HtmlBody](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a8367bf6208557a5885c269d429209f7f) property. The use of this string as a message body indicates that the email will be sent with HTML formatting instead of plain text.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetHTMLBody-SetHTMLBody.cpp" >}}

### **Setting Alternate Text**

Some email clients cannot display HTML content. To ensure your message is readable for all recipients, you can add an alternate plain text version using the [AlternateView](https://reference.aspose.com/email/cpp/class/aspose.email.alternate_view) class. It allows you to include multiple versions of an email message in different formats. For example, if your main message body is HTML, you can also attach a plain text version as an alternative.

The code sample below demonstrates how to create an email message and add an alternate view containing plain text content to it.


{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SetAlternateText-SetAlternateText.cpp" >}}


The [AlternateView](https://reference.aspose.com/email/cpp/class/aspose.email.alternate_view) class also manages resources used within the email body:

* **LinkedResources** – a collection of embedded items (such as images or attachments) that are referenced by links in the message content.
* **set_BaseUri()** – defines the base URL used to resolve relative links or resource paths in the message body.





