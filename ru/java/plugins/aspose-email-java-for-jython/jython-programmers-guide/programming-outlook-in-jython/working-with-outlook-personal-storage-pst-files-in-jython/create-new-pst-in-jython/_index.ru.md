---
title: "Создание нового PST в Jython"
url: /ru/java/create-new-pst-in-jython/
weight: 60
type: docs
---

## **Aspose.Email - Создание нового PST**
Чтобы создать новый PST с использованием **Aspose.Email Java для Jython**, просто вызовите модуль **CreatePST**. Здесь вы можете увидеть пример кода.

**Jython код**

``` python

 from aspose-email import Settings

from com.aspose.email import MapiMessage

from com.aspose.email import NoteColor

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

from java.util import Date

from java.util import Calendar

class CreatePST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST/'



        # Создать экземпляр PersonalStorage

        personalStorage=PersonalStorage()

        pst = personalStorage.create(dataDir + "sample1.pst", 0)

        # Создать папку на корневом уровне pst

        pst.getRootFolder().addSubFolder("myInbox")

        # Добавить сообщение в только что созданную папку

        mapi_message = MapiMessage()

        pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(dataDir + "Message.msg"))

        print "PST успешно создан."





if __name__ == '__main__':        

    CreatePST()

```
## **Скачать рабочий код**
Скачайте **Создание нового PST (Aspose.Email)** с любого из ниже упомянутых социальных кодовых сайтов:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)