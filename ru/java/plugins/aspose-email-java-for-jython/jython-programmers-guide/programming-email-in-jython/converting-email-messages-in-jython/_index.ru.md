---
title: "Преобразование сообщений электронной почты в Jython"
url: /ru/java/converting-email-messages-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - конвертация сообщений электронной почты**
Для преобразования сообщений электронной почты с помощью **Aspose.Электронная почта Java для Mython**, позвоните **convert_eml_to_msg** метод **Converter** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import SaveOptions

class Converter:

    def __init__(self):



        # Loading EML, Saving to MSG

        self.convert_eml_to_msg()



    def convert_eml_to_msg(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/Converter/'



        # Initialize and Load an existing EML file by specifying the MessageFormat

        mailMessage = MailMessage()

        eml = mailMessage.load(dataDir + "Message.eml")

        # Save the Email message to disk in Unicode format

        saveOptions= SaveOptions

        eml.save(dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

        # Display Status

        print "Converted email to msg successfully."



if __name__ == '__main__':       

    Converter()

```
## **Загрузить рабочий код**
Download **Преобразование сообщений электронной почты (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)
