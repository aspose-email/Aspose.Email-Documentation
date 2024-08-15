---
title: "Извлечение заголовков электронной почты в Mython"
url: /ru/java/extracting-email-headers-in-jython/
weight: 40
type: docs
---

## **Aspose.Email - Извлечение заголовков писем**
Извлечение заголовков электронных писем с помощью **Aspose.Электронная почта Java для Mython**, просто вызовите **ExtractEmailHeaders** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

class ExtractEmailHeaders:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ExtractEmailHeaders/'



        # Initialize and Load an existing EML file by specifying the MessageFormat

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "Printing all Headers:"

        # Print out all the headers

        i=0

        while (i < message.getHeaders().getCount()):

            print message.getHeaders().get(i)

            i += 1





if __name__ == '__main__':       

    ExtractEmailHeaders()

```
## **Загрузить рабочий код**
Download **Извлечение заголовков электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
