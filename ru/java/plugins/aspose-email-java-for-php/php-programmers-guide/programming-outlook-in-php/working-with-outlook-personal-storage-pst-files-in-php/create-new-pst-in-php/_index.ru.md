---
title: "Создайте новый PST в PHP"
url: /ru/java/create-new-pst-in-php/
weight: 60
type: docs
---

## **Aspose.Email - Создайте новый PST**
Чтобы создать новый PST, используя **Aspose.Электронная почта Java для PHP**, просто вызовите **CreatePST** модуль. Здесь вы можете увидеть пример кода.

**Код PHP**

``` php

 # Create an instance of PersonalStorage

$personalStorage=new PersonalStorage();

$pst = $personalStorage->create($dataDir . "sample1.pst", 0);

\# Create a folder at root of pst

$pst->getRootFolder()->addSubFolder("myInbox");

\# Add message to newly created folder

$mapi_message = new MapiMessage();

$pst->getRootFolder()->getSubFolder("myInbox")->addMessage($mapi_message->fromFile($dataDir . "Message.msg"));

print "Created PST successfully.".PHP_EOL;

```
## **Загрузить рабочий код**
Download **Создайте новый PST (Aspose.Email)** с любого из нижеперечисленных сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
