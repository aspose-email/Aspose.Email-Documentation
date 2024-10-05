---
title: Создание нового письма в Jython
type: docs
weight: 20
url: /java/create-new-email-in-jython/
---

## **Aspose.Email - Создание нового письма**
Чтобы создать новое письмо с помощью **Aspose.Email Java for Jython**, просто вызовите модуль **CreateNewEmail**. Здесь вы можете увидеть пример кода.

**Код Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import MailMessageSaveType

class CreateNewEmail:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/CreateNewEmail/'



        # Создание экземпляра класса MailMessage

        message = MailMessage()

        # Установите тему сообщения

        message.setSubject("Новое сообщение, созданное Aspose.Email для Java")

        mail_address = MailAddress

        # Установите HTML тело

        message.setHtmlBody("<b>Эта строка выделена жирным шрифтом.</b> <br/> <br/>" +

            "<font color=blue>Эта строка синего цвета</font>")

        # Установите информацию об отправителе

        message.setFrom(MailAddress("from@domain.com", "Имя отправителя", False))

        # Добавьте получателей TO

        message.getTo().add(MailAddress("to1@domain.com", "Получатель 1", False))

        message.getTo().add(MailAddress("to2@domain.com", "Получатель 2", False))

        # Добавьте получателей CC

        message.getCC().add(MailAddress("cc1@domain.com", "Получатель 3", False))

        message.getCC().add(MailAddress("cc2@domain.com", "Получатель 4", False))

        # Сохраните сообщение в форматах EML и MSG

        mail_message_save_type = MailMessageSaveType()

        message.save(dataDir + "Message.eml", mail_message_save_type.getEmlFormat())

        message.save(dataDir + "Message.msg", mail_message_save_type.getOutlookMessageFormat())

        # Отобразите статус

        print "Email-сообщения успешно созданы."



if __name__ == '__main__':        

    CreateNewEmail()

```
## **Скачать работающий код**
Скачайте **Создание нового письма (Aspose.Email)** с любого из указанных ниже сайтов для социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)