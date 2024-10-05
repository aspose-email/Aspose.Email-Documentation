---
title: "Конвертация электронных сообщений в Jython"
url: /ru/java/converting-email-messages-in-jython/
weight: 10
type: docs
---

## **Aspose.Email - Конвертация электронных сообщений**
Чтобы конвертировать электронные сообщения с использованием **Aspose.Email Java для Jython**, вызовите метод **convert_eml_to_msg** модуля **Converter**. Вот пример кода.

**Код Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import SaveOptions

class Converter:

    def __init__(self):



        # Загрузка EML, сохранение в MSG

        self.convert_eml_to_msg()



    def convert_eml_to_msg(dataDir):



        dataDir = Settings.dataDir + 'ProgrammingEmail/Converter/'



        # Инициализация и загрузка существующего EML файла, указав формат сообщения

        mailMessage = MailMessage()

        eml = mailMessage.load(dataDir + "Message.eml")

        # Сохранение электронного сообщения на диск в формате Unicode

        saveOptions= SaveOptions

        eml.save(dataDir + "AnEmail.msg", saveOptions.getDefaultMsgUnicode())

        # Отображение статуса

        print "Электронное сообщение успешно преобразовано в msg."



if __name__ == '__main__':        

    Converter()

```
## **Скачать рабочий код**
Скачайте **Конвертацию электронных сообщений (Aspose.Email)** из любого из нижеупомянутых социальных сайтов кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)