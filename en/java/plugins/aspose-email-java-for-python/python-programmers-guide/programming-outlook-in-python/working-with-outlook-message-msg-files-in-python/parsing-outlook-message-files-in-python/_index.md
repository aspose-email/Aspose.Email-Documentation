---
title: Parsing Outlook Message Files in Python
ArticleTitle: Parsing Outlook Message Files in Python
type: docs
weight: 30
url: /java/parsing-outlook-message-files-in-python/
---

## **Aspose.Email - Parsing Outlook Message Files**
To Parse Outlook Message Files using **Aspose.Email Java for Python**, Use following code.

**Python Code**

{{< highlight python >}}



mapiMessage = self.MapiMessage

outlook_message_file = mapiMessage.fromFile(self.dataDir + "Message.msg")

\# Display sender's name

print "Sender Name : " 

print outlook_message_file.getSenderName()

#Display Subject

print "Subject : " 

print outlook_message_file.getSubject()

\# Display Body

print "Body : " 

print outlook_message_file.getBody()

{{< /highlight >}}
## **Download Running Code**
Download **Parsing Outlook Message Files (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
