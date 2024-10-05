---
title: Работа с MapiJournal в PST
type: docs
weight: 70
url: /java/working-with-mapijournal-in-pst/
---

## **Добавление MapiJournal в PST**

[Создание нового PST, добавление подпапок и сообщений](/email/java/create-new-pst-add-sub-folders-and-messages/) показано, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiJournal в подпапку Journal файла PST, который вы создали или загрузили. Ниже приведены шаги для добавления MapiJournal в PST:

1. Создайте объект [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/).
1. Установите свойства [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) с использованием конструктора и методов.
1. Создайте PST с помощью метода [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) .
1. Создайте предопределённую папку (Journals) в корне файла PST, получив доступ к корневой папке и затем вызвав метод [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) .

Ниже приведён код, который показывает, как создать [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) и затем добавить его в папку Journal вновь созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddMapiJournalToPST.java" >}}

## **Добавление вложений в MapiJournal**

Также возможно добавление вложений в элементы журнала MAPI. Код ниже показывает, как это сделать.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddAttachmentsToMapiJournal.java" >}}