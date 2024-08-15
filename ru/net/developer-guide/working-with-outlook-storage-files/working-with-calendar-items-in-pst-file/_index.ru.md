---
title: "Работа с элементами календаря в файле PST"
url: /ru/net/working-with-calendar-items-in-pst-file/
weight: 50
type: docs
---


## **Добавление MapiCalendar в PST**

[Создайте новый файл PST и добавьте подпапки](https://docs.aspose.com/email/ru/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) показал, как создать файл PST и добавить в него подпапку. С помощью Aspose.Email вы можете добавить MapicaLendar в подпапку Calendar созданного или загруженного вами PST-файла. Ниже приведены шаги по добавлению MapicaLendar в PST:

1. Создайте [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) object.
2. Установите [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) свойства с использованием конструктора и методов.
3. Создайте PST, используя [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Создайте предварительно определенную папку (календарь) в корне файла PST, открыв корневую папку и вызвав [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

В следующем фрагменте кода показано, как создать [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) а затем добавьте его в папку календаря вновь созданного файла PST.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cs" >}}

## **Сохранение элементов календаря из PST на диск в формате ICS**

В этой статье показано, как получить доступ к элементам календаря из файла Outlook PST и сохранить календарь на диск в формате ICS. Используйте [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) занятия для получения информации о календаре. Ниже приведены шаги по сохранению элементов календаря:

1. Загрузите файл PST в [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class.
1. Перейдите в папку «Календарь».
1. Получите содержимое папки «Календарь», чтобы получить коллекцию сообщений.
1. Просмотрите коллекцию сообщений.
1. Call [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) способ получения контактной информации в [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) class.
1. Позвоните [MapiCalendar.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/save/#save/) метод сохранения элемента календаря на диск в формате ICS.

Приведенная ниже программа загружает файл PST с диска и сохраняет все элементы календаря в формате ICS. Затем файлы ICS можно использовать в любой другой программе, которая может загрузить стандартный файл календаря ICS. Файл ICS, открытый в Microsoft Outlook, выглядит так, как показано на скриншоте ниже.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
|: - |
В следующем фрагменте кода показано, как экспортировать элементы календаря из Outlook PST в формат ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveCalendarItems-SaveCalendarItems.cs" >}}

### **Сохранение в виде ICS с исходной меткой времени**

Доступны следующие функции для сохранения элементов календаря в формате ICS с сохранением исходной информации о дате и времени:

- [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Позволяет указать дополнительные параметры при сохранении MapiCalendar в формате Ics.

- [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Позволяет сохранить исходное значение DateTimestamp в выходном файле.

Используйте приведенный ниже пример кода, чтобы реализовать функции в своем проекте:

```cs
var cal = pst.ExtractMessage(msgInfo).ToMapiMessageItem() as MapiCalendar;

if (cal != null)
{
  cal.Save("cal.ics", new MapiCalendarIcsSaveOptions() { KeepOriginalDateTimeStamp = true});
}
```

## **Изменить/удалить повторения из повторов**

Исключения можно добавлять к существующим рекурсиям с помощью Aspose.Email для .NET API. Следующий пример кода иллюстрирует использование этой функции.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ModifyDeleteOccurrenceInRecurrence-ModifyDeleteOccurrenceInRecurrence.cs" >}}
