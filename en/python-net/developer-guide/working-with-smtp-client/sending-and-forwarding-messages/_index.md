---
title: Sending and Forwarding Messages
ArticleTitle: Sending and Forwarding Messages
type: docs
weight: 20
url: /python-net/sending-and-forwarding-messages/
---


The SmtpClient class allows applications to send email using the Simple Mail Transfer Protocol (SMTP).

- The SmtpClient class is the only major entry developers use to send mail messages.
- The SmtpClient class also provides other common email delivery methods, including writing email messages to the file system, message queue etc.
- The SmtpClient class fully supports these two programming models:
  - Synchronous
- The SmtpClient class also supports sending messages as TNEF

To send the email message and block while waiting for the email to be transmitted to the SMTP server, use one of the synchronous Send methods. To allow your program's main thread to continue executing while the email is transmitted, use one of the asynchronous SendAsync methods.
## **Sending Emails Synchronously**
An email message can be sent synchronously using the SmtpClient class Send method. It sends the specified email message through an SMTP server for delivery. The message sender, recipients, subject, and message body are specified using String objects. To send an email message synchronously, follow the steps given below:

1. Create an instance of MailMessage class and set its properties.
1. Create an instance of SmtpClient class and specify the Host, port, username & Password.
1. Send the Message using the SmtpClient class Send method and pass the MailMessage instance.

The following code snippet shows you how to send emails synchronously.

{{% alert color="primary" %}} 

Sending emails asynchronously is not supported by the API.

{{% /alert %}} 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendEmailsSynchronously-SendEmailsSynchronously.py" >}}

## **Sending Stored Messages from Disc**

If you need to programmatically send a pre-composed email message stored in the EML format, use the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class to load the existing file and keep it before sending. Then send it using the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class specifying the SMTP server's hostname, username, and password for authentication. The 'send' method of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class is used to send the email message. The whole process is shown in the code sample below.

```py
import aspose.email as ae

message = ae.MailMessage.load("test.eml")

# Send this message using SmtpClient
client = ae.clients.SmtpClient("host", "username", "password")
client.send(message)
```

## **Sending Plain Text Email**
The programming samples below show how to send a plain text email message. The Body property, a property of the MailMessage class, is used to specify the plain text content of the message body. To send a plain text email message, follow these steps:

- Create an instance of the MailMessage class.
- Specify the sender and receiver email addresses in the MailMessage instance.
- Specify the TextBody content, used for the plain text message.
- Create an instance of the SmtpClient class and send the email.

The following code snippet shows you how to send plain text email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingPlainTextMessage-SendingPlainTextMessage.py" >}}
## **Sending Email with HTML body**
The programming samples below show how you can send a simple HTML email message. The HtmlBody, a property of the MailMessage class, is used to specify the HTML content of the message body. To send a simple HTML email, follow these steps:

- Create an instance of the MailMessage class.
- Specify sender and receiver email address in the MailMessage instance.
- Specify the HtmlBody content.
- Create an instance of the SmtpClient class and send the email using the Send method.

For the purposes of this article, the HTML content of the email is rudimentary: <html><body>This is the HTML body</body></html> Most HTML emails will be more complex. The following code snippet shows you how to send email with HTML body.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SettingHTMLBody-SettingHTMLBody.py" >}}
## **Sending Email with Alternate Message Text**
The programming samples below show how to send a simple HTML email message with alternative content. Use the AlternateView class to specify copies of an email message in different formats. For example, if you send a message in HTML, you might also want provide a plain text version for recipients who use email readers that cannot display HTML content. Or, if you are sending a newsletter, you might want to provide a plain text copy of the text for those recipients who have chosen to receive a plain text version. To send an email with alternate text, follow these steps:

1. Create an instance of the MailMessage class.
1. Specify sender and receiver email addresses in the MailMessage instance.
1. Create an instance of the AlternateView class.

This creates an alternate view to an email message using the content specified in the string.

1. Add instance of the AlternateView class to the MailMessage object.
1. Create an instance of the SmtpClient class and send the email using the Send method.

The following code snippet shows you how to send email with alternate text.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SetAlternateText-SetAlternateText.py" >}}
## **Sending Bulk Emails**
Sending emails in bulk means sending a batch of emails in one message. We can send batch of email using the of SmtpClient class BulkSend method:

1. Create an instance of SmtpClient class.
1. Specify the SmtpClient class properties.
1. Create an instance of the MailMessage class.
1. Specify sender, receiver, mail subject and message in the instance of the MailMessage class.
1. Repeat the above two steps again, if you want to send email to a different person.
1. Create an instance of MailMessageCollection class.
1. Add instance of MailMessage class in the object of the MailMessageCollection class.
1. Now send your email using the SmtpClient class BulkSend method by passing the instance of MailMessageCollection class in it.

The following code snippet shows you how to sending bulk emails.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingBulkEmails-SendingBulkEmails.py" >}}

## **Sending Emails with MultiConnection**

The following properties of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class allow a client to utilize multiple connections to the server for sending emails. This can be beneficial in scenarios where the client needs to send a large volume of emails and wants to distribute the workload across multiple connections.

- 'use_multi_connection' property	gets or sets value which indicates if client has to use multiple connections for heavy loaded operations.
- 'connections_quantity' property	gets or sets quantity of connections in multy-connection mode.
```
Please note, the use of this mode will not necessarily lead to performance increasing.
```
The following code sample shows how to implement this feature in a project:
```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

client.connections_quantity = 5
client.use_multi_connection = ae.clients.MultiConnectionMode.ENABLE
client.send(messages)
```

## **Sending Message as TNEF**
TNEF emails have special formatting which may be lost if sent using the standard API. Aspose.Email provides the capability to send emails as TNEF, thus preserving the format. The SmtpClient class UseTnef property can be set to send the email as TNEF. The following code snippet shows you how to send message as TNEF.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendMsgAsTNEF-SendMsgAsTNEF.py" >}}
## **Sending Meeting Requests**
Microsoft Outlook offers calendar functions as well as email management. When a user opens an email with an invitation to an event, Outlook prompts them to accept or reject the invitation. Aspose.Email lets developers add calendar functions to your emails.
### **Sending Requests via Email**
To send meeting requests via email, follow these steps:

- Create an instance of the MailMessage class.
- Specify sender and recipient addresses using an instance of the MailMessage class.
- Initialize an instance of the Appointment class and pass it values.
- Specify summary and description in the Calendar instance.
- Add the Calendar to the MailMessage instance and pass it the Appointment instance.

|**iCalendar meeting request sent by email**|
| :- |
|![todo:image_alt_text](sending-and-forwarding-messages_1.png)|
The following code snippet shows you how to send requests via Email.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SendingMeetingRequestsViaEmail-SendingMeetingRequestsViaEmail.py" >}}
### **iCalendar supports for IBM Lotus Notes**
Aspose.Email.Mail's calendar feature is based on the iCalendar standard, a standard for calendar data exchange (RFC 2445 or RFC2445 Syntax Reference). Therefore, it supports not only Microsoft Outlook, but also IBM Lotus Notes. To send a meeting request in Lotus Notes, follow the same steps as mentioned above.
## **Forward an Email using SMTP Client**
### **Forwarding Email with SMTP client**
Forwarding an email is common practice in daily life digital communication. An email received can be forwarded to specific recepients without sharing with the original senders. Aspose.Email API's SmtpClient provides the capability to forward an email to specific recipients. It's Forward method can be used to forward a received or saved email to desired recipients as shown in this article. The following code snippet shows you how to Forward an Email using SMTP Client.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-ForwardEmail-ForwardEmail.py" >}}

### **Forwarding Email without using MailMessage**

The API also supports forwarding EML messages without first loading into [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class). This is useful in cases where there are limited resources in terms of system memory.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient(host, smtp_port, username, password, ae.clients.SecurityOptions.AUTO)
file = open("test.eml", "rb")
client.forward(sender, recipients, file)
```
