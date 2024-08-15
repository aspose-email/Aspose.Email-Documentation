---
title: Save Message as Draft in Jython
type: docs
weight: 60
url: /java/save-message-as-draft-in-jython/
---

## **Aspose.Email - Save Message as Draft**
To Save Message as Draft using **Aspose.Email Java for Jython**, simply invoke **SaveMessageAsDraft** module. Here you can see example code.

**Jython Code**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import MapiMessage

from com.aspose.email import MapiMessageFlags

class SaveMessageAsDraft:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/SaveMessageAsDraft/'



        # Create a instance of MailMessage class

        message = MailMessage()

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

        message.getTo().add(MailAddress("to2@domain.com", "Recipient 2", False))

        # Create an instance of MapiMessage and load the MailMessag instance into it

        mapiMessage=MapiMessage()

        mapi_msg = mapiMessage.fromMailMessage(message)

        # Set the MapiMessageFlags as UNSENT and FROMME

        mapi_message_flags = MapiMessageFlags()



        # Save the MapiMessage to disk

        mapi_msg.save(dataDir + "New-Draft.msg")

        # Display Status

        print "Draft saved Successfully."





if __name__ == '__main__':        

    SaveMessageAsDraft()

```
## **Download Running Code**
Download **Save Message as Draft (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
