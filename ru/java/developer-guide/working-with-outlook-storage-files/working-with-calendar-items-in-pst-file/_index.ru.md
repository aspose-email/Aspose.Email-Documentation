---
title: "Работа с элементами календаря в файле PST"
url: /ru/java/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---

## **Добавление MapiCalendar в PST**

[Создание нового PST, добавление подкаталогов и сообщений](/email/java/create-new-pst-add-sub-folders-and-messages/) показало, как создать файл PST и добавить к нему подкаталог. С помощью Aspose.Email вы можете добавить [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) в подкаталог Календаря файла PST, который вы создали или загрузили.

Ниже приведены шаги для добавления [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) в PST:

1. Создайте объект [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/).
1. Установите свойства [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) с помощью конструктора и методов.
1. Создайте PST с помощью метода [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-).
1. Создайте предопределенную папку (Календарь) в корне файла PST, получив доступ к корневой папке и затем вызвав метод [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

Ниже приведен фрагмент кода, который показывает, как создать [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) и затем добавить его в папку Календаря только что созданного файла PST.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiCalendarToPST-.java" >}}

## **Сохранение элементов календаря из Outlook PST на диск в формате ICS**

Эта статья показывает, как получить доступ к элементам календаря из файла Outlook PST и сохранить календарь на диск в формате ICS. Она использует классы [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) и [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) для получения информации о календаре.

Ниже приведены шаги для сохранения элементов календаря:

1. Загрузите файл PST в классе [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
1. Просмотрите папку Календаря.
1. Получите содержимое папки Календаря, чтобы получить коллекцию сообщений.
1. Пройдите по коллекции сообщений.
1. Вызовите метод [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) для получения информации о контакте в классе [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/).
1. Вызовите метод [MapiCalendar.save()](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/#save-java.io.OutputStream-) для сохранения элемента календаря на диск в формате ICS.

В приведенной ниже программе загружается файл PST с диска и сохраняются все элементы календаря в формате ICS. Файлы ICS затем могут быть использованы в любой другой программе, которая может загружать стандартный файл календаря ICS. Если вы откроете любой файл ICS в Microsoft Outlook, он будет выглядеть как на приведенном ниже скриншоте.

|![todo:image_alt_text](https://i.imgur.com/OhnGEXj.png)|
| :- |
|**Рисунок: Элемент календаря, сохраненный с помощью Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveCalendarItemsFromOutlookPSTToDiskInICSFormat-.java" >}}

## **Извлечение элементов календаря из файла PST**

Класс MapiCalendar представляет элемент календаря в формате MAPI Microsoft Outlook. Извлеките сообщение из файла PST и преобразуйте его в элемент сообщения MAPI. Приведенный ниже код извлекает элемент календаря из файла PST и преобразует его в объект MapiCalendar для дальнейшей манипуляции или обработки:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();
```

## **Сохранение элементов календаря в формате ICS с оригинальным временным штампом**

Используйте приведенный выше фрагмент кода для извлечения элемента календаря из файла PST, а затем укажите дополнительные параметры для сохранения его как ICS с оригинальным временным штампом, используя метод [setKeepOriginalDateTimeStamp](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#setKeepOriginalDateTimeStamp-boolean-) класса [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/):

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();

if (cal != null) {
    MapiCalendarIcsSaveOptions so = new MapiCalendarIcsSaveOptions();
    so.setKeepOriginalDateTimeStamp(true);
    cal.save("cal.ics", so);
}
```

## **Изменение/удаление вхождений из повторений**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ModifyDeleteOccurrencesFromRecurrence-ModifyDeleteOccurrencesFromRecurrence.java" >}}