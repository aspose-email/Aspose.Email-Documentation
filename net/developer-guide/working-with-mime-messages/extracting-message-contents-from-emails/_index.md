---
title: Extracting Message Contents from Emails
type: docs
weight: 30
url: /net/extracting-message-contents-from-emails/
---

# Extracting Message Contents from Emails
## **Displaying Email Information on Screen**
The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) represents an email message and allows developers to access email message properties. The header information (discussed in [Extracting Email Headers](#extracting-email-headers)) can be extracted and manipulated in different ways. This article explains how to display selected email header information and the email body on screen. To Display Email Information on Screen, follow these steps:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class.
- Load an email message into the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) instance.
- Display the email content on the screen.

The following code snippet shows you how to display email information on the screen.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Email();

// Create MailMessage instance by loading an Eml file
MailMessage message = MailMessage.Load(dataDir + "test.eml", new EmlLoadOptions());

// Gets the sender info, recipient info, Subject, htmlbody and textbody
Console.Write("From:");
Console.WriteLine(message.From);
Console.Write("To:");
Console.WriteLine(message.To);
Console.Write("Subject:");
Console.WriteLine(message.Subject);
Console.WriteLine("HtmlBody:");
Console.WriteLine(message.HtmlBody);
Console.WriteLine("TextBody");
Console.WriteLine(message.Body);
```

## **Extracting Email Headers**
The email header represents an Internet and RFC defined standard set of header fields included in Internet email messages. An email header can be specified using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class. Common header types are defined in the [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype) class. It is a sealed class working like normal enumeration. To extract headers from an email, follow these steps:

1. Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class.
1. Load an email message in the instance of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class.
1. After an email message has been loaded, we will get its raw content.

The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class itself contains properties such as From, To, Cc, Subject and so on. These properties can be extracted from headers.

1. Display the raw content.

The following code snippet shows you how to extract email headers.


## **Get Decoded Header Values**
The following code snippet shows you how to get decoded header values.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
MailMessage mailMessage = MailMessage.Load(dataDir + "emlWithHeaders.eml");
string decodedValue = mailMessage.Headers.GetDecodedValue("Thread-Topic");
Console.WriteLine(decodedValue);
```

## **Get plain text body**
The [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/body) property returns a plain text representation of message's body.

```csharp
string plainTextBody = mailMessage.Body;
```

Note: If the text/plain MIME part is present in a message, the property returns its text data. Otherwise, it returns the separated text content from the [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/htmlbody) property without html markup. 


## **Get HTML body as plain text**
The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class provides the feature to extract the HTML body of the message as plain text. The [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) class provides a [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/gethtmlbodytext) method that returns the HTML body in plain text. This method parses the [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/properties/htmlbody) property and returns separated plain text content ignoring the html markup. The [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/gethtmlbodytext) method accepts a boolean parameter that indicates whether the body should contain URLs or not. Passing the parameter as true indicates that the HTML body should contain URLs.

The following code snippet demonstrates the use of [GetHtmlBodyText](https://reference.aspose.com/email/net/aspose.email/mailmessage/methods/gethtmlbodytext) method to extract the HTML body of the email as plain text.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// The path to the File directory.
string dataDir = RunExamples.GetDataDir_Email();

MailMessage mail = MailMessage.Load(dataDir + "HtmlWithUrlSample.eml");

string body_with_url = mail.GetHtmlBodyText(true);// body will contain URL
string body_without_url = mail.GetHtmlBodyText(false);// body will not contain URL

Console.WriteLine("Body with URL: " + body_with_url);
Console.WriteLine("Body without URL: " + body_without_url);
```
