---
title: Utility Features - MailMessage
type: docs
weight: 40
url: /python-net/utility-features-mailmessage/
---


## **MailMessages Containing TNEF attachments**
Transport Neutral Encapsulation Format (TNEF) is a proprietary email attachment format used by Microsoft Outlook and Microsoft Exchange Server. The Aspose.Email API allows you to read email messages that have TNEF attachments and modify the contents of the attachment. The email can then be saved as normal email or to the same format, preserving TNEF attachments. This article shows different code samples for working with messages containing TNEF attachments. This article also shows working with creating TNEF EML files from Outlook MSG files.
### **Reading Message by Preserving TNEF Attachments**
The following code snippet shows you how to reading message by preserving TNEF attachments.

```py
from aspose.email import MailMessage, SaveOptions, EmlLoadOptions, MessageFormat, FileCompatibilityMode

options = EmlLoadOptions()
# This will Preserve the TNEF attachment as it is, file contains the TNEF attachment
options.preserve_tnef_attachments = True

eml = MailMessage.load(data_dir + "message.eml", options)
for attachment in eml.attachments:
    print(attachment.name)
```

### **Creating TNEF EML from MSG**
Outlook MSGs sometimes contain information such as tables and text styles that may get disturb if these are converted to EML. Creating TNEF messages from such MSG files allows to retain the formatting and even send such messages via the email clients retaining the formatting. The convert_as_tnef property is used to achieve this. The following code snippet shows you how to creating TNEF eML from MSG.

```py
from aspose.email.mapi import MapiMessage, MailConversionOptions, OutlookMessageFormat

mapi_msg = MapiMessage.from_file(data_dir + "message.msg")

mail_conversion_options = MailConversionOptions()
mail_conversion_options.convert_as_tnef = True

message = mapi_msg.to_mail_message(mail_conversion_options)
```

For creating the TNEF, the following sample code can be used.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode

options = MsgLoadOptions()
# The PreserveTnefAttachments option with MessageFormat.Msg will create the TNEF eml.
options.preserve_tnef_attachments = True

eml = MailMessage.load(eml_file_name, options)
```
### **Detect If a Message is TNEF**
The following code snippet shows you how to detect If a message is TNEF.

```py
from aspose.email import MailMessage

mail = MailMessage.load(data_dir + "message.eml")
is_tnef = mail.original_is_tnef
```
## **Processing of Bounced Messages**
It is very common that a message sent to a recipient may bounce for any reason such as invalid recipient address. Aspose.Email API has the capability to process such a message for checking if it is a bounced email or a regular email message. The  MailMesage's check_bounced method returns a valid result if the email message is a bounced email. This article shows the usage of [BounceResult](https://reference.aspose.com/email/python-net/aspose.email.bounce/bounceresult/) class that provides the capability of checking if a message is a bounced email. It further gives detailed information about the recipients, action taken and the reason about the notification. The following code snippet shows you how to process bounced messages.

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
## **Bayesian Spam Analyzer**
Aspose.Email provides email filtering using a Bayesian spam analyzer. It provides the [SpamAnalyzer](http://www.aspose.com/api/net/email/aspose.email.antispam/spamanalyzer) class for this purpose. This article shows how to train the filter to distinguish between spam and regular emails based on a words database.

```py
from aspose.email import MailMessage, SaveOptions, MsgLoadOptions, MessageFormat, FileCompatibilityMode
from aspose.email.antispam import SpamAnalyzer
import os

ham_folder = "/hamFolder"
spam_folder = "/Spam"
test_folder = data_dir
database_file = "SpamFilterDatabase.txt"

def print_result(probability):
    if probability >= 0.5:
        print("The message is classified as spam.")
    else:
        print("The message is classified as not spam.")
    print("Spam Probability: " + str(probability))
    print()

def teach_and_create_database(ham_folder, spam_folder, database_file):
    analyzer = SpamAnalyzer(database_file)
    analyzer.teach_from_directory(ham_folder, True)
    analyzer.teach_from_directory(spam_folder, False)
    analyzer.save_database()

teach_and_create_database(ham_folder, spam_folder, database_file)

test_files = [f for f in os.listdir(test_folder) if f.endswith(".eml")]
analyzer = SpamAnalyzer(database_file)

for file in test_files:
    file_path = os.path.join(test_folder, file)
    msg = MailMessage.load(file_path)
    print(msg.subject)
    probability = analyzer.test(msg)
    print_result(probability)
```
