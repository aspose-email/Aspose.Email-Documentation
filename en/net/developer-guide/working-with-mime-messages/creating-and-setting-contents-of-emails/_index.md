---
title: Creating and Setting Contents of Emails in .NET
linktitle: Creating and setting contents of Emails
type: docs
weight: 10
url: /net/creating-and-setting-contents-of-emails/
---

## **Create New Email Message**

To create a new email message you can use [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. The **MailMessage** class also initializes properties of the created email message such as the sender's email address, the recipients' email addresses, the subject of the email, and the email body content in HTML format. 

Consider the following code, with detailed steps, to create a new email message and set its properties.

**Code steps:**

1. Create a new instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Set the [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) property to the email address of the sender.
3. Set the [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) property to a comma-separated list of email addresses of the recipients.
4. Set the [Subject](https://reference.aspose.com/email/net/aspose.email/mailmessage/subject/) property to the subject of the email.
5. Set the [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) property to the HTML content of the email body.

**Code sample:**
```cs
// Create a new instance of MailMessage class
var message = new MailMessage
{
    From = "from@domain.com",
    To = "to1@domain.com, to2@domain.com",
    Subject = "New message",
    HtmlBody = @"<!DOCTYPE html>
    <html>
     <head>
      <style>
       h3{font-family:Verdana, sans-serif;color:#000000;background-color:#ffffff;}
       p {font-family:Verdana, sans-serif;font-size:14px;font-style:normal;
         font-weight:normal;color:#000000;background-color:#ffffff;}
      </style>
     </head>
     <body>
       <h3>New message</h3>
       <p>This is a new message created by Aspose.Email.</p>
     </body>
    </html>"
};
```

## **Specifying Multiple Recipients**

There are three ways to specify recepients of an email message: using **To**, **CC**, or **BCC** fields.

- **To** field is the main recipient of your message. You can enter one or more email addresses in this field, separated by commas. The To field is mandatory for every email message.

- **CC** field stands for carbon copy. It is used to send a copy of your message to other people who are interested or involved in the topic. The CC field is optional and can also contain multiple email addresses. The recipients in the CC field can see who else received the message.

- **BCC** field stands for blind carbon copy. It is similar to the CC field, but the recipients in the BCC field are hidden from the other recipients. The BCC field is useful when you want to protect the privacy of some recipients or avoid cluttering their inbox with replies. The BCC field is also optional and can have multiple email addresses.

Consider the following code, with detailed steps, to specify multiple recipients for an email message.

**Code steps:**

1. Create a new instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Set the [From](https://reference.aspose.com/email/net/aspose.email/mailmessage/from/) property to the email address of the sender.
3. Set the [To](https://reference.aspose.com/email/net/aspose.email/mailmessage/to/) property to an array of email addresses of the primary recipients.
4. Set the [CC](https://reference.aspose.com/email/net/aspose.email/mailmessage/cc/) property to an array of email addresses of the recipients who will receive a copy of the email.
5. Set the [Bcc](https://reference.aspose.com/email/net/aspose.email/mailmessage/bcc/) property to an array of email addresses of the recipients who will receive a blind carbon copy of the email.

**Code sample:**

```cs
var eml = new MailMessage
{
    // Specify From address
    From = "sender@sender.com",
    //  Specify recipients’ mail addresses
    To = {"receiver1@receiver.com", "receiver2@receiver.com", "receiver3@receiver.com"},
    // Specify CC addresses
    CC = {"CC1@receiver.com", "CC2@receiver.com"},
    // Specify BCC addresses
    Bcc = {"Bcc1@receiver.com", "Bcc2@receiver.com"}
};
```

## **Adding display names to email addresses**

Along with an email address, a **display name** can be included to identify the sender or recipient of the email. It may include a person's full name, nickname, or other identifier.

When an email message is displayed in an email client or webmail interface, the display name is usually shown alongside the email address, making it easier for the user to identify who the message is from or who it is addressed to. For example, an email address might be "johndoe@example.com," but the display name associated with it could be "John Doe." 

To add display names to email addresses in an email message, consider the following code with detailed steps:

**Code steps:**

1. Load the email message from a file using [MailMessage.Load]() method.
2. Set the sender of the email using the [From]() property of the eml object by creating a new [MailAddress]() object with the email address and a display name of the sender.
3. Add a recipient to the email by using the [To]() property of the eml object, if necessary add CC (Carbon Copy) list using the [CC]() property, BCC (Blind Carbon Copy) list using the [Bcc]() property and call the [Add]() method with a new [MailAddress]() object that contains the email address and a display name of the recipient.

**Code sample:**

```cs
// Load eml from file
MailMessage eml = MailMessage.Load(Data.Email/"test.eml");

eml.From = new MailAddress("TimothyFairfield@from.com", "Timothy Fairfield");

// A To address with a friendly name can also be specified like this
eml.To.Add(new MailAddress("kyle@to.com", "Kyle Huang"));

// Specify Cc and Bcc email address along with a friendly name
eml.CC.Add(new MailAddress("guangzhou@cc.com", "Guangzhou Team"));
eml.Bcc.Add(new MailAddress("ahaq@bcc.com", "Ammad ulHaq "));
```
## **Displaying the optional attendees in the mht header output**

The code sample below demonstrates how to use *display optional attendees* feature when saving an msg in mhtml format:


```cs
MhtSaveOptions options = new MhtSaveOptions()
{
    MhtFormatOptions = MhtFormatOptions.RenderCalendarEvent | MhtFormatOptions.WriteHeader
};

MapiMessage msg = MapiMessage.Load(fileName);
msg.Save(fileName + ".mhtml", options);

//if you need to skip OptionalAttendees in mhtml file you can clear format template for OptionalAttendees
options.FormatTemplates[MhtTemplateName.OptionalAttendees] = "";
msg.Save(fileName + "2.mhtml", options);
```


## **Set Mail Body**

In this article you will learn how to:

- [set plain text body](#Set-Plain-Text-Body)
- [set HTML body](#Setting-HTML-Body)
- [set alternate text](#Setting-Alternate-Text)
- [specify mail body encoding](#Specifying-Mail-Body-Encoding)

### **Setting Plain Text Body**

A mail body can be specified using the [Body](https://reference.aspose.com/email/net/aspose.email/mailmessage/body/) property of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Specify HtmlBody
    Body = "This is a plain text body"
};
```

### **Setting HTML Body**

A mail body can also be specified using [HtmlBody](https://reference.aspose.com/email/net/aspose.email/mailmessage/htmlbody/) property of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. 

```cs
// Declare message as MailMessage instance
var eml = new MailMessage
{
    // Specify HtmlBody
    HtmlBody = "<html><body>This is the HTML body</body></html>"
};
```

### **Setting Alternate Text**

An alternate view in an EML file is an additional representation of the email content that can be used to provide a different rendering of the email message. For example, if you send a message in HTML, you might also want to provide a **plain text** version in case some of the recipients use email readers that cannot display HTML content. For that purpose use the [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/) class. This class has two properties, [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) and [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/), which are used to resolve URLs within the content of the email.

- [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) is a collection of [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) objects. When rendered, URLs within the email content are first matched against the URLs in the Content Link of each [LinkedResource](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) object in the [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) collection and resolved.
- [BaseUri](https://reference.aspose.com/email/net/aspose.email/alternateview/baseuri/) is used by the mail reader to resolve relative URLs within the body, and also to resolve relative Content Link URLs, in the [LinkedResources](https://reference.aspose.com/email/net/aspose.email/alternateview/linkedresources/) collection.

Consider the following code with detailed steps to set an alternate text.

**Code steps:**

1. Create an instance of [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
2. Create [AlternateView](https://reference.aspose.com/email/net/aspose.email/alternateview/createalternateviewfromstring/) to view an email message using the content specified in the string.
3. Add alternate text using [Add](https://reference.aspose.com/email/net/aspose.email/mailmessage/addalternateview/) method of [MailMessage.AlternateViews](https://reference.aspose.com/email/net/aspose.email/mailmessage/alternateviews/) collection.

**Code sample:**
```cs
// Declare message as MailMessage instance
var eml = new MailMessage();

// Creates AlternateView to view an email message using the content specified in the //string
AlternateView alternate = AlternateView.CreateAlternateViewFromString("Alternate Text");

// Adding alternate text
 eml.AlternateViews.Add(alternate);
```

### **Specifying Mail Body Encoding**

Aspose.Email uses the [BodyEncoding](https://reference.aspose.com/email/net/aspose.email/mailmessage/bodyencoding/) property of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class to specify the email body encoding. For example:

```cs
eml.BodyEncoding = Encoding.UTF8;
```

## **Setting MailMessage Additional Properties**

With Aspose.Email you can use additional properties of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class such as:

- [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) property - sets **date and time** of an email. By default, the date is the actual date when the message was sent, and time is the time it was sent, as displayed by Microsoft Outlook. However, the real email delivery time is added by the SMTP server itself in the mail header. For example, below is a common mail header, where [Date](https://reference.aspose.com/email/net/aspose.email/mailmessage/date/) sets the field Date.

   ```cs
   // For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
   
   // Add by SMTP server in delivery emails
   Received: from ip-123.56.99.216.dsl-cust.ca.inter.net ([216.99.56.123]) by Aspose.secureserver.net with MailEnable ESMTP; Thu, 22 Feb 2007 13:58:57 -0700
   
   // Add by SMTP server in delivery emails
   Return-Path: <xyz@oikoscucine.it>
   
   // Add by SMTP server in delivery emails
   Received: from 195.120.225.20 (HELO mail.oikoscucine.it)
   by aspose.com with esmtp (:1CYY+<LA*- *1WK@)
   id Q8,/O/-.N83@7-9M
   for abc@aspose.com; Thu, 22 Feb 2007 20:58:51 +0300
   From: "XYZ" <xyz@oikoscucine.it>
   To: <abc@aspose.com>
   Subject: For ABC
   
   // Date will set the Date field, outlook will show this as
   Date: Thu, 22 Feb 2007 20:58:51 +0300
   Message-ID: <01c756c4$41b554d0$6c822ecf@dishonestyinsufferably>
   MIME-Version: 1.0
   Content-Type: multipart/alternative;
   boundary="----=_NextPart_000_0006_01C7569A.58DF4CD0"
   X-Mailer: Microsoft Office Outlook, Build 11.0.5510
   X-MimeOLE: Produced By Microsoft MimeOLE V6.00.2800.1106
   Thread-Index: Aca6Q:=ES0M(9-=(<.<1.<Q9@QE6CD==
   X-Read: 1
   ```

- [MailPriority](https://reference.aspose.com/email/net/aspose.email/mailpriority/#mailpriority-enumeration) enumeration- specifies priority levels for sending an email message. It can be low, normal or high. Priority influences transmission speed and delivery.
- [MailSensitivity](https://reference.aspose.com/email/net/aspose.email/mailsensitivity/#mailsensitivity-enumeration) enumeration - specifies five levels of sensitivity.
- [XMailer](https://reference.aspose.com/email/net/aspose.email/mailmessage/xmailer/)- specifies the software that created the e-mail message.

The code snippet below illustrates how each of the properties discussed above can be used.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Some subject", "Some body text")
{
    Date = DateTime.Now,
    Priority = MailPriority.High,
    Sensitivity = MailSensitivity.Normal,
    Xmailer = "Aspose.Email"
};
```

## **Requesting a Read Receipt**

To request a [read receipt](https://en.wikipedia.org/wiki/Return_receipt), use Aspose.Email [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/mailmessage/deliverynotificationoptions/) property of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. This property contains the values of the [DeliveryNotificationOptions](https://reference.aspose.com/email/net/aspose.email/deliverynotificationoptions/#deliverynotificationoptions-enumeration) enumeration.

Consider the following **code sample**:

```cs
// Create an Instance of MailMessage class
var eml = new MailMessage
{
    // Specify From, To, HtmlBody, DeliveryNotificationOptions field
    From = "sender@sender.com",
    To = "receiver@receiver.com",
    HtmlBody = "<html><body>This is the Html body</body></html>",
    DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess
};

eml.Headers.Add("Return-Receipt-To", "sender@sender.com");
eml.Headers.Add("Disposition-Notification-To", "sender@sender.com");

// Create an instance of SmtpClient Class
var client = new SmtpClient
{
    // Specify your mailing host server, Username, Password and Port No
    Host = "smtp.server.com",
    Username = "Username",
    Password = "Password",
    Port = 25
};

try
{
    // Client.Send will send this message
    client.Send(eml);
    // Display ‘Message Sent’, only if message sent successfully
    Console.WriteLine(@"Message sent");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

**Note**: Read receipt requests may not be always honored because:

- A mail client may not implement that functionality.
- The end-user may have that functionality turned off.
- The end-user may choose not to send one.


## **Set Email Headers**

Email headers represent an Internet standard and RFC define header fields which are included in Internet email messages. An email header can be specified using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. Common header types are defined in the [HeaderType](https://reference.aspose.com/email/net/aspose.email/headertype/) class. It is a sealed class working as a normal enumeration.

Normally, an email header contains these fields:

- **To**: Recipient addresses can be specified in the To field. The To field recipients are the message's primary audience. There can be more than one recipient addresses.
- **From**: This field presents the email address of the message sender.
- **Cc**: Allows users to send a message as a "Carbon Copy" or "Courtesy Copy". That is, the receiver is not expected to reply or act. Typically, supervisory personnel are notified with CC.
- **Bcc**: It stands for Blind Carbon Copy, which lets you send an email to a recipient that is hidden from other recipients.
- **ReplyTo**: This header field is meant to indicate where the sender wants replies to go.
- **Subject**: Title, heading, subject. Often used as a thread indicator for messages replying to or commenting on other messages.
- **Date**: This header specifies a date (and time). Normally this is the date at which the message was composed and sent.
- **XMailer**: Information about the client software of the originator. Example: X-Mailer: Aspose.Email. XMailer is used by mail clients. Different mail clients will have different XMailer values. MS Outlook's XMailer value is Microsoft Office Outlook, Build 11.0.5510. It is ignored by the email receiver or email reader.

Normally, an email header looks something like this:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: guangzhou@guangzhoo.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

To customize an email header, follow these **code steps**:

- Create an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
- Specify To, From, Cc, Bcc, ReplyTo, Subject, Date & XMailer using an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
- Create an instance of the [MimeHeader](https://reference.aspose.com/email/net/aspose.email.mime/mimeheader/) class and specify the custom header.
- Add the custom header to the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) instance.

The following **code snippet** shows you how to set email headers.

```cs
var eml = new MailMessage
{
    ReplyToList = "reply@reply.com",
    From = "sender@sender.com",
    To = "receiver1@receiver.com",
    CC = "receiver2@receiver.com",
    Bcc = "receiver3@receiver.com",
    Subject = "test mail",
    Date = new System.DateTime(2006, 3, 6),
    XMailer = "Aspose.Email"
};
```

The above code snippet produces an email header in the following format:

```
Reply-To: reply@reply.com
From: sender@sender.com
To: receiver1@receiver.com
CC: receiver2@receiver.com
BCC: receiver3@receiver.com
Subject: test mail
Date: 6 Mar 2006 8:2:2 +0800
X-Mailer: Aspose.Email
```

### **Insert a Header at a Specific Location**

The [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) method of the [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/) class inserts a header at the end of the collection. However, it may sometimes be necessary to insert a header at a specific location. In such a case, the [Add](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/add/#add/) method won't be of help. To achieve this, use the [Insert](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/insert/#insert) method of the [HeaderCollection](https://reference.aspose.com/email/net/aspose.email.mime/headercollection/). If the collection contains headers with the same name, this header will be inserted before other headers with the same name. The following code snippet shows you how to insert a header at a specific location.

```cs
eml.Headers.Insert("Received", "Value");
```

### **Save All Headers in MHTML**

The [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/#mhtsaveoptionssaveallheaders-property) property of the [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) class defines whether there is a need to save all headers in output mhtml or not. The following code snippet shows you how to save all headers of an mhtml file:

```cs
var eml = MailMessage.Load("message.eml");
var sopt = SaveOptions.DefaultMhtml;
sopt.SaveAllHeaders = true;
eml.Save("message.mhtml", sopt);
```

### **Adding Custom Headers to Email**

An email header can be specified using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class. To specify a **custom header** in an email message, consider the following code sample:

```cs
eml.Headers.Add("secret-header", "mystery");
```

The above code snippet produces an email header in the following format:

```cs
secret-header: mystery
```

## **Save a HTML file with Task Fields in a Header**

The [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) enumeration allows you to specify that task fields should be included in the header of the saved HTML file. The following code snippet shows how to preserve task fields in a header when saving a html file:

```cs
var msg = MapiMessage.Load("task.msg");
HtmlSaveOptions opt = SaveOptions.DefaultHtml;
opt.HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderTaskFields;
msg.Save("task.html", opt);
```

## **Sign Emails with DKIM**

> **_NOTE:_** The feature is accessible only for the library versions targeting .NET Framework. Versions, targeting .NET Core, do not have this feature.

Aspose.Email allows signing Email with DKIM (DomainKeys Identified Mail). This lets an organization take responsibility for a message that is in transit ([More Info](https://www.dkim.org/)). DKIM adds a digital signature to the email message headers that can be validated by recipients. The public key of the sender enables the receiver to verify that the signature matches the message's contents. The [DKIMSign](https://reference.aspose.com/email/net/aspose.email/mailmessage/dkimsign/#dkimsign) method of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class is used to set the cryptographic and signature information for signing the message. The following code snippet shows you how to sign emails with DKIM.

```cs
var eml = new MailMessage("sender@gmail.com", "receiver@gmail.com", "Some subject", "Some body text");

string privateKeyFile = "key2.pem";
RSACryptoServiceProvider rsa = PemReader.GetPrivateKey(privateKeyFile);
DKIMSignatureInfo signInfo = new DKIMSignatureInfo("test", "somedomain.com");

var signedEml = eml.DKIMSign(rsa, signInfo);
```
