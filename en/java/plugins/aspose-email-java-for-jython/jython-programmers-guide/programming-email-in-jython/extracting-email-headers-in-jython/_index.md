---
title: Extracting Email Headers in Jython
ArticleTitle: Extracting Email Headers in Jython
type: docs
weight: 40
url: /java/extracting-email-headers-in-jython/
---

## **Aspose.Email - Extracting Email Headers**
To Extract Email Headers using **Aspose.Email Java for Jython**, simply invoke **ExtractEmailHeaders** module. Here you can see example code.

**Jython Code**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

class ExtractEmailHeaders:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ExtractEmailHeaders/'



        # Initialize and Load an existing EML file by specifying the MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "Printing all Headers:"

        # Print out all the headers

        i=0

        while (i < message.getHeaders().getCount()):

            print message.getHeaders().get(i)

            i += 1





if __name__ == '__main__':        

    ExtractEmailHeaders()

```
## **Download Running Code**
Download **Extracting Email Headers (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
