---
title: Extracting Message Contents from Emails
type: docs
weight: 30
url: /java/extracting-message-contents-from-emails/
---

## **Displaying Email Information on Screen**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate()) represents an email message and allows developers to access email message properties. The header information (discussed in [Extracting Email Headers](#extracting-email-headers)) can be extracted and manipulated in different ways. This article explains how to display selected email header information and the email body on screen.

1. Create an instance of the **MailMessage**.
2. Load an email message into the **MailMessage** instance.
3. Display the email content on the screen.

The code below demonstrates how to load an email message and display its contents - from, to, subject and email body - on screen.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-DisplayEmailInformation-DisplayEmailInformation.java" >}}

### **Getting Message Date Time**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class can be used to retrieve message date in UTC or local timezone. This information can be summarized as follow:

1. [MailMessage.getDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getDate--) - returns date in UTC
1. [MailMessage.getLocalDate()](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getLocalDate--) - returns date in local TimeZone
2. [MailMessage.isLocalDate](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#isLocalDate--) Returns **true**, if **MailMessage.getDate()** is in the local timezone

## **Extracting Email Headers**

The email header represents an Internet and RFC defined standard set of header fields included in Internet email messages. An email header can be specified using the [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class. Common header types are defined in the [HeaderType](https://reference.aspose.com/email/java/com.aspose.email/headertype/) class. It is a sealed class working like normal enumeration.

To extract headers from an email, follow these steps:

1. Create an instance of the **MailMessage** class.
2. Load an email message in the instance of **MailMessage** class.
3. After an email message has been loaded, we will get its raw content. The **MailMessage** class itself contains properties such as From, To, Cc, Subject and so on. These properties can be extracted from headers.
4. Display the raw content.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-ExtractingEmailHeaders.java" >}}

## **Get Decoded Header Values**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-EmailHeaders-GetDecodedHeaderValueFromHeaderCollection.java" >}}

## **Get and Modify the Linked Resource Disposition Header**

The linked resource can be accessed and manipulated programmatically in the email message object. The [getContentDisposition()](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/#getContentDisposition--) method of the [LinkedResource](https://reference.aspose.com/email/java/com.aspose.email/linkedresource/) class gets the Content-Disposition header. The code sample below demonstrates how to access and modify the filename of the linked resource:

```java
MailMessage eml = MailMessage.load(fileName);
eml.getLinkedResources().get_Item(0).getContentDisposition().setFileName("changed.png");
```
## **Get HTML body as plain text**

The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class provides the feature to extract the HTML body of the message as plain text. The **MailMessage** class provides a [GetHtmlBodyText](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/#getHtmlBodyText-boolean-) method that returns the HTML body in plain text. The **GetHtmlBodyText** method accepts a boolean parameter that indicates whether the body should contain URLs or not. Passing the parameter as true indicates that the HTML body should contain URLs.

The following code snippet demonstrates the use of **GetHtmlBodyText** method to extract the HTML body of the email as plain text.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-GetHTMLBodyAsPlainText-1.java" >}}
