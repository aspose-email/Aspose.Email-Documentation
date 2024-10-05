---
title: "Отображение информации об электронной почте на экране в Jython"
url: /ru/java/displaying-email-information-on-screen-in-jython/
weight: 30
type: docs
---

## **Aspose.Email - Отображение информации об электронной почте**
Для отображения информации об электронной почте с использованием **Aspose.Email Java for Jython** просто вызовите модуль **GetEmailInfo**. Здесь вы можете увидеть пример кода.

**Код Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MessageFormat

class GetEmailInfo:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/GetEmailInfo/'



        # Создание экземпляра MailMessage путем загрузки файла Eml

        message_format = MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "От: " 

        print message.getFrom()

        print "Кому: " 

        print message.getTo()

        print "Тема: " 

        print message.getSubject()

        print "HtmlТело: " 

        print message.getHtmlBody()

        print "ТекстТело: " 

        print message.getTextBody()





if __name__ == '__main__':        

    GetEmailInfo()

```
## **Скачать рабочий код**
Скачайте **Отображение информации об электронной почте (Aspose.Email)** с любого из нижеупомянутых социальных кодов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)