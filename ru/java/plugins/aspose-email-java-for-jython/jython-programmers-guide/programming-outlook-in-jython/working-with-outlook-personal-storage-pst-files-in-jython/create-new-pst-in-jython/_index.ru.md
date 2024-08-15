---
title: "Создайте новый PST в Mython"
url: /ru/java/create-new-pst-in-jython/
weight: 60
type: docs
---

## **Aspose.Email - Создайте новый PST**
Чтобы создать новый PST, используя **Aspose.Электронная почта Java для Mython**, просто вызовите **CreatePST** модуль. Здесь вы можете увидеть пример кода.

**Код Митона**

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



        # Create an instance of PersonalStorage

        personalStorage=PersonalStorage()

        pst = personalStorage.create(dataDir + "sample1.pst", 0)

        # Create a folder at root of pst

        pst.getRootFolder().addSubFolder("myInbox")

        # Add message to newly created folder

        mapi_message = MapiMessage()

        pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(dataDir + "Message.msg"))

        print "Created PST successfully."





if __name__ == '__main__':       

    CreatePST()

```
## **Загрузить рабочий код**
Download **Создайте новый PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
