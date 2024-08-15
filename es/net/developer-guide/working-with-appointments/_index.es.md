---
title: "Trabajando con citas"
url: /es/net/working-with-appointments/
weight: 20
type: docs
---
## **Crea una cita**

The [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) La clase en Aspose.Email para.NET se puede usar para crear una nueva cita. En este artículo, primero creamos una cita y la guardamos en un disco en formato ICS.

### **Crear una cita y guardarla en un disco en formato MSG o ICS**

Se requieren los siguientes pasos para crear una cita y guardarla en un disco.

1. Crea una instancia del [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) clase e inicialícela con este constructor.
1. Pase los siguientes argumentos en el constructor anterior
   1. Location
   1. Summary
   1. Description
   1. Fecha de inicio
   1. Fecha de finalización
   1. Organizer
   1. Attendees
1. Llame al [Save()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save/) método y especifique el nombre y el formato del archivo en los argumentos.

La cita se puede abrir en Microsoft Outlook o en cualquier programa que pueda cargar un archivo ICS. Si el archivo se abre en Microsoft Outlook, agrega automáticamente la cita al calendario de Outlook.

El siguiente fragmento de código muestra cómo crear y guardar una cita en un disco en formato ICS o MSG.

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

### **Crear una cita con contenido HTML**

Puede especificar representaciones alternativas de la descripción del evento en diferentes tipos de contenido mediante el encabezado X-ALT-DESC. Permite a los destinatarios del archivo iCalendar elegir la representación que mejor se adapte a sus necesidades. Por ejemplo, puede incluir una descripción en texto plano con el tipo de contenido «text/plain» y una descripción HTML con el tipo de contenido «text/html». El encabezado X-ALT-DESC se agrega para cada representación alternativa. Para crear una cita con contenido HTML, defina [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) property.

Prueba el siguiente ejemplo de código para crear una cita con una descripción HTML alternativa:

1. Cree una nueva instancia de la clase Appointment.
2. Proporcione los parámetros necesarios al constructor Appointment:
   - Especifique la ubicación de la cita.
   - Defina la fecha y la hora de inicio.
   - Defina la fecha y la hora de finalización.
   - Especifique el organizador.
   - Especifique el asistente.
3. Configure el [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) propiedad del objeto de cita, que indica que la descripción está en formato HTML.
4. Establezca la propiedad Description del objeto appointment en una cadena con formato HTML, incluida dentro de una cadena de líneas múltiples:
   - El marcado HTML incluye un `<style>` bloque que define una clase CSS denominada «texto» con estilos de fuente.
   - El cuerpo HTML contiene una etiqueta de párrafo `<p>` con la clase CSS «text» y el mensaje de invitación real.
5. El objeto de cita ya está listo y puede realizar más operaciones o guardarlo como un archivo iCalendar.

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
### **Crear un borrador de solicitud de cita**

En nuestros artículos anteriores se mostró cómo crear y guardar una cita en formato ICS. A menudo es necesario crear una solicitud de cita en modo borrador, de modo que se agrega la información básica y, a continuación, el mismo borrador de cita se envía a otros usuarios para que hagan los cambios necesarios según los usos individuales. Para guardar una cita en modo borrador, el [MethodType](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/methodtype/) la propiedad de la clase Appointment debe establecerse en [AppointmentMethodType.Publish](https://reference.aspose.com/email/net/aspose.email.calendar/appointmentmethodtype/). El siguiente fragmento de código muestra cómo crear un borrador de solicitud de cita.

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

### **Creación de borradores de citas a partir del texto**

El siguiente fragmento de código muestra cómo crear un borrador de cita desde Text. 

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

### **Establecer el estado de los participantes de los asistentes a la cita**

La API Aspose.Email para .NET le permite establecer el estado de los asistentes a la cita mientras formula un mensaje de respuesta. Esto agrega la propiedad PARTSTAT al archivo ICS.

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

### **Personalice el identificador de producto para iCalendar**

La API Aspose.Email para .NET permite obtener o establecer el identificador del producto que creó el objeto iCalendar.

```cs
string description = "Test Description";
Appointment app = new Appointment("location", "test appointment", description, DateTime.Today,
DateTime.Today.AddDays(1), "first@test.com", "second@test.com");

IcsSaveOptions saveOptions = IcsSaveOptions.Default;
saveOptions.ProductId = "Test Corporation";
app.Save(dataDir + "ChangeProdIdOfICS.ics", saveOptions);
```

## **Cargar y guardar una cita en formato ICS**

Además, el [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) la clase se puede usar para cargar una cita desde un archivo ICS.

### **Cargar una cita en formato ICS**

Para cargar una cita en formato ICS, se requieren los siguientes pasos:

1. Crea una instancia del [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) class.
1. Llame al [Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load/) método proporcionando la ruta del archivo ICS.
1. Lea cualquier propiedad para obtener información de la cita (archivo ICS).

El siguiente fragmento de código muestra cómo cargar una cita en formato ICS.

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

### **Cargar y convertir un archivo ICS a un formato de mensaje**

La API le permite convertir fácilmente una cita en un objeto de mensaje. El siguiente ejemplo de código muestra cómo convertir una solicitud de cita en un MailMessage o MapiMessage:

```cs
var appointment = Appointment.Load("appRequest.ics");

var eml = appointment.ToMailMessage();
var msg = appointment.ToMapiMessage();
```

## **Leer varios eventos del archivo ICS**

```cs
List<Appointment> appointments = new List<Appointment>();
CalendarReader reader = new CalendarReader(dataDir + "US-Holidays.ics");

while (reader.NextEvent())
{
    appointments.Add(reader.Current);
}
//working with appointments...
```

## **Escribir varios eventos en un archivo ICS**

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

## **Determine la versión de la cita**

Para determinar la versión de una cita, puede usar el [Appointment.Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/#appointmentversion-property) propiedad del [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) clase. Esta propiedad ayuda a determinar en qué versión se basan sus archivos, lo que garantiza la integración con otros sistemas y aplicaciones.

El siguiente ejemplo de código muestra cómo implementar esta propiedad en su proyecto:

```cs
var app = Appointment.Load("meeting.ics");

if (app.Version == 1.0)
{
    // do something
}
```
