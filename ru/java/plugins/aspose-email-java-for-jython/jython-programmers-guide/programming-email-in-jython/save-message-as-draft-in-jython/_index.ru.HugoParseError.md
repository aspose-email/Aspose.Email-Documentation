---
title: Сохранение сообщения как черновика в Jython
type: docs
weight: 60
url: /java/save-message-as-draft-in-jython/
---

## **Aspose.Email - Сохранение сообщения как черновика**
Чтобы сохранить сообщение как черновик с использованием **Aspose.Email Java для Jython**, просто вызовите модуль **SaveMessageAsDraft**. Здесь вы можете увидеть пример кода.

**Код Jython**

``` python

 from aspose-email import Settings

from com.aspose.email import MailMessage

from com.aspose.email import MailAddress

from com.aspose.email import MapiMessage

from com.aspose.email import MapiMessageFlags

class SaveMessageAsDraft:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingEmail/SaveMessageAsDraft/'



        # Создайте экземпляр класса MailMessage

        message = MailMessage()

            # Установите тему сообщения

        message.setSubject("Новое сообщение, созданное Aspose.Email для Java")

        mail_address = MailAddress

        # Установите Html тело

        message.setHtmlBody("<b>Эта строка жирным шрифтом.</b> <br/> <br/>" +

            "<font color=blue>Эта строка синего цвета</font>")

        # Установите информацию о отправителе

        message.setFrom(MailAddress("from@domain.com", "Имя отправителя", False))

        # Добавьте получателей в список TO

        message.getTo().add(MailAddress("to1@domain.com", "Получатель 1", False))

        message.getTo().add(MailAddress("to2@domain.com", "Получатель 2", False))

        # Создайте экземпляр MapiMessage и загрузите в него экземпляр MailMessage

        mapiMessage=MapiMessage()

        mapi_msg = mapiMessage.fromMailMessage(message)

        # Установите флаги MapiMessageFlags как UNSENT и FROMME

        mapi_message_flags = MapiMessageFlags()



        # Сохраните MapiMessage на диск

        mapi_msg.save(dataDir + "New-Draft.msg")

        # Вывод статуса

        print "Черновик успешно сохранен."





if __name__ == '__main__':        

    SaveMessageAsDraft()

```
## **Скачать рабочий код**
Скачайте **Сохранение сообщения как черновика (Aspose.Email)** с любого из упомянутых ниже сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)