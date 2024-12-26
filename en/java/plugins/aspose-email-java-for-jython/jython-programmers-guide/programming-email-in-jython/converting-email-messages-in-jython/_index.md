---
title: Converting Email Messages in Jython
ArticleTitle: Converting Email Messages in Jython
type: docs
weight: 10
url: /java/converting-email-messages-in-jython/
---

## **Aspose.Email - Converting Email Messages**
To Convert Email Messages using **Aspose.Email Java for Jython**, call **convert_eml_to_msg** method of **Converter** module. Here you can see example code.

**Jython Code**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import SaveOptions

class Converter:

    def __init__(self):



        # Loading EML, Saving to MSG

        self.convert_eml_to_msg()



    def convert_eml_to_msg(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/Converter/'



        # Initialize and Load an existing EML file by specifying the MessageFormat

        mailMessage = MailMessage()

        eml = mailMessage.load(dataDir + "Message.eml")

        # Save the Email message to disk in Unicode format

        saveOptions= SaveOptions

        eml.save(dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

        # Display Status

        print "Converted email to msg successfully."



if __name__ == '__main__':        

    Converter()

```
## **Download Running Code**
Download **Converting Email Messages (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
