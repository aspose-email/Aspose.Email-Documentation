---
title: "Отображение информации об электронной почте на экране в Jython"
url: /ru/java/displaying-email-information-on-screen-in-jython/
weight: 30
type: docs
---

## **Aspose.Email - отображение информации об электронной почте**
Для отображения информации об электронной почте с помощью **Aspose.Электронная почта Java для Mython**, просто вызовите **GetEmailInfo** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MessageFormat

class GetEmailInfo:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/GetEmailInfo/'



        # Create MailMessage instance by loading an Eml file

        message_format = MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

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





if __name__ == '__main__':       

    GetEmailInfo()

```
## **Загрузить рабочий код**
Download **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
