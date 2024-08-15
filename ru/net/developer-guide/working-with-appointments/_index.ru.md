---
title: "Работа с назначениями"
url: /ru/net/working-with-appointments/
weight: 20
type: docs
---
## **Назначьте встречу**

The [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) класс в Aspose.Email for .NET можно использовать для создания новой встречи. В этой статье мы сначала создадим встречу и сохраним ее на диске в формате ICS.

### **Назначьте встречу и сохраните ее на диске в формате MSG или ICS**

Чтобы создать встречу и сохранить ее на диске, необходимо выполнить следующие шаги.

1. Создайте экземпляр [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) класс и инициализируйте его с помощью этого конструктора.
1. Передайте следующие аргументы в приведенном выше конструкторе
   1. Location
   1. Summary
   1. Description
   1. Дата начала
   1. Дата окончания
   1. Organizer
   1. Attendees
1. Позвоните [Save()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save/) метод и укажите имя и формат файла в аргументах.

Встречу можно открыть в Microsoft Outlook или любой программе, которая может загрузить файл ICS. Если файл открыт в Microsoft Outlook, встреча автоматически добавляется в календарь Outlook.

В следующем фрагменте кода показано, как создать и сохранить встречу на диске в формате ICS или MSG.

```cs
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET

// Create and initialize an instance of the Appointment class
Appointment appointment = new Appointment(
    "Meeting Room 3 at Office Headquarters",// Location
    "Monthly Meeting",                      // Summary
    "Please confirm your availability.",    // Description
    new DateTime(2015, 2, 8, 13, 0, 0),     // Start date
    new DateTime(2015, 2, 8, 14, 0, 0),     // End date
    "from@domain.com",                      // Organizer
    "attendees@domain.com");                // Attendees

// Save the appointment to disk in ICS format           
appointment.Save(fileName + ".ics", new AppointmentIcsSaveOptions());
Console.WriteLine("Appointment created and saved to disk successfully.");

// Save the appointment to disk in MSG format
appointment.Save(fileName + ".msg", new AppointmentMsgSaveOptions(););
Console.WriteLine("Appointment created and saved to disk successfully.");
```

### **Назначьте встречу с помощью HTML-контента**

С помощью заголовка X-ALT-DESC можно указать альтернативные представления описания события в различных типах контента. Это позволяет получателям файла iCalendar выбрать представление, наиболее соответствующее их потребностям. Например, вы можете включить текстовое описание, используя тип содержимого «текст/обычный», и описание HTML с использованием типа содержимого «текст/html». Для каждого альтернативного представления добавляется заголовок X-ALT-DESC. Чтобы назначить встречу с HTML-содержимым, задайте поле [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) property.

Попробуйте следующий пример кода, чтобы назначить встречу с альтернативным HTML-описанием:

1. Создайте новый экземпляр класса Appointment.
2. Укажите необходимые параметры конструктору Appointment:
   - Укажите место встречи.
   - Задайте дату и время начала.
   - Задайте дату и время окончания.
   - Укажите организатора.
   - Укажите участника.
3. Установите [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) свойство объекта встречи, указывающее, что описание находится в формате HTML.
4. Присвойте свойству Description объекта назначения строку в формате HTML, заключенную в многострочную строку:
   - HTML-разметка включает `<style>` блок, определяющий класс CSS с именем «текст» со стилями шрифтов.
   - Тело HTML содержит тег абзаца `<p>` с классом CSS «text» и фактическим пригласительным сообщением.
5. Теперь объект встречи готов, и вы можете выполнить дополнительные операции или сохранить его в виде файла iCalendar.

```cs
var appointment = new Appointment("Bygget 83",
    DateTime.UtcNow, // start date
    DateTime.UtcNow.AddHours(1), // end date
    new MailAddress("TintinStrom@from.com", "Tintin Strom"), // organizer
    new MailAddress("AinaMartensson@to.com", "Aina Martensson")) // attendee
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
     <p class=""text"">Hi, I'm happy to invite you to our party.</p>
    </body>
    </html>"
};
```
### **Создайте черновик запроса на встречу**

В наших предыдущих статьях было показано, как создать и сохранить встречу в формате ICS. Часто требуется создать заявку на прием в черновом режиме, чтобы добавить основную информацию, а затем отправить тот же черновик встречи другим пользователям для внесения необходимых изменений в соответствии с индивидуальными потребностями. Чтобы сохранить встречу в черновом режиме, нажмите [MethodType](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/methodtype/) для свойства класса Appointment должно быть установлено значение [AppointmentMethodType.Publish](https://reference.aspose.com/email/net/aspose.email.calendar/appointmentmethodtype/). В следующем фрагменте кода показано, как создать черновик запроса на встречу.

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

// Save the appointment as draft.
msg.Save(dstDraft);

Console.WriteLine(Environment.NewLine + "Draft saved at " + dstDraft);
```

### **Создание проекта встречи на основе текста**

В следующем фрагменте кода показано, как создать черновик встречи из текста. 

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

### **Установите статус участников для участников встречи**

Aspose.Email for .NET API позволяет задавать статус участников встречи при составлении ответного сообщения. Это добавляет свойство PARTSTAT в файл ICS.

```cs
DateTime startDate = new DateTime(2011, 12, 10, 10, 12, 11),
         endDate = new DateTime(2012, 11, 13, 13, 11, 12);
MailAddress organizer = new MailAddress("aaa@amail.com", "Organizer");
MailAddressCollection attendees = new MailAddressCollection();
MailAddress attendee1 = new MailAddress("bbb@bmail.com", "First attendee");
MailAddress attendee2 = new MailAddress("ccc@cmail.com", "Second attendee");

attendee1.ParticipationStatus = ParticipationStatus.Accepted;
attendee2.ParticipationStatus = ParticipationStatus.Declined;
attendees.Add(attendee1);
attendees.Add(attendee2);

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);
```

### **Настройка идентификатора продукта для iCalendar**

Aspose.Email for .NET API позволяет получить или установить идентификатор продукта, создавшего объект iCalendar.

```cs
string description = "Test Description";
Appointment app = new Appointment("location", "test appointment", description, DateTime.Today,
DateTime.Today.AddDays(1), "first@test.com", "second@test.com");

IcsSaveOptions saveOptions = IcsSaveOptions.Default;
saveOptions.ProductId = "Test Corporation";
app.Save(dataDir + "ChangeProdIdOfICS.ics", saveOptions);
```

## **Загрузите и сохраните встречу в формате ICS**

Кроме того, [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) класс можно использовать для загрузки встречи из файла ICS.

### **Загрузить встречу в формате ICS**

Чтобы загрузить встречу в формате ICS, необходимо выполнить следующие шаги:

1. Создайте экземпляр [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) class.
1. Позвоните [Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load/) метод, указав путь к файлу ICS.
1. Прочтите любой объект недвижимости, чтобы получить любую информацию о встрече (файл ICS).

В следующем фрагменте кода показано, как загрузить встречу в формате ICS.

```cs
// Load an Appointment just created and saved to disk and display its details.
Appointment loadedAppointment = Appointment.Load(dstEmail);
Console.WriteLine(Environment.NewLine + "Loaded Appointment details are as follows:");
// Display the appointment information on screen
Console.WriteLine("Summary: " + loadedAppointment.Summary);
Console.WriteLine("Location: " + loadedAppointment.Location);
Console.WriteLine("Description: " + loadedAppointment.Description);
Console.WriteLine("Start date: " + loadedAppointment.StartDate);
Console.WriteLine("End date: " + loadedAppointment.EndDate);
Console.WriteLine("Organizer: " + appointment.Organizer);
Console.WriteLine("Attendees: " + appointment.Attendees);
Console.WriteLine(Environment.NewLine + "Appointment loaded successfully from " + dstEmail);
```

### **Загрузите и конвертируйте файл ICS в формат сообщения**

API позволяет легко преобразовать встречу в объект сообщения. В следующем примере кода показано, как преобразовать запрос на встречу в MailMessage или MapiMessage:

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
//working with appointments...
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
        app.Description = "Test body " + i;
        app.Summary = "Test summary:" + i;
        writer.Write(app);
    }
}
```

## **Определите версию встречи**

Чтобы определить версию встречи, вы можете использовать [Appointment.Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/#appointmentversion-property) собственность [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) класс. Это свойство помогает определить, на какой версии основаны файлы, обеспечивая интеграцию с другими системами и приложениями.

В следующем примере кода показано, как реализовать это свойство в своем проекте:

```cs
var app = Appointment.Load("meeting.ics");

if (app.Version == 1.0)
{
    // do something
}
```
