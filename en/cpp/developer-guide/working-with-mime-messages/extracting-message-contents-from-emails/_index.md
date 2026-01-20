---
title: Read and Display Email Messages & Headers in C++
ArticleTitle: Read and Display Email Messages & Headers in C++
linktitle: Extracting Message Contents from Emails
type: docs
weight: 20
url: /cpp/read-display-email-messages-headers/
description: Learn how to load, view, and extract email content and headers from EML files with Aspose.Email for C++.
---


**Aspose.Email for C++** provides the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class, which represents an email message and allows developers to access and display its contents and headers. You can easily extract information such as sender, recipients, subject, body, and headers from an existing email file (EML).


## **Display Email Information**

Load an email file and display its key properties on the screen, such as the sender, recipients, subject, and body. The code sample below will show you how to display email information on the screen using Aspose.Email API.

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class.
2. Load an email message into the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) instance.
3. Display the desired properties (for example, From, To, Subject, and Body) on the console.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-DisplayEmailInformation-DisplayEmailInformation.cpp" >}}

> **Note:** For complete examples and data files, visit the [Aspose.Email for C++ GitHub repository](https://github.com/aspose-email/Aspose.Email-for-C).



## **Extract Email Headers**

An **email header** is a set of metadata fields that describe the message, including routing information, content type, encoding, and sender/recipient details.

Aspose.Email for C++ allows you to extract and work with these headers using the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class.

The most common header types are available through the [HeaderType](https://reference.aspose.com/email/cpp/class/aspose.email.header_type) class, which provides named constants for standard header fields.

The following code snippet shows how to **extract email headers**:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message/) class.
2. Load an email file into the instance.
3. Retrieve the header collection using the [get_Headers()](https://reference.aspose.com/email/cpp/class/aspose.email.mail_message#a0e0c441069f3971dcc6e456a2d4471a2) method.
4. Iterate through the collection to read or display header names and values.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-ExtractingEmailHeaders-ExtractingEmailHeaders.cpp" >}}


## **Get Decoded Header Values**

Some email headers may contain encoded text (for example, subject lines or custom headers using encoded words). You can easily retrieve a decoded value using the [GetDecodedValue()](https://reference.aspose.com/email/cpp/class/aspose.email.mime.header_collection#a2a41a5b3ca41346c25865d0419976a32) method of the [HeaderCollection](https://reference.aspose.com/email/cpp/class/aspose.email.mime.header_collection/) class.

The following code snippet shows you how to get decoded header values.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-EmailCPP-Email-GetDecodedHeaderValues-GetDecodedHeaderValue.cpp" >}}
