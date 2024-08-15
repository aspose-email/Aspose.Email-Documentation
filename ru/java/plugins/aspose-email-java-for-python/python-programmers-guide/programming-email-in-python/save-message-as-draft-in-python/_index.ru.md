---
title: "Сохранить сообщение как черновик в Python"
url: /ru/java/save-message-as-draft-in-python/
weight: 70
type: docs
---

## **Aspose.Email - Сохранить сообщение как черновик**
Чтобы сохранить сообщение как черновик, используя **Aspose.Электронная почта Java для Python**, Используйте следующий код.

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

\# Create an instance of MapiMessage and load the MailMessag instance into it

mapiMessage = self.MapiMessage

mapi_msg = mapiMessage.fromMailMessage(message)

\# Set the MapiMessageFlags as UNSENT and FROMME

mapi_message_flags = self.MapiMessageFlags

\# Save the MapiMessage to disk

mapi_msg.save(self.dataDir + "New-Draft.msg")

\# Display Status

print "Draft saved Successfully."

```
## **Загрузить рабочий код**
Download **Сохранить сообщение как черновик (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)
