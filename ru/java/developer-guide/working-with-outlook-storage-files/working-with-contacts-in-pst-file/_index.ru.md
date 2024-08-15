---
title: "Работа с контактами в файле PST"
url: /ru/java/working-with-contacts-in-pst-file/
weight: 40
type: docs
---

## **Чтение нескольких контактов в формате vCard**

В приведенном ниже примере кода показано, как прочитать файл VCF, проверить, содержит ли он несколько контактов, и, если да, загрузить контакты из файла в список объектов vCardContact. В коде используются следующие методы:

- [ISMultiContacts (поток входного потока)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#isMultiContacts-java.io.InputStream-) - Проверяет, содержит ли исходный поток несколько контактов.
- [LoadasMultiple (путь к строковому файлу, кодировка кодировки)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.lang.String-java.nio.charset.Charset-) - Загружает список контактов из мультиконтактного файла.
- [Загрузить как несколько (поток входного потока, кодировка кодировки кодировки)](https://reference.aspose.com/email/java/com.aspose.email/vcardcontact/#loadAsMultiple-java.io.InputStream-java.nio.charset.Charset-) - Загружает список контактов из многоконтактного потока.

```java
try (InputStream stream = new FileInputStream("test.vcf")) {
    if (VCardContact.isMultiContacts(stream)) {
        List<VCardContact> contacts = VCardContact.loadAsMultiple(stream, Charset.forName("utf-8"));
    }
}
```

## **Добавление контакта в PST**

[Создайте новый PST, добавьте подпапки и сообщения](java/create-new-pst-add-sub-folders-and-messages/) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) в подпапку «Контакты» созданного или загруженного файла PST. Ниже приведены шаги по добавлению [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) в PST:

1. Создайте [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) object.
1. Установите [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) свойства с использованием различных конструкторов и методов.
1. Создайте PST, используя [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-) method.
1. Создайте предварительно определенную папку (Контакты) в корне файла PST, открыв корневую папку и вызвав [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

В приведенном ниже фрагменте кода показано, как создать [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) а затем добавьте его в папку «Контакты» вновь созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiContactToPST-.java" >}}

## **Сохраните информацию о контактах из файла PST в формате MSG**

В этой статье показано, как получить доступ к контактной информации из файла Microsoft Outlook PST и сохранить контакты на диск в формате MSG. Для этого используйте [PersonalStorage](https://apireference.aspose.com/email/java/com.aspose.email/PersonalStorage) and [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) занятия для получения и отображения контактной информации.

Чтобы получить контактную информацию, выполните следующие действия:

1. Загрузите файл PST в [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class.
1. Перейдите в папку «Контакты».
1. Получите содержимое папки «Контакты», чтобы получить коллекцию сообщений.
1. Просмотрите коллекцию сообщений.
1. Call [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) а затем [toMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#toMapiMessageItem--) способ получения контактной информации в [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.
1. Use [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) свойства для доступа к контактной информации.
1. Позвоните [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) способ получения контактной информации в [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/) class.
1. Позвоните [MapiMessage.save()](https://reference.aspose.com/email/java/com.aspose.email/mapimessage/#save-java.lang.String-) метод сохранения контакта на диск в формате MSG.

Ниже приведен пример кода, который извлекает всю контактную информацию из файла PST и сохраняет ее на диске в формате MSG.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AccessContactInformationFromPSTFile-.java" >}}

## **Сохранение информации о контактах из Outlook PST на диск в формате vCard**

В этой статье показано, как получить доступ к контактной информации из файла Microsoft Outlook PST и сохранить контакт на диск в формате vCard (VCF). В нем используется [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) and [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) занятия для получения контактной информации.

Ниже приведены шаги для получения контактной информации:

1. Загрузите файл PST в [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class.
1. Перейдите в папку «Контакты».
1. Получите содержимое папки «Контакты», чтобы получить коллекцию сообщений.
1. Просмотрите коллекцию сообщений.
1. Позвоните [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) способ получения контактной информации в [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) class.
1. Используйте свойства [MapiContact](https://reference.aspose.com/email/java/com.aspose.email/mapicontact/) класс для доступа к контактной информации.

Приведенная ниже программа загружает файл PST с диска и сохраняет все контакты в формате vCard (VCF). Затем файлы VCF можно использовать в любой другой программе, которая может загрузить стандартный файл контактов vCard. Если вы откроете какой-либо файл VCF в Microsoft Outlook, он будет выглядеть так, как показано на скриншоте ниже.

|![todo:image_alt_text](https://i.imgur.com/EFt3p1Z.png)|
|: - |
|**Рис.: Карточка vCard, сохраненная с помощью Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveContactsInformationFromOutlookPSTToDiskInvCardFormat-.java" >}}
