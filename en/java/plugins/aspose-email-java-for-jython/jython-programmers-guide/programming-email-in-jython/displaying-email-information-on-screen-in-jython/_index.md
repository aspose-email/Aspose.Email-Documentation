---
title: Displaying Email Information on Screen in Jython
type: docs
weight: 30
url: /java/displaying-email-information-on-screen-in-jython/
---

## **Aspose.Email - Displaying Email Information**
To Display Email Information using **Aspose.Email Java for Jython**, simply invoke **GetEmailInfo** module. Here you can see example code.

**Jython Code**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MessageFormat

class GetEmailInfo:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/GetEmailInfo/'



        # Create MailMessage instance by loading an Eml file

        message_format = MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "From: " 

        print message.getFrom()

        print "To: " 

        print message.getTo()

        print "Subject: " 

        print message.getSubject()

        print "HtmlBody: " 

        print message.getHtmlBody()

        print "TextBody: " 

        print message.getTextBody()





if __name__ == '__main__':        

    GetEmailInfo()

```
## **Download Running Code**
Download **Displaying Email Information (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
