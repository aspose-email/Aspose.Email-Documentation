---
title: "Создание нового PST в PHP"
url: /ru/java/create-new-pst-in-php/
weight: 60
type: docs
---

## **Aspose.Email - Создание нового PST**
Чтобы создать новый PST с помощью **Aspose.Email Java для PHP**, просто вызовите модуль **CreatePST**. Здесь вы можете увидеть пример кода.

**PHP Код**

``` php

 # Создать экземпляр PersonalStorage

$personalStorage=new PersonalStorage();

$pst = $personalStorage->create($dataDir . "sample1.pst", 0);

\# Создать папку в корне pst

$pst->getRootFolder()->addSubFolder("myInbox");

\# Добавить сообщение в новосозданную папку

$mapi_message = new MapiMessage();

$pst->getRootFolder()->getSubFolder("myInbox")->addMessage($mapi_message->fromFile($dataDir . "Message.msg"));

print "PST успешно создан.".PHP_EOL;

```
## **Скачать работающий код**
Скачайте **Создание нового PST (Aspose.Email)** с любых из перечисленных ниже сайтов социального программирования:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_PHP/src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)
- [CodePlex](https://asposeemailjavaphp.codeplex.com/SourceControl/latest#src/aspose/email/ProgrammingOutlook/WorkingWithOutlookPersonalStorage/CreatePST.php)