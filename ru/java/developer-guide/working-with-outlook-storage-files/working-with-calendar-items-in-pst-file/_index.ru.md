---
title: "Работа с элементами календаря в файле PST"
url: /ru/java/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---

## **Добавление MapiCalendar в PST**

[Создайте новый PST, добавьте подпапки и сообщения](/email/java/create-new-pst-add-sub-folders-and-messages/) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) в подпапку Calendar созданного или загруженного файла PST.

Ниже приведены шаги по добавлению [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) в PST:

1. Создайте [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) object.
1. Установите [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) свойства с использованием конструктора и методов.
1. Создайте PST, используя [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-) method.
1. Создайте предварительно определенную папку (календарь) в корне файла PST, открыв корневую папку и вызвав [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

В приведенном ниже фрагменте кода показано, как создать [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) а затем добавьте его в папку «Календарь» вновь созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiCalendarToPST-.java" >}}

## **Сохранение элементов календаря из Outlook PST на диск в формате ICS**

В этой статье показано, как получить доступ к элементам календаря из файла Outlook PST и сохранить календарь на диск в формате ICS. Он использует [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) and [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) занятия для получения информации о календаре.

Ниже приведены шаги по сохранению элементов календаря:

1. Загрузите файл PST в [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class.
1. Перейдите в папку «Календарь».
1. Получите содержимое папки «Календарь», чтобы получить коллекцию сообщений.
1. Просмотрите коллекцию сообщений.
1. Позвоните [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) способ получения контактной информации в [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) class.
1. Позвоните [MapiCalendar.save()](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/#save-java.io.OutputStream-) метод сохранения элемента календаря на диск в формате ICS.

Приведенная ниже программа загружает файл PST с диска и сохраняет все элементы календаря в формате ICS. Затем файлы ICS можно использовать в любой другой программе, которая может загрузить стандартный файл календаря ICS. Если вы откроете какой-либо файл ICS в Microsoft Outlook, он будет выглядеть так, как показано на скриншоте ниже.

|![todo:image_alt_text](https://i.imgur.com/OhnGEXj.png)|
|: - |
|**Рис.: Элемент календаря, сохраненный с помощью Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveCalendarItemsFromOutlookPSTToDiskInICSFormat-.java" >}}

## **Извлечение элементов календаря из файла PST**

Класс MAPICalendar представляет собой элемент календаря в формате Microsoft Outlook MAPI. Извлеките сообщение из файла PST и преобразуйте его в элемент сообщения MAPI. Следующий пример кода извлекает элемент календаря из файла PST и преобразует его в объект MapicaLendar для дальнейшей обработки или обработки:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();
```
## **Сохраните элементы календаря в формате ICS с оригинальной отметкой времени**

Используйте приведенный выше пример кода, чтобы извлечь элемент календаря из файла PST, а затем указать дополнительные параметры для сохранения его как ICS с исходной меткой времени, используя [setKeepOriginalDateTimeStamp](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#setKeepOriginalDateTimeStamp-boolean-) метод [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) class:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();

if (cal != null) {
    MapiCalendarIcsSaveOptions so = new MapiCalendarIcsSaveOptions();
    so.setKeepOriginalDateTimeStamp(true);
    cal.save("cal.ics", so);
}
```
## **Изменить/удалить повторения из повторов**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ModifyDeleteOccurrencesFromRecurrence-ModifyDeleteOccurrencesFromRecurrence.java" >}}
