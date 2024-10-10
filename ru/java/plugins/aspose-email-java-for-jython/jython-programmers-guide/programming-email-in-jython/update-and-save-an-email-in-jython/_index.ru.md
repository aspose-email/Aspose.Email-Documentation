---
title: "Обновление и сохранение электронной почты в Jython"
url: /ru/java/update-and-save-an-email-in-jython/
weight: 70
type: docs
---

## **Aspose.Email - Обновление и сохранение электронной почты**
Чтобы обновить и сохранить электронную почту с помощью **Aspose.Email Java для Jython**, просто вызовите модуль **UpdateEmail**. Здесь вы можете видеть пример кода.

**Код Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddressCollection

from com.aspose.email import MailMessageSaveType

class UpdateEmail:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/UpdateEmail/'



        # Инициализируйте и загрузите существующий MSG файл, указав формат сообщения

        mailMessage=MailMessage()

        email = mailMessage.load(dataDir + "Message.msg")

        # Инициализируйте строковую переменную для получения темы электронной почты

        subject = email.getSubject()

        # Добавьте немного информации к теме

        subject = subject + " Этот текст добавляется к существующей теме"

        # Установите тему электронной почты

        email.setSubject('Этот текст добавляется к существующей теме')

        # Инициализируйте строковую переменную для получения HTML-содержимого электронной почты

        body = email.getHtmlBody()

        # Добавьте немного информации к переменной Body

        body = body + "<br> Этот текст добавляется к существующему содержимому"

        # Установите содержимое электронной почты

        email.setHtmlBody(body)

        # Инициализируйте объект MailAddressCollection

        contacts = MailAddressCollection()

        # Получите список получателей электронной почты

        contacts = email.getTo()

        # Добавьте еще один адрес электронной почты в коллекцию

        contacts.add("to1@domain.com")

        # Установите коллекцию как список получателей электронной почты

        email.setTo(contacts)

        # Инициализируйте MailAddressCollection

        contacts = MailAddressCollection()

        # Получите список CC электронной почты

        contacts = email.getCC()

        # Добавьте еще один адрес электронной почты в коллекцию

        contacts.add("cc2@domain.com")

        # Установите коллекцию как список CC электронной почты

        email.setCC(contacts)

        # Сохраните сообщение электронной почты на диск, указав формат сообщения

        mailMessageSaveType=MailMessageSaveType

        email.save(dataDir + "UpdateMessage.msg", mailMessageSaveType.getOutlookMessageFormat())

        # Отобразите статус

        print "Сообщение электронной почты успешно обновлено."





if __name__ == '__main__':        

    UpdateEmail()

```
## **Скачать рабочий код**
Скачайте **Обновление и сохранение электронной почты (Aspose.Email)** с любого из нижеуказанных сайтов демонстрационного кода:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)