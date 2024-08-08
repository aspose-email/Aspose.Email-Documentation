---
title: Extracting Message Contents from Emails in C++
linktitle: Extracting Message Contents from Emails
type: docs
weight: 20
url: /cpp/extracting-message-contents-from-emails/
description: Using C++ Email Parser Library, you can access email message properties, header information and manipulate it in different ways programmatically.
---

## **Displaying Email Information on Screen**
The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) represents an email message and allows developers to access email message properties. The header information (discussed in Extracting Email Headers) can be extracted and manipulated in different ways. This article explains how to display selected email header information and the email body on screen. To Display Email Information on the screen, follow these steps:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
- Load an email message into the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) instance.
- Display the email content on the screen.

The following C++ code snippet shows you how to display email information on the screen.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-DisplayEmailInformation-DisplayEmailInformation.cpp" >}}

## **Extracting Email Headers**
The email header represents an Internet and RFC defined standard set of header fields included in Internet email messages. An email header can be specified using the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class. Common header types are defined in the HeaderType class. It is a sealed class working like normal enumeration. To extract headers from an email, follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
1. Load an email message in the instance of [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class.
1. After an email message has been loaded, we will get its raw content.

The [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message) class itself contains properties such as From, To, Cc, Subject and so on. These properties can be extracted from headers.

1. Display the raw content.

The following  C++ code snippet shows you how to extract email headers.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-ExtractingEmailHeaders-ExtractingEmailHeaders.cpp" >}}

## **Get Decoded Header Values**
The following code snippet shows you how to get decoded header values.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-GetDecodedHeaderValues-GetDecodedHeaderValue.cpp" >}}
