---
title: Extracting Message Contents from Emails
ArticleTitle: Extracting Message Contents from Emails
type: docs
weight: 20
url: /python-net/extracting-message-contents-from-emails/
---


## **Displaying Email Information on Screen**
The MailMessage represents an email message and allows developers to access email message properties. The header information (discussed in Extracting Email Headers) can be extracted and manipulated in different ways. This article explains how to display selected email header information and the email body on screen. To Display Email Information on Screen , follow these steps:

- Create an instance of the MailMessage class.
- Load an email message into the MailMessage instance.
- Display the email content on screen.

The following code snippet shows you how to displaying email information on screen.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-DisplayEmailInformation-DisplayEmailInformation.py" >}}
## **Extracting Email Headers**
The email header represents an Internet and RFC defined standard set of header fields included in Internet email messages. An email header can be specified using the MailMessage class. Common header types are defined in the HeaderType class. It is a sealed class working like normal enumeration. To extract headers from an email, follow these steps:

1. Create an instance of the MailMessage class.
1. Load an email message in the instance of MailMessage class.
1. After an email message has been loaded, we will get its raw content.

The MailMessage class itself contains properties such as From, To, Cc, Subject and so on. These properties can be extracted from headers.

1. Display the raw content.

The following code snippet shows you how to extract email headers.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-ExtractingEmailHeaders-ExtractingEmailHeaders.py" >}}
## **Get Decoded Header Values**
The following code snippet shows you how to get decoded header values.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithMimeMessages-GetDecodedHeaderValues-GetDecodedHeaderValues.py" >}}
