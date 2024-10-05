---
title: Управление вложениями в электронной почте на Jython
type: docs
weight: 50
url: /java/manage-attachments-in-email-message-in-jython/
---

## **Aspose.Email - Управление вложениями в электронной почте**
Чтобы добавить вложения в новое электронное сообщение с помощью **Aspose.Email Java for Jython**, вызовите метод **add_attachments** модуля **ManageAttachments**. Здесь вы можете увидеть пример кода.

**Код Jython**

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



        # Создание экземпляра класса MailMessage

        message =MailMessage()

        # Установка темы сообщения

        message.setSubject("Новое сообщение, созданное Aspose.Email для Java")

        mail_address = MailAddress

        # Установка HTML-содержимого

        message.setHtmlBody("<b>Эта строка выделена жирным шрифтом.</b> <br/> <br/>" +

            "<font color=blue>Эта строка синего цвета</font>")

        # Установка информации об отправителе

        message.setFrom(MailAddress("from@domain.com", "Имя отправителя", False))

        # Добавление получателей по адресу TO

        message.getTo().add(MailAddress("to1@domain.com", "Получатель 1", False))

        # Добавление вложения

        # Загрузка вложения

        attachment = Attachment(dataDir + "1.txt")

        # Добавление вложения в экземпляр класса MailMessage

        message.addAttachment(attachment)

        # Сохранение сообщения на диск

        messageFormat=MessageFormat()

        message.save(dataDir + "Add-Attachment.msg", messageFormat.getMsg())

        # Показать статус

        print "Вложение успешно добавлено."





if __name__ == '__main__':        

    ManageAttachments()

```
## **Скачать рабочий код**
Скачать **Управление вложениями в электронной почте (Aspose.Email)** с любого из упомянутых ниже социальных сайтов программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://asposeemailjavajython.codeplex.com/releases/view/620655)