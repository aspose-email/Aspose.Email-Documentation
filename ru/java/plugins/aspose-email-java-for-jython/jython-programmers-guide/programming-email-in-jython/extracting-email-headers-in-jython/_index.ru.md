---
title: "Извлечение заголовков электронной почты в Jython"
url: /ru/java/extracting-email-headers-in-jython/
weight: 40
type: docs
---

## **Aspose.Email - Извлечение заголовков электронной почты**
Чтобы извлечь заголовки электронной почты с помощью **Aspose.Email Java для Jython**, просто вызовите модуль **ExtractEmailHeaders**. Здесь вы можете увидеть пример кода.

**Jython Код**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

class ExtractEmailHeaders:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/ExtractEmailHeaders/'



        # Инициализируйте и загрузите существующий файл EML, указав формат сообщения

        mailMessage=MailMessage()

        message = mailMessage.load(dataDir + "Message.eml")

        print "Печать всех заголовков:"

        # Вывод всех заголовков

        i=0

        while (i < message.getHeaders().getCount()):

            print message.getHeaders().get(i)

            i += 1





if __name__ == '__main__':        

    ExtractEmailHeaders()

```
## **Скачать работающий код**
Скачайте **Извлечение заголовков электронной почты (Aspose.Email)** с любого из нижеупомянутых сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)