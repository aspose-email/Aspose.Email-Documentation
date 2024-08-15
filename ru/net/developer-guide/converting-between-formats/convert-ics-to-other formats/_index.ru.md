---
title: "Конвертируйте ICS в другие форматы"
url: /ru/net/converting-between-formats/convert-ics-to-other-formats
weight: 60
type: docs
---

## **Конвертируйте ICS в EML**

Для представления календарных событий или встреч в Aspose.Email есть [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) класс. Следующий пример кода демонстрирует процесс преобразования ICS в EML:

1. Загрузите файл ICS для конвертации с помощью [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Создайте новый [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) объект для хранения данных календаря.
3. Добавьте встречу из файла ICS в EML в качестве альтернативного представления, используя [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Сохраните файл EML с преобразованными данными, используя [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод с [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/emlsaveoptions/#emlsaveoptions-constructor) указав тип сохранения как EMLFormat.


```cs
// load the ICS file to be converted
var ics = Calendar.Appointment.Load("My File.ics");
// create an EML
var eml = new MailMessage();
// add appointment to EML
eml.AlternateViews.Add(ics.RequestApointment());
// save the EML
eml.Save("Saved File.eml", new EmlSaveOptions(MailMessageSaveType.EmlFormat));
```

## **Конвертируйте ICS в EMLX**

Чтобы преобразовать файл ICS в формат eMLX, следуйте инструкциям из [Конвертируйте ICS в EML](#convert-ics-to-eml) статью и сохраните файл.emlx, как показано в следующей строке кода:

```cs
// save as a EMLX
eml.Save("Saved File.emlx", new EmlSaveOptions(MailMessageSaveType.EmlxFormat));
```

## **Конвертируйте ICS в HTML**

Следующий пример кода демонстрирует процесс преобразования:

1. Загрузите файл ICS для конвертации с помощью [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Создайте новый [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) объект для хранения данных календаря.
3. Добавьте встречу из файла ICS в EML в качестве альтернативного представления, используя [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Сохраните файл EML с преобразованными данными, используя [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод с [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) чтобы предоставить параметры форматирования сохраненного HTML-файла. В данном конкретном случае [HtmlFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) используется для включения заголовка HTML в выходной файл, в то время как [HtmlFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) используется для отображения любых календарных событий, содержащихся в сообщении EML, в удобном для отображения формате.

```cs
// load the ICS file to be converted
var ics = Aspose.Email.Calendar.Appointment.Load("My File.ics");
// create an EML
var eml = new MailMessage();
// add appointment to EML
eml.AlternateViews.Add(ics.RequestApointment());
// save EML as a HTML
eml.Save("Saved File.html", new HtmlSaveOptions { HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderCalendarEvent });
```

Используйте другие значения и свойства [HtmlFormatOptions](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) перечисление и [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) класс для установки необходимых параметров формата.


## **Конвертируйте ICS в MBOX**

Следующий пример кода демонстрирует процесс преобразования ICS в MBOX. Он загружает файл ICS, создает сообщение EML, добавляет сведения о встрече из файла ICS в сообщение EML, а затем записывает сообщение EML в файл хранилища MBOX.

1. Загрузите файл ICS для конвертации с помощью [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Создайте новый [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) объект для хранения данных календаря.
3. Добавьте встречу из файла ICS в EML в качестве альтернативного представления, используя [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Создайте новый объект MboxRDStorageWriter.
5. Добавьте сообщение EML в хранилище, записав содержимое сообщения в формате MBOX в указанный файл MBOX.


```cs
// load the ICS file to be converted
var ics = Aspose.Email.Calendar.Appointment.Load("My File.ics");
// create an EML
var eml = new MailMessage();
// add appointment to EML
eml.AlternateViews.Add(ics.RequestApointment());
// create an MBOX storage
using var mboxStorage = new MboxrdStorageWriter("Saved File.mbox" , false);
// add EML to MBOX storage
mboxStorage.WriteMessage(eml);
```

## **Конвертируйте ICS в MHTML**

Следующий пример кода демонстрирует представление всех этих этапов процесса преобразования с использованием библиотеки Aspose.Email для .NET:

1. Загрузите файл ICS для конвертации с помощью [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Создайте новый [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) объект для хранения преобразованных данных.
3. Добавьте встречу из файла ICS в EML в качестве альтернативного представления, используя [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Сохраните файл EML с преобразованными данными, используя [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) метод с [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) для предоставления опций сохранения файла MHTML. В данном конкретном случае [MhtFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) используется для включения заголовка сообщения электронной почты в выходной файл, в то время как [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) используется для отображения любых календарных событий, содержащихся в сообщении EML, в удобном для отображения формате.


```cs
// load the ICS file to be converted
var ics = Aspose.Email.Calendar.Appointment.Load("My File.ics");
// create an EML
var eml = new MailMessage();
// add appointment to EML
eml.AlternateViews.Add(ics.RequestApointment());
// save EML as a MHTML
eml.Save("Saved File.mht", new MhtSaveOptions{MhtFormatOptions = MhtFormatOptions.WriteHeader | MhtFormatOptions.RenderCalendarEvent});
```

Такой подход гарантирует, что преобразованный файл MHTML сохраняет сведения и форматирование событий календаря, обеспечивая эффективный обмен и просмотр на различных платформах и почтовых клиентах.

Не стесняйтесь использовать другие значения и свойства [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) перечисление и [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) класс для установки необходимых параметров формата.

## **Конвертируйте ICS в MSG**

Преобразование файлов ICS (iCalendar) в формат MSG целесообразно для лучшей совместимости с Microsoft Outlook, поскольку файлы MSG обычно используются для хранения сообщений электронной почты, встреч и других данных, связанных с Outlook. В следующем примере кода показано, как загрузить файл ICS, изменить его содержимое и сохранить его как файл MSG без потери данных или форматирования:

1. Загрузите файл ICS с помощью [Calendar.Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) и создайте [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) объект из календарных данных, хранящихся в файле.
2. Позвоните [Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) метод на объекте Appointment для преобразования и сохранения загруженных данных о встрече из файла ICS в файл MSG в указанном месте.

```cs
// load the ICS file to be converted
// save ICS as a MSG
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save("Saved File.msg", AppointmentSaveFormat.Msg);
```

## **Конвертируйте ICS в OFT**

Процесс включает загрузку файлов ICS и сохранение их в виде файлов MSG с последующим преобразованием в формат OFT:

1. Создайте новый объект потока для хранения данных о встречах в памяти.
2. Загрузите данные о встрече из файла ICS. Сохраните данные о встрече в потоковом объекте в формате MSG с помощью метода Save ().
3. Загрузите данные о встрече из потока, создав новый объект MapiMessage с помощью [MapiMessage.Load()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load) method.
4. Сохраните загруженные данные MapiMessage в виде файла шаблона Outlook, используя [Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) метод с предоставленными параметрами формата SaveOptions.defaultOft.

```cs
// load the ICS file to be converted
// save ICS as a MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// save MSG as an OFT
MapiMessage.Load(ms).Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Конвертировать ICS в OST**

Aspose.Email предоставляет возможность загрузить файл ICS, сохранить его как файл MSG, затем открыть файл OST, получить доступ к папкам календаря в файле и легко добавить файлы MSG в папку календаря:

1. Создайте поток для хранения данных о встречах.
2. Загрузите данные о встрече из файла ICS с помощью [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) метод и сохраните его в потоке в формате MSG с помощью [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) method.
3. Загрузите файл личного хранилища, используя [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) метод [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.
4. Извлеките папку с календарем из файла личного хранилища с помощью [PersoanlStorage.GetPredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getpredefinedfolder/) method.
5. Используйте [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) метод добавления сообщения о встрече в папку календаря в файле OST.

```cs
// load the ICS file to be converted
// save ICS as a MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// open an OST file
using var pst = PersonalStorage.FromFile("Saved File.ost");
// get a calendar folder
var calendarFolder = pst.GetPredefinedFolder(StandardIpmFolder.Appointments);
// add MSG to the calendar folder
calendarFolder.AddMessage(MapiMessage.Load(msgStream));
```

## **Конвертировать ICS в PST**


Следующий пример кода демонстрирует процесс преобразования:

1. Создайте трансляцию для хранения данных о встречах.
2. Загрузите данные о встрече из файла ICS с помощью [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) метод и сохраните его в потоке в формате MSG с помощью [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) method.
3. Создайте новый файл PST с именем файла, используя [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method.
4. Создайте папку с календарем в файле PST для хранения встреч с помощью [CreatePredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/createpredefinedfolder/#createpredefinedfolder) method.
5. Добавьте сообщение о встрече в папку календаря в файле PST, используя [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method.

```cs
// load the ICS file to be converted
// save ICS as a MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// create a PST file
using var pst = PersonalStorage.Create("Saved File.pst", FileFormatVersion.Unicode);
// create a calendar folder
var calendarFolder = pst.CreatePredefinedFolder("Calendar", StandardIpmFolder.Appointments);
// add MSG to the calendar folder
calendarFolder.AddMessage(MapiMessage.Load(msgStream));
```
