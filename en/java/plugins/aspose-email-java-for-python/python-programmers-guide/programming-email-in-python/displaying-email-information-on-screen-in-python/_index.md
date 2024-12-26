---
title: Displaying Email Information on Screen in Python
ArticleTitle: Displaying Email Information on Screen in Python
type: docs
weight: 40
url: /java/displaying-email-information-on-screen-in-python/
---

## **Aspose.Email - Displaying Email Information**
To Displaying Email Information using **Aspose.Email Java for Python**, Use following code.

**Python Code**

``` python



\# Create MailMessage instance by loading an Eml file

message_format = self.MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

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

```
## **Download Running Code**
Download **Displaying Email Information (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
