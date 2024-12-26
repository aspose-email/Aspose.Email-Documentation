---
title: Manage Attachments in Email Message in Jython
ArticleTitle: Manage Attachments in Email Message in Jython
type: docs
weight: 50
url: /java/manage-attachments-in-email-message-in-jython/
---

## **Aspose.Email - Manage Attachments in Email Message**
To Add Attachments to a New Email Message using **Aspose.Email Java for Jython**, call **add_attachments** method of **ManageAttachments** module. Here you can see example code.

**Jython Code**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import Attachment

from com.aspose.email import MessageFormat

class ManageAttachments:

    def __init__(self):



        self.add_attachments()



    def add_attachments(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ManageAttachments/'



        # Create a instance of MailMessage class

        message =MailMessage()

        # Set subject of the message

        message.setSubject("New message created by Aspose.Email for Java")

        mail_address = MailAddress

        # Set Html body

        message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

            "<font color=blue>This line is in blue color</font>")

        # Set sender information

        message.setFrom(MailAddress("from@domain.com", "Sender Name", False))

        # Add TO recipients

        message.getTo().add(MailAddress("to1@domain.com", "Recipient 1", False))

        # Adding attachment

        # Load an attachment

        attachment = Attachment(dataDir + "1.txt")

        # Add attachment in instance of MailMessage class

        message.addAttachment(attachment)

        # Save message to disc

        messageFormat=MessageFormat()

        message.save(dataDir + "Add-Attachment.msg", messageFormat.getMsg())

        # Display Status

        print "Added attachment successfully."





if __name__ == '__main__':        

    ManageAttachments()

```
## **Download Running Code**
Download **Manage Attachments in Email Message (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
