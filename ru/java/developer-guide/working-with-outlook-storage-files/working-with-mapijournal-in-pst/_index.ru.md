---
title: "Работа с журналом MAPIjournal в формате PST"
url: /ru/java/working-with-mapijournal-in-pst/
weight: 70
type: docs
---

## **Добавление журнала MAPIjournal в PST**

[Создайте новый PST, добавьте подпапки и сообщения](/email/java/create-new-pst-add-sub-folders-and-messages/) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить MapiJournal в подпапку Journal созданного или загруженного файла PST. Ниже приведены шаги по добавлению MapiJournal в PST:

1. Создайте [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) object.
1. Установите [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) свойства с использованием конструктора и методов.
1. Создайте PST, используя [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.io.OutputStream-int-) method.
1. Создайте предварительно определенную папку (Журналы) в корне файла PST, открыв корневую папку и вызвав [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

В приведенном ниже фрагменте кода показано, как создать [MapiJournal](https://reference.aspose.com/email/java/com.aspose.email/mapijournal/) а затем добавьте его в папку Journal вновь созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddMapiJournalToPST.java" >}}

## **Добавление вложений в MapiJournal**

Также можно добавлять вложения к элементам журнала MAPI. В приведенном ниже коде показано, как это сделать.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiJournalToPST-AddAttachmentsToMapiJournal.java" >}}
