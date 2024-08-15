---
title: "Управление вложениями в сообщении электронной почты в Jython"
url: /ru/java/manage-attachments-in-email-message-in-jython/
weight: 50
type: docs
---

## **Aspose.Email - Управление вложениями в сообщении электронной почты**
Чтобы добавить вложения в новое сообщение электронной почты, используя **Aspose.Электронная почта Java для Mython**, позвоните **add_attachments** метод **ManageAttachments** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import Attachment

from com.aspose.email import MessageFormat

class ManageAttachments:

    def __init__(self):



        self.add_attachments()



    def add_attachments(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ManageAttachments/'



        # Create a instance of MailMessage class

        message =MailMessage()

        # Set subject of the message

        message.setSubject("New message created by Aspose.Email for Java")

        mail_address = MailAddress

        # Set Html body

        message.setHtmlBody("<b>This line is in bold.</b> <br/> <br/>" +

            "<font color=blue>This line is in blue color</font>")

        # Set sender information

        message.setFrom(MailAddress("from@domain.com", "Sender Name", False))

        # Add TO recipients

        message.getTo().add(MailAddress("to1@domain.com", "Recipient 1", False))

        # Adding attachment

        # Load an attachment

        attachment = Attachment(dataDir + "1.txt")

        # Add attachment in instance of MailMessage class

        message.addAttachment(attachment)

        # Save message to disc

        messageFormat=MessageFormat()

        message.save(dataDir + "Add-Attachment.msg", messageFormat.getMsg())

        # Display Status

        print "Added attachment successfully."





if __name__ == '__main__':       

    ManageAttachments()

```
## **Загрузить рабочий код**
Download **Управление вложениями в сообщении электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
