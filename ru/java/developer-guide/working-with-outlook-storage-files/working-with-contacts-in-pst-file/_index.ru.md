---
title: "Работа с контактами в файле PST"
url: /ru/java/working-with-contacts-in-pst-file/
weight: 40
type: docs
---

## **Чтение нескольких контактов в формате VCard**

Ниже приведен образец кода, который демонстрирует, как прочитать файл VCF, проверить, содержит ли он несколько контактов, и, если да, загрузить контакты из файла в список объектов VCardContact. Код использует следующие методы:

- [isMultiContacts(InputStream stream)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#isMultiContacts-java.io.InputStream-) - Проверяет, содержит ли исходный поток несколько контактов.
- [loadAsMultiple(String filePath, Charset encoding)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.lang.String-java.nio.charset.Charset-) - Загружает список контактов из файла с несколькими контактами.
- [loadAsMultiple(InputStream stream, Charset encoding)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.io.InputStream-java.nio.charset.Charset-) - Загружает список контактов из потока с несколькими контактами.

```java
try (InputStream stream = new FileInputStream("test.vcf")) {
    if (VCardContact.isMultiContacts(stream)) {
        List<VCardContact> contacts = VCardContact.loadAsMultiple(stream, Charset.forName("utf-8"));
    }
}
```

## **Добавление контакта в PST**

[Создание нового PST, добавление подпапок и сообщений](java/create-new-pst-add-sub-folders-and-messages/) показало, как создать файл PST и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) в подпапку Контакты файла PST, который вы создали или загрузили. Ниже приведены шаги для добавления [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) в PST:

1. Создайте объект [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Установите свойства [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) с помощью различных конструкторов и методов.
1. Создайте PST с помощью метода [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-).
1. Создайте предварительно заданную папку (Контакты) в корне файла PST, получив доступ к корневой папке, а затем вызвав метод [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

Ниже приведен фрагмент кода, который показывает, как создать [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) и затем добавить его в папку Контакты нового файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiContactToPST-.java" >}}

## **Сохранение информации о контактах из файла PST в формате MSG**

В этой статье показано, как получить информацию о контакте из файла Microsoft Outlook PST и сохранить контакты на диск в формате MSG. Для этого используйте классы [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email/PersonalStorage) и [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/), чтобы получить и отобразить информацию о контакте.

Чтобы получить информацию о контакте:

1. Загрузите файл PST в классе [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
1. Просмотрите папку Контакты.
1. Получите содержимое папки Контакты, чтобы получить коллекцию сообщений.
1. Переберите коллекцию сообщений.
1. Вызовите метод [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) и затем метод [toMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMapiMessageItem--) чтобы получить информацию о контакте в классе [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Используйте свойства [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) для доступа к информации о контакте.
1. Вызовите метод [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) чтобы получить информацию о контакте в классе [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/).
1. Вызовите метод [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) для сохранения контакта на диск в формате MSG.

Ниже приведен пример кода, который извлекает всю информацию о контактах из файла PST и сохраняет ее на диск в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AccessContactInformationFromPSTFile-.java" >}}

## **Сохранение информации о контактах из Outlook PST на диск в формате vCard**

В этой статье показано, как получить информацию о контакте из файла Microsoft Outlook PST и сохранить контакт на диск в формате vCard (VCF). Она использует классы [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) и [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) для получения информации о контакте.

Ниже приведены шаги для получения информации о контактах:

1. Загрузите файл PST в классе [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
1. Просмотрите папку Контакты.
1. Получите содержимое папки Контакты для получения коллекции сообщений.
1. Переберите коллекцию сообщений.
1. Вызовите метод [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) для получения информации о контакте в классе [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/).
1. Используйте свойства класса [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) для доступа к информации о контакте.

Программа ниже загружает файл PST с диска и сохраняет все контакты в формате vCard (VCF). Файлы VCF затем можно использовать в любой другой программе, которая может загружать стандартные файлы контактов vCard. Если вы откроете любой файл VCF в Microsoft Outlook, он будет выглядеть как на скриншоте ниже.

|![todo:image_alt_text](https://i.imgur.com/EFt3p1Z.png)|
| :- |
|**Рисунок: vCard, сохраненная с помощью Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveContactsInformationFromOutlookPSTToDiskInvCardFormat-.java" >}}