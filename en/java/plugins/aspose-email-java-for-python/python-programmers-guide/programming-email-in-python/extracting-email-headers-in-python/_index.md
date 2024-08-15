---
title: Extracting Email Headers in Python
type: docs
weight: 50
url: /java/extracting-email-headers-in-python/
---

## **Aspose.Email - Extracting Email Headers**
To Extract Email Headers using **Aspose.Email Java for Python**, Use following code.

**Python Code**

``` python



\# Initialize and Load an existing EML file by specifying the MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "Printing all Headers:"

\# Print out all the headers

i=0

while (i < message.getHeaders().getCount()):

    print message.getHeaders().get(i)

    i += 1

```
## **Download Running Code**
Download **Extracting Email Headers (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
