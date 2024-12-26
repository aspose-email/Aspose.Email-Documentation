---
title: Update and Save an Email in Jython
ArticleTitle: Update and Save an Email in Jython
type: docs
weight: 70
url: /java/update-and-save-an-email-in-jython/
---

## **Aspose.Email - Update and Save an Email**
To Update and Save an Email using **Aspose.Email Java for Jython**, simply invoke **UpdateEmail** module. Here you can see example code.

**Jython Code**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddressCollection

from com.aspose.email import MailMessageSaveType

class UpdateEmail:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/UpdateEmail/'



        # Initialize and Load an existing MSG file by specifying the MessageFormat

        mailMessage=MailMessage()

        email = mailMessage.load(dataDir + "Message.msg")

        # Initialize a String variable to get the Email Subject

        subject = email.getSubject()

        # Append some more information to Subject

        subject = subject + " This text is added to the existing subject"

        # Set the Email Subject

        email.setSubject('This text is added to the existing subject')

        # Initialize a String variable to get the Email's HTML Body

        body = email.getHtmlBody()

        # Apppend some more information to the Body variable

        body = body + "<br> This text is added to the existing body"

        # Set the Email Body

        email.setHtmlBody(body)

        # Initialize MailAddressCollection object

        contacts = MailAddressCollection()

        # Retrieve Email's TO list

        contacts = email.getTo()

        # Add another email address to collection

        contacts.add("to1@domain.com")

        # Set the collection as Email's TO list

        email.setTo(contacts)

        # Initialize MailAddressCollection

        contacts = MailAddressCollection()

        # Retrieve Email's CC list

        contacts = email.getCC()

        # Add another email address to collection

        contacts.add("cc2@domain.com")

        # Set the collection as Email's CC list

        email.setCC(contacts)

        # Save the Email message to disk by specifying the MessageFormat

        mailMessageSaveType=MailMessageSaveType

        email.save(dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

        # Display Status

        print "Updated email message Successfully."





if __name__ == '__main__':        

    UpdateEmail()

```
## **Download Running Code**
Download **Update and Save an Email (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
