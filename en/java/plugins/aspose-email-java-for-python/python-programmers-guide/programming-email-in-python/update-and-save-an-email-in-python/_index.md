---
title: Update and Save an Email in Python
type: docs
weight: 80
url: /java/update-and-save-an-email-in-python/
---

## **Aspose.Email - Update and Save an Email**
To Update and Save an Email using **Aspose.Email Java for Python**, Use following code.

**Python Code**

``` python



\# Initialize and Load an existing MSG file by specifying the MessageFormat

mailMessage = self.MailMessage

email = mailMessage.load(self.dataDir + "Message.msg")

\# Initialize a String variable to get the Email Subject

subject = email.getSubject()

\# Append some more information to Subject

subject = subject + " This text is added to the existing subject"

\# Set the Email Subject

email.setSubject('This text is added to the existing subject')

\# Initialize a String variable to get the Email's HTML Body

body = email.getHtmlBody()

\# Apppend some more information to the Body variable

body = body + "<br> This text is added to the existing body"

\# Set the Email Body

email.setHtmlBody(body)

\# Initialize MailAddressCollection object

contacts = self.MailAddressCollection()

\# Retrieve Email's TO list

contacts = email.getTo()

\# Add another email address to collection

contacts.add("to1@domain.com")

\# Set the collection as Email's TO list

email.setTo(contacts)

\# Initialize MailAddressCollection

contacts = self.MailAddressCollection()

\# Retrieve Email's CC list

contacts = email.getCC()

\# Add another email address to collection

contacts.add("cc2@domain.com")

\# Set the collection as Email's CC list

email.setCC(contacts)

\# Save the Email message to disk by specifying the MessageFormat

mailMessageSaveType = self.MailMessageSaveType

email.save(self.dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

\# Display Status

print "Updated email message Successfully."

```
## **Download Running Code**
Download **Update and Save an Email (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
