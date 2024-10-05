---
title: Работа с элементами календаря в PST-файле
type: docs
weight: 50
url: /net/working-with-calendar-items-in-pst-file/
---


## **Добавление MapiCalendar в PST**

[Создание нового PST-файла и добавление подпапок](https://docs.aspose.com/email/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) показало, как создать PST-файл и добавить к нему подпапку. С помощью Aspose.Email вы можете добавить MapiCalendar в подпапку Календаря PST-файла, который вы создали или загрузили. Ниже приведены шаги для добавления MapiCalendar в PST:

1. Создайте объект [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/).
2. Установите свойства [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) с помощью конструктора и методов.
3. Создайте PST с помощью метода [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Создайте предопределенную папку (Календарь) в корне PST-файла, обратившись к корневой папке и затем вызвав метод [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

Следующий фрагмент кода показывает, как создать [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) и затем добавить его в папку календаря только что созданного PST-файла.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cs" >}}

## **Сохранение элементов календаря из PST на диск в формате ICS**

Эта статья показывает, как получить элементы календаря из файла Outlook PST и сохранить календарь на диск в формате ICS. Используйте классы [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) и [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) для получения информации о календаре. Ниже приведены шаги для сохранения элементов календаря:

1. Загрузите PST-файл в класс [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Просмотрите папку Календарь.
1. Получите содержимое папки Календарь, чтобы получить коллекцию сообщений.
1. Переберите коллекцию сообщений.
1. Вызовите метод [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/), чтобы получить информацию о контакте в классе [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/).
1. Вызовите метод [MapiCalendar.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/save/#save/), чтобы сохранить элемент календаря на диск в формате ICS.

Программа ниже загружает PST-файл с диска и сохраняет все элементы календаря в формате ICS. Файлы ICS затем можно использовать в любой другой программе, которая может загрузить стандартный файл календаря ICS. Открытый в Microsoft Outlook, файл ICS выглядит как на приведенном ниже скриншоте.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
Следующий фрагмент кода показывает, как экспортировать элементы календаря из Outlook PST в формат ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveCalendarItems-SaveCalendarItems.cs" >}}

### **Сохранение как ICS с оригинальной меткой времени**

Следующие функции доступны для сохранения элементов календаря в формате ICS с сохранением их оригинальной информации о дате и времени:

- [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Позволяет указывать дополнительные параметры при сохранении MapiCalendar в формат Ics. 

- [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Позволяет сохранить оригинальное значение DateTimeStamp в выходном файле.

Используйте приведенный ниже образец кода, чтобы реализовать функции в своем проекте:

```cs
var cal = pst.ExtractMessage(msgInfo).ToMapiMessageItem() as MapiCalendar;

if (cal != null)
{
  cal.Save("cal.ics", new MapiCalendarIcsSaveOptions() { KeepOriginalDateTimeStamp = true});
}
```

## **Изменение/удаление событий из повторений**

Исключения могут быть добавлены к существующим повторениям с использованием API Aspose.Email для .NET. Следующий образец кода иллюстрирует использование этой функции.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ModifyDeleteOccurrenceInRecurrence-ModifyDeleteOccurrenceInRecurrence.cs" >}}