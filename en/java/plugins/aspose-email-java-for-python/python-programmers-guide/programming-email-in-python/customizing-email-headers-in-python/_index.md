---
title: Customizing Email Headers in Python
ArticleTitle: Customizing Email Headers in Python
type: docs
weight: 30
url: /java/customizing-email-headers-in-python/
---

## **Aspose.Email - Customizing Email Headers**
To Customize Email Headers using **Aspose.Email Java for Python**, Use following code.

**Python Code**

``` python



\# Create a instance of MailMessage class

message = self.MailMessage()

    # Set subject of the message

message.setSubject("New message created by Aspose.Email for Java")

\# Set Html body

message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

    "<font color=blue>This line is in blue color</font>")

\# Set sender information

message.setFrom(self.MailAddress("from@domain.com", "Sender Name", False))

\# Add TO recipients

message.getTo().addMailAddress(self.MailAddress("to@domain.com", "Recipient 1", False))

\# Message subject

message.setSubject("Customizing Email Headers")

\# Specify Date

timeZone = self.TimeZone

calendar = self.Calendar

calendar = calendar.getInstance(timeZone.getTimeZone("GMT"))

date = calendar.getTime()

message.setDate(date)

\# Specify XMailer

message.setXMailer("Aspose.Email")

\# Specify Secret Header

message.getHeaders().add("secret-header", "mystery")

\# Save message to disc

messageFormat= self.MessageFormat

message.save(self.dataDir + "MsgHeaders.msg", messageFormat.getMsg())

\# Display Status

print "Customized message headers Successfully."

```
## **Download Running Code**
Download **Customizing Email Headers (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
