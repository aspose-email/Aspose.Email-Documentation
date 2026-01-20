---
title: Extracting Email Information
ArticleTitle: Extracting Email Information
type: docs
weight: 20
url: /python-net/extracting-email-information/
---


## **Displaying Email Metadata**

The `MailMessage` represents an email message and allows developers to access its properties. The header information can be extracted and manipulated in different ways. This article explains how to display selected email header information and the email body on the screen. To display email information on the screen, follow these steps:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class.
- Load an email message into the `MailMessage` instance.
- Display the email content on the screen.

The following code snippet shows you how to display email information on the screen:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayEmailInformation-DisplayEmailInformation.py" >}}

## **Extracting Email Headers**

The email header represents an Internet and RFC defined standard set of header fields included in email messages. An email header can be specified using the MailMessage class. Common header types are defined in the [HeaderType](https://reference.aspose.com/email/python-net/aspose.email/headertype/) class. It is a sealed class working like typical enumeration. To extract headers from an email, follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class.
1. Load an email message in the instance of [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class.
1. After an email message has been loaded, we will get its raw content.

The [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class itself contains properties such as From, To, Cc, Subject and so on. These properties can be extracted from headers.

The following code snippet shows you how to extract email headers:



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractingEmailHeaders-ExtractingEmailHeaders.py" >}}

## **Decoding Header Values**

The following code snippet shows you how to get decoded header values.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-GetDecodedHeaderValues-GetDecodedHeaderValues.py" >}}
