---
title: Detecting and Processing Bounced Emails in Python
ArticleTitle: Detecting and Processing Bounced Emails in Python
type: docs
weight: 60
url: /python-net/processing-bounced-emails/
---


## **Processing Bounced Emails**

It is very common that a message sent to a recipient may bounce for some reason such as invalid recipient address. The Aspose.Email API has the ability to check if an email is a bounced one or regular and process it. The [check_bounced](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#methods) method of the [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/#mailmessage-class) class returns a valid result if the email message is a bounced one. The following code snippet shows you how to process bounced messages using the [BounceResult](https://reference.aspose.com/email/python-net/aspose.email.bounce/bounceresult/) class providing the detailed information about the recipients, the action taken and the reason for the notification.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

mail = MailMessage.load(data_dir + "message.eml")
result = mail.check_bounced()

print("IsBounced: " + str(result.is_bounced))
print("Action: " + str(result.action))
print("Recipient: " + str(result.recipient))
print()
print("Reason: " + str(result.reason))
print("Status: " + str(result.status))
print()
```


