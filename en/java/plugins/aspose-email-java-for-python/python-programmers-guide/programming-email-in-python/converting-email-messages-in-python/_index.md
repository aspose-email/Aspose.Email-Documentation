---
title: Converting Email Messages in Python
type: docs
weight: 10
url: /java/converting-email-messages-in-python/
---

## **Aspose.Email - Converting Email Messages**
To Convert Email Messages using **Aspose.Email Java for Python**, Use following code.

**Python Code**

``` python

 # Initialize and Load an existing EML file by specifying the MessageFormat

mailMessage = self.MailMessage

eml = mailMessage.load(self.dataDir + "Message.eml")

\# Save the Email message to disk in Unicode format

saveOptions= self.SaveOptions

eml.save(self.dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

\# Display Status

print "Converted email to msg successfully."

```
## **Download Running Code**
Download **Converting Email Messages (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
