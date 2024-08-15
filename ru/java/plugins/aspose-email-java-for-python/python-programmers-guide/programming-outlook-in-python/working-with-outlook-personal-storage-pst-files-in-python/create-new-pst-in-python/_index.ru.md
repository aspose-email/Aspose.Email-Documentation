---
title: "Создайте новый PST на Python"
url: /ru/java/create-new-pst-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Создайте новый PST**
Для создания нового PST с помощью **Aspose.Электронная почта Java для Python**, Используйте следующий код.

**Код Python**

``` python



\# Create an instance of PersonalStorage

personalStorage = self.PersonalStorage

pst = personalStorage.create(self.dataDir + "sample1.pst", 0)

\# Create a folder at root of pst

pst.getRootFolder().addSubFolder("myInbox")

\# Add message to newly created folder

mapi_message = self.MapiMessage

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(self.dataDir + "Message.msg"))

print "Created PST successfully."

```
## **Загрузить рабочий код**
Download **Создайте новый PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)
