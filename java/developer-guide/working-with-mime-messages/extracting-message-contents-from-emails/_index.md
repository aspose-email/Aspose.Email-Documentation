---
title: Extracting Message Contents from Emails
type: docs
weight: 30
url: /java/extracting-message-contents-from-emails/
---

## **Displaying Email Information on Screen**
The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) represents an email message and allows developers to access email message properties. The header information (discussed in [Extracting Email Headers](#extracting-email-headers)) can be extracted and manipulated in different ways. This article explains how to display selected email header information and the email body on screen.

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class.
1. Load an email message into the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) instance.
1. Display the email content on the screen.

The code below demonstrates how to load an email message and display its contents - from, to, subject and email body - on screen.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayEmailInformation-DisplayEmailInformation.java" >}}
### **Getting Message Date Time**
The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class can be used to retrieve message date in UTC or local timezone. This information can be summarized as follow:

1. [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) - returns date in UTC
1. [MailMessage.getLocalDate()](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getLocalDate\(\)) - returns date in local TimeZone
1. [MailMessage.isLocalDate](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#isLocalDate\(\)) Returns **true**, if [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) is in the local timezone
## **Extracting Email Headers**
The email header represents an Internet and RFC defined standard set of header fields included in Internet email messages. An email header can be specified using the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class. Common header types are defined in the [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype) class. It is a sealed class working like normal enumeration.

To extract headers from an email, follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class.
1. Load an email message in the instance of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class.
1. After an email message has been loaded, we will get its raw content.
   The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class itself contains properties such as From, To, Cc, Subject and so on. These properties can be extracted from headers.
1. Display the raw content.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-ExtractingEmailHeaders.java" >}}
## **Get Decoded Header Values**


{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-GetDecodedHeaderValueFromHeaderCollection.java" >}}
## **Get HTML body as plain text**
The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class provides the feature to extract the HTML body of the message as plain text. The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getDate\(\)) class provides a [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getHtmlBodyText\(boolean\)) method that returns the HTML body in plain text. The [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getHtmlBodyText\(boolean\)) method accepts a boolean parameter that indicates whether the body should contain URLs or not. Passing the parameter as true indicates that the HTML body should contain URLs.

The following code snippet demonstrates the use of [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/MailMessage#getHtmlBodyText\(boolean\)) method to extract the HTML body of the email as plain text.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-GetHTMLBodyAsPlainText-1.java" >}}
