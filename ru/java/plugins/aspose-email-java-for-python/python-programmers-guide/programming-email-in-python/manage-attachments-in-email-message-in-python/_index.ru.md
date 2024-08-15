---
title: "Управление вложениями в сообщении электронной почты на Python"
url: /ru/java/manage-attachments-in-email-message-in-python/
weight: 60
type: docs
---

## **Aspose.Email - Управление вложениями в электронной почте**
Для управления вложениями в электронной почте с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

``` python



\# Create a instance of MailMessage class

message = self.MailMessage()

\# Set subject of the message

message.setSubject("New message created by Aspose.Email for Java")

mail_address = self.MailAddress

\# Set Html body

message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

    "<font color=blue>This line is in blue color</font>")

\# Set sender information

message.setFrom(self.MailAddress("from@domain.com", "Sender Name", False))

\# Add TO recipients

message.getTo().addMailAddress(self.MailAddress("to1@domain.com", "Recipient 1", False))

\# Adding attachment

\# Load an attachment

attachment = self.Attachment(self.dataDir + "1.txt")

\# Add attachment in instance of MailMessage class

message.addAttachment(attachment)

\# Save message to disc

messageFormat = self.MessageFormat

message.save(self.dataDir + "Add-Attachment.msg", messageFormat.getMsg())

\# Display Status

print "Added attachment successfully."

```
## **Загрузить рабочий код**
Download **Управление вложениями в сообщении электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
