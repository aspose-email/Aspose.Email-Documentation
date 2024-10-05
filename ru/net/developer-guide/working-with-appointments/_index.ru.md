---
title: "Работа с встречами"
url: /ru/net/working-with-appointments/
weight: 20
type: docs
---
## **Создание встречи**

Класс [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) в Aspose.Email для .NET можно использовать для создания новой встречи. В этой статье мы сначала создадим встречу и сохраним ее на диск в формате ICS.

### **Создание встречи и сохранение на диск в формате MSG или ICS**

Необходимы следующие шаги для создания встречи и сохранения ее на диск.

1. Создайте экземпляр класса [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) и инициализируйте его с помощью этого конструктора.
1. Передайте следующие аргументы в вышеуказанный конструктор:
   1. Место
   1. Резюме
   1. Описание
   1. Дата начала
   1. Дата окончания
   1. Организатор
   1. Участники
1. Вызовите метод [Save()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save/) и укажите имя файла и формат в аргументах.

Встречу можно открыть в Microsoft Outlook или любой программе, которая может загрузить файл ICS. Если файл открыт в Microsoft Outlook, он автоматически добавляет встречу в календарь Outlook.

Следующий код показывает, как создать и сохранить встречу на диск в формате ICS или MSG.

```cs
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Создайте и инициализируйте экземпляр класса Appointment
Appointment appointment = new Appointment(
    "Meeting Room 3 at Office Headquarters",// Место
    "Monthly Meeting",                      // Резюме
    "Please confirm your availability.",    // Описание
    new DateTime(2015, 2, 8, 13, 0, 0),     // Дата начала
    new DateTime(2015, 2, 8, 14, 0, 0),     // Дата окончания
    "from@domain.com",                      // Организатор
    "attendees@domain.com");                // Участники

// Сохраните встречу на диск в формате ICS            
appointment.Save(fileName + ".ics", new AppointmentIcsSaveOptions());
Console.WriteLine("Встреча успешно создана и сохранена на диск.");

// Сохраните встречу на диск в формате MSG
appointment.Save(fileName + ".msg", new AppointmentMsgSaveOptions(););
Console.WriteLine("Встреча успешно создана и сохранена на диск.");
```

### **Создание встречи с HTML-содержимым**

Вы можете указать альтернативные представления описания события в разных типах контента, используя заголовок X-ALT-DESC. Это позволяет получателям файла iCalendar выбрать представление, которое лучше всего соответствует их потребностям. Например, вы можете включить описание в простом текстовом формате, используя тип контента "text/plain", и HTML-описание, используя тип контента "text/html". Заголовок X-ALT-DESC добавляется для каждого альтернативного представления. Чтобы создать встречу с HTML-содержимым, установите свойство [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property).

Попробуйте следующий код для создания встречи с альтернативным HTML-описанием:

1. Создайте новый экземпляр класса Appointment.
2. Укажите необходимые параметры для конструктора Appointment:
   - Укажите место встречи.
   - Установите дату и время начала.
   - Установите дату и время окончания.
   - Укажите организатора.
   - Укажите участника.
3. Установите свойство [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) объекта встречи, указывая, что описание в HTML-формате.
4. Установите свойство Description объекта встречи на строку, отформатированную в HTML, заключенную в многострочную строку:
   - HTML-разметка включает блок `<style>`, определяющий класс CSS с именем "text" с параметрами шрифта.
   - HTML-тело содержит тег абзаца `<p>` с CSS-классом "text" и фактическим текстом приглашения.
5. Объект встречи теперь готов, и вы можете выполнять дальнейшие операции или сохранить его как файл iCalendar.

```cs
var appointment = new Appointment("Bygget 83",
    DateTime.UtcNow, // дата начала
    DateTime.UtcNow.AddHours(1), // дата окончания
    new MailAddress("TintinStrom@from.com", "Tintin Strom"), // организатор
    new MailAddress("AinaMartensson@to.com", "Aina Martensson")) // участник
{
    HtmlDescription = @"
    <html>
     <style type=""text/css"">
      .text {
             font-family:'Comic Sans MS';
             font-size:16px;
            }
     </style>
    <body>
     <p class=""text"">Привет, я рад пригласить вас на нашу вечеринку.</p>
    </body>
    </html>"
};
```

### **Создание черновика запроса на встречу**

В ранее опубликованных статьях было показано, как создавать и сохранять встречу в формате ICS. Часто требуется создать запрос на встречу в черновом режиме, чтобы основная информация была добавлена, а затем тот же черновик встречи можно было переслать другим пользователям для необходимых изменений в соответствии с индивидуальным использованием. Для сохранения встречи в черновом режиме свойство [MethodType](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/methodtype/) класса Appointment должно быть установлено в [AppointmentMethodType.Publish](https://reference.aspose.com/email/net/aspose.email.calendar/appointmentmethodtype/). Следующий код показывает, как создать черновик запроса на встречу.

```cs
string sender = "test@gmail.com";
string recipient = "test@email.com";

MailMessage message = new MailMessage(sender, recipient, string.Empty, string.Empty);

Appointment app = new Appointment(string.Empty, DateTime.Now, DateTime.Now, sender, recipient)
{
    MethodType = AppointmentMethodType.Publish
};

message.AddAlternateView(app.RequestApointment());

MapiMessage msg = MapiMessage.FromMailMessage(message);

// Сохраните встречу как черновик.
msg.Save(dstDraft);

Console.WriteLine(Environment.NewLine + "Черновик сохранен по адресу " + dstDraft);
```

### **Создание черновика встречи из текста**

Следующий код показывает, как создать черновик встречи из текста.

```cs
string ical = @"BEGIN:VCALENDAR
METHOD:PUBLISH
PRODID:-//Aspose Ltd//iCalender Builder (v3.0)//EN
VERSION:2.0
BEGIN:VEVENT
ATTENDEE;CN=test@gmail.com:mailto:test@gmail.com
DTSTART:20130220T171439
DTEND:20130220T174439
DTSTAMP:20130220T161439Z
END:VEVENT
END:VCALENDAR";

string sender = "test@gmail.com";
string recipient = "test@email.com";
MailMessage message = new MailMessage(sender, recipient, string.Empty, string.Empty);
AlternateView av = AlternateView.CreateAlternateViewFromString(ical, new ContentType("text/calendar"));
message.AlternateViews.Add(av);
MapiMessage msg = MapiMessage.FromMailMessage(message);
msg.Save(dataDir + "draft_out.msg");
```

### **Установка статуса участников встречи**

Aspose.Email для .NET API позволяет вам установить статус участников встречи при формировании сообщения-ответа. Это добавляет свойство PARTSTAT в файл ICS.

```cs
DateTime startDate = new DateTime(2011, 12, 10, 10, 12, 11),
         endDate = new DateTime(2012, 11, 13, 13, 11, 12);
MailAddress organizer = new MailAddress("aaa@amail.com", "Организатор");
MailAddressCollection attendees = new MailAddressCollection();
MailAddress attendee1 = new MailAddress("bbb@bmail.com", "Первый участник");
MailAddress attendee2 = new MailAddress("ccc@cmail.com", "Второй участник");

attendee1.ParticipationStatus = ParticipationStatus.Accepted;
attendee2.ParticipationStatus = ParticipationStatus.Declined;
attendees.Add(attendee1);
attendees.Add(attendee2);

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);
```

### **Настройка идентификатора продукта для iCalendar**

Aspose.Email для .NET API позволяет получать или устанавливать идентификатор продукта, который создал объект iCalendar.

```cs
string description = "Тестовое описание";
Appointment app = new Appointment("место", "тестовая встреча", description, DateTime.Today,
DateTime.Today.AddDays(1), "first@test.com", "second@test.com");

IcsSaveOptions saveOptions = IcsSaveOptions.Default;
saveOptions.ProductId = "Тестовая Корпорация";
app.Save(dataDir + "ChangeProdIdOfICS.ics", saveOptions);
```

## **Загрузка и сохранение встречи в формате ICS**

Кроме того, класс [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) может использоваться для загрузки встречи из файла ICS.

### **Загрузка встречи в формате ICS**

Чтобы загрузить встречу в формате ICS, необходимо выполнить следующие шаги:

1. Создайте экземпляр класса [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/).
1. Вызовите метод [Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load/) , предоставив путь к файлу ICS.
1. Прочитайте любое свойство, чтобы получить любую информацию о встрече (файле ICS).

Следующий код показывает, как загрузить встречу в формате ICS.

```cs
// Загрузите только что созданную и сохраненную на диске встречу и отобразите ее детали.
Appointment loadedAppointment = Appointment.Load(dstEmail);
Console.WriteLine(Environment.NewLine + "Детали загруженной встречи следующие:");
// Отобразите информацию о встрече на экране
Console.WriteLine("Резюме: " + loadedAppointment.Summary);
Console.WriteLine("Место: " + loadedAppointment.Location);
Console.WriteLine("Описание: " + loadedAppointment.Description);
Console.WriteLine("Дата начала: " + loadedAppointment.StartDate);
Console.WriteLine("Дата окончания: " + loadedAppointment.EndDate);
Console.WriteLine("Организатор: " + appointment.Organizer);
Console.WriteLine("Участники: " + appointment.Attendees);
Console.WriteLine(Environment.NewLine + "Встреча успешно загружена из " + dstEmail);
```

### **Загрузка и конвертация файла ICS в формат сообщения**

API позволяет легко конвертировать встречу в объект сообщения. Следующий пример кода показывает, как преобразовать запрос на встречу в MailMessage или MapiMessage:

```cs
var appointment = Appointment.Load("appRequest.ics");

var eml = appointment.ToMailMessage();
var msg = appointment.ToMapiMessage();
```

## **Чтение нескольких событий из файла ICS**

```cs
List<Appointment> appointments = new List<Appointment>();
CalendarReader reader = new CalendarReader(dataDir + "US-Holidays.ics");

while (reader.NextEvent())
{
    appointments.Add(reader.Current);
}
// работа с встречами...
```

## **Запись нескольких событий в файл ICS**

```cs
IcsSaveOptions saveOptions = new IcsSaveOptions();
saveOptions.Action = AppointmentAction.Create;
using (CalendarWriter writer = new CalendarWriter(dataDir + "WriteMultipleEventsToICS_out.ics", saveOptions))
{
    for (int i = 0; i < 10; i++)
    {
        Appointment app = new Appointment(string.Empty, DateTime.Now, DateTime.Now, "sender@domain.com", "receiver@domain.com");
        app.Description = "Тестовое сообщение " + i;
        app.Summary = "Тестовое резюме:" + i;
        writer.Write(app);
    }
}
```

## **Определение версии встречи**

Чтобы определить версию встречи, вы можете использовать свойство [Appointment.Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/#appointmentversion-property) класса [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class). Это свойство помогает определить, на каких версиях основаны их файлы, обеспечивая интеграцию с другими системами и приложениями.

Следующий пример кода показывает, как использовать это свойство в вашем проекте:

```cs
var app = Appointment.Load("meeting.ics");

if (app.Version == 1.0)
{
    // выполните действия
}
```