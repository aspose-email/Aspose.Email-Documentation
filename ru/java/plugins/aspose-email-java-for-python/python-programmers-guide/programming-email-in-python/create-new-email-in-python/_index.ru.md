---
title: "Создайте новую электронную почту в Python"
url: /ru/java/create-new-email-in-python/
weight: 20
type: docs
---

## **Aspose.Email - Создайте новое письмо**
Чтобы создать новое электронное письмо, используя **Aspose.Электронная почта Java для Python**, Используйте следующий код.

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

message.getTo().addMailAddress(self.MailAddress("to2@domain.com", "Recipient 2", False))

\# Add CC recipients

message.getCC().addMailAddress(self.MailAddress("cc1@domain.com", "Recipient 3", False))

message.getCC().addMailAddress(self.MailAddress("cc2@domain.com", "Recipient 4", False))

\# Save message in EML and MSG formats

mail_message_save_type = self.MailMessageSaveType

message.save(self.dataDir + "Message.eml", mail_message_save_type.getEmlFormat())

message.save(self.dataDir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

\# Display Status

print "Created email messages Successfully."

```
## **Загрузить рабочий код**
Download **Создать новое электронное письмо (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
