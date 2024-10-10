---
title: "Создание нового PST в Python"
url: /ru/java/create-new-pst-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Создание нового PST**
Чтобы создать новый PST с использованием **Aspose.Email Java для Python**, используйте следующий код.

**Python код**

``` python



\# Создайте экземпляр PersonalStorage

personalStorage = self.PersonalStorage

pst = personalStorage.create(self.dataDir + "sample1.pst", 0)

\# Создайте папку в корне pst

pst.getRootFolder().addSubFolder("myInbox")

\# Добавьте сообщение в недавно созданную папку

mapi_message = self.MapiMessage

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(self.dataDir + "Message.msg"))

print "PST успешно создан."

```
## **Скачать рабочий код**
Скачайте **Создание нового PST (Aspose.Email)** с любого из упомянутых ниже сайтов социального кодирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)