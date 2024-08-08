---
title: Parsing Outlook Message Files in Jython
type: docs
weight: 30
url: /java/parsing-outlook-message-files-in-jython/
---

## **Aspose.Email - Parsing Outlook Message Files**
To Parse Outlook Message file using **Aspose.Email Java for Jython**, simply invoke **ParseOutlookMessageFile** module. Here you can see example code.

**Jython Code**

{{< highlight python >}}

 from aspose-email import Settings

from com.aspose.email import MapiMessage

class ParseOutlookMessageFile:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookMessageFiles/ParseOutlookMessageFile/'



        mapiMessage=MapiMessage()

        outlook_message_file = mapiMessage.fromFile(dataDir + "Message.msg")

        # Display sender's name

        print "Sender Name : " 

        print outlook_message_file.getSenderName()

        #Display Subject

        print "Subject : " 

        print outlook_message_file.getSubject()

        # Display Body

        print "Body : " 

        print outlook_message_file.getBody()





if __name__ == '__main__':        

    ParseOutlookMessageFile()

{{< /highlight >}}
## **Download Running Code**
Download **Parsing Outlook Message Files (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
