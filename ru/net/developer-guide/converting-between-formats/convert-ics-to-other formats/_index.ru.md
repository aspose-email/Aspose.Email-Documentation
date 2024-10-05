---
title: "Конвертировать ICS в другие форматы"
url: /ru/net/converting-between-formats/convert-ics-to-other-formats
weight: 60
type: docs
---

## **Конвертировать ICS в EML**

Для представления календарного события или записи Aspose.Email имеет класс [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class). Следующий пример кода демонстрирует процесс конвертации ICS в EML:

1. Загрузите файл ICS для конвертации с помощью метода [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Создайте новый объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) для хранения данных календаря.
3. Добавьте запись из файла ICS в EML как альтернативный вид с помощью метода [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Сохраните файл EML с конвертированными данными с помощью метода [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) с параметрами [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/emlsaveoptions/#emlsaveoptions-constructor), указывая тип сохранения как EmlFormat.

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

## **Конвертировать ICS в EMLX**

Чтобы конвертировать файл ICS в формат EMLx, следуйте инструкциям из статьи [Конвертировать ICS в EML](#convert-ics-to-eml) и сохраните файл .emlx, как показано в следующей строке кода:

```cs
// save as a EMLX
eml.Save("Saved File.emlx", new EmlSaveOptions(MailMessageSaveType.EmlxFormat));
```

## **Конвертировать ICS в HTML**

Следующий пример кода демонстрирует процесс конвертации:

1. Загрузите файл ICS для конвертации с помощью метода [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Создайте новый объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) для хранения данных календаря.
3. Добавьте запись из файла ICS в EML как альтернативный вид с помощью метода [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Сохраните файл EML с конвертированными данными с помощью метода [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) с параметрами [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class), чтобы предоставить параметры форматирования для сохраняемого HTML файла. В данном конкретном случае используется [HtmlFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration), чтобы включить HTML заголовок в выходной файл, в то время как [HtmlFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) используется для вывода любых календарных событий, содержащихся в EML сообщении, в формате, подходящем для отображения.

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

Используйте другие значения и свойства перечисления [HtmlFormatOptions](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) и класса [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class), чтобы установить параметры формата по мере необходимости.

## **Конвертировать ICS в MBOX**

Следующий пример кода демонстрирует процесс конвертации ICS в MBOX. Он загружает файл ICS, создает EML сообщение, добавляет детали записи из файла ICS в EML сообщение и затем записывает EML сообщение в файл хранения MBOX.

1. Загрузите файл ICS для конвертации с помощью метода [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Создайте новый объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) для хранения данных календаря.
3. Добавьте запись из файла ICS в EML как альтернативный вид с помощью метода [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Создайте новый объект MboxrdStorageWriter.
5. Добавьте EML сообщение в хранилище, записав содержимое сообщения в формате MBOX в указанный файл MBOX.

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

## **Конвертировать ICS в MHTML**

Следующий пример кода демонстрирует представление всех этих шагов в процессе конвертации с использованием библиотеки Aspose.Email для .NET:

1. Загрузите файл ICS для конвертации с помощью метода [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Создайте новый объект [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) для хранения конвертированных данных.
3. Добавьте запись из файла ICS в EML как альтернативный вид с помощью метода [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Сохраните файл EML с конвертированными данными с помощью метода [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) с [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class), чтобы предоставить параметры сохранения для MHTML файла. В данном конкретном случае используется [MhtFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration), чтобы включить заголовок сообщения электронной почты в выходной файл, в то время как [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) используется для вывода любых календарных событий, содержащихся в EML сообщении, в формате, подходящем для отображения.

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

Этот подход гарантирует, что конвертированный MHTML файл сохраняет детали и форматирование календарного события, обеспечивая эффективный обмен и просмотр на различных платформах и почтовых клиентах.

Пользуйтесь другими значениями и свойствами перечисления [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) и класса [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class), чтобы установить параметры формата по мере необходимости.

## **Конвертировать ICS в MSG**

Конвертация файлов ICS (iCalendar) в формат MSG имеет смысл для лучшей совместимости с Microsoft Outlook, так как файлы MSG обычно используются для хранения электронных сообщений, записей и других данных, связанных с Outlook. Следующий пример кода демонстрирует, как загрузить файл ICS, обработать его содержимое и сохранить его в файл MSG без потери данных или форматирования:

1. Загрузите файл ICS с помощью метода [Calendar.Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) и создайте объект [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) из данных календаря, хранящихся в файле.
2. Вызовите метод [Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) на объекте Appointment, чтобы конвертировать и сохранить загруженные данные записи из файла ICS в файл MSG в указанном месте.

```cs
// load the ICS file to be converted
// save ICS as a MSG
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save("Saved File.msg", AppointmentSaveFormat.Msg);
```

## **Конвертировать ICS в OFT**

Процесс включает в себя загрузку файлов ICS и сохранение их как файлов MSG с последующей конвертацией в формат OFT:

1. Создайте новый объект потока для хранения данных о записи в памяти.
2. Загрузите данные о записи из файла ICS. Сохраните данные о записи в объекте потока в формате MSG с помощью метода Save().
3. Загрузите данные о записи из потока, создав новый объект MapiMessage с использованием метода [MapiMessage.Load()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load) .
4. Сохраните загруженные данные MapiMessage как файл шаблона Outlook, используя метод [Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) с предоставленными параметрами формата SaveOptions.DefaultOft.

```cs
// load the ICS file to be converted
// save ICS as a MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// save MSG as an OFT
MapiMessage.Load(ms).Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Конвертировать ICS в OST**

Aspose.Email предоставляет функциональность для загрузки файла ICS, сохранения его как файла MSG, затем открытия файла OST, доступа к календарным папкам внутри файла и легкого добавления файлов MSG в календарную папку:

1. Создайте поток для хранения данных о записи.
2. Загрузите данные о записи из файла ICS с помощью метода [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) и сохраните его в потоке в формате MSG с помощью метода [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4).
3. Загрузите файл Личного Хранилища с использованием метода [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) класса [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
4. Извлеките календарную папку из файла Личного Хранилища с помощью метода [PersoanlStorage.GetPredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getpredefinedfolder/) .
5. Используйте метод [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) для добавления сообщения о записи в календарную папку в файле OST.

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

Следующий пример кода демонстрирует процесс конвертации:

1. Создайте поток для хранения данных о записи.
2. Загрузите данные о записи из файла ICS с помощью метода [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) и сохраните его в потоке в формате MSG с помощью метода [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4).
3. Создайте новый PST файл с именем файла с помощью метода [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4).
4. Создайте календарную папку внутри PST файла для хранения записей с помощью метода [CreatePredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/createpredefinedfolder/#createpredefinedfolder).
5. Добавьте сообщение о записи в календарную папку внутри PST файла с помощью метода [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) .

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