---
title: "Trabajando con Citas"
url: /es/net/working-with-appointments/
weight: 20
type: docs
---
## **Crear una Cita**

La [Clase de Cita](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) en Aspose.Email para .NET puede ser utilizada para crear una nueva cita. En este artículo, primero creamos una cita y la guardamos en un disco en formato ICS.

### **Crear una Cita y Guardar en un Disco en Formato MSG o ICS**

Los siguientes pasos son necesarios para crear una cita y guardarla en un disco.

1. Crea una instancia de la [Clase de Cita](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) e inicialízala con este constructor.
1. Pasa los siguientes argumentos en el constructor anterior
   1. Ubicación
   1. Resumen
   1. Descripción
   1. Fecha de inicio
   1. Fecha de fin
   1. Organizador
   1. Asistentes
1. Llama al [metodo Save()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save/) y especifica el nombre del archivo y el formato en los argumentos.

La cita puede ser abierta en Microsoft Outlook o cualquier programa que pueda cargar un archivo ICS. Si el archivo se abre en Microsoft Outlook, automáticamente agrega la cita en el calendario de Outlook.

El siguiente fragmento de código te muestra cómo crear y guardar una cita en un disco en formato ICS o MSG.

```cs
// Para ejemplos completos y archivos de datos, por favor ve a https://github.com/aspose-email/Aspose.Email-for-.NET

// Crear e inicializar una instancia de la clase Appointment
Appointment appointment = new Appointment(
    "Sala de reuniones 3 en la Sede de la Oficina",// Ubicación
    "Reunión Mensual",                      // Resumen
    "Por favor confirma tu disponibilidad.",    // Descripción
    new DateTime(2015, 2, 8, 13, 0, 0),     // Fecha de inicio
    new DateTime(2015, 2, 8, 14, 0, 0),     // Fecha de fin
    "from@domain.com",                      // Organizador
    "attendees@domain.com");                // Asistentes

// Guardar la cita en el disco en formato ICS            
appointment.Save(fileName + ".ics", new AppointmentIcsSaveOptions());
Console.WriteLine("Cita creada y guardada en el disco exitosamente.");

// Guardar la cita en el disco en formato MSG
appointment.Save(fileName + ".msg", new AppointmentMsgSaveOptions(););
Console.WriteLine("Cita creada y guardada en el disco exitosamente.");
```

### **Crear una Cita con Contenido HTML**

Puedes especificar representaciones alternativas de la descripción del evento en diferentes tipos de contenido utilizando el encabezado X-ALT-DESC. Esto permite a los destinatarios del archivo iCalendar elegir la representación que mejor se adapte a sus necesidades. Por ejemplo, puedes incluir una descripción en texto plano utilizando el tipo de contenido "text/plain" y una descripción HTML utilizando el tipo de contenido "text/html". El encabezado X-ALT-DESC se añade para cada representación alternativa. Para crear una cita con contenido HTML, establece la propiedad [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property).

Prueba el siguiente ejemplo de código para crear una cita con una descripción HTML alternativa:

1. Crea una nueva instancia de la clase Appointment.
2. Proporciona los parámetros necesarios al constructor de Appointment:
   - Especifica la ubicación de la cita.
   - Establece la fecha y hora de inicio.
   - Establece la fecha y hora de fin.
   - Especifica el organizador.
   - Especifica el asistente.
3. Establece la propiedad [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) del objeto cita, indicando que la descripción está en formato HTML.
4. Establece la propiedad Description del objeto cita a una cadena con formato HTML, encerrada dentro de una cadena multilinea:
   - La marca HTML incluye un bloque `<style>` que define una clase CSS llamada "text" con estilos de fuente.
   - El cuerpo HTML contiene una etiqueta de párrafo `<p>` con la clase CSS "text", y el mensaje de invitación real.
5. El objeto de cita ahora está listo, y puedes realizar más operaciones o guardarlo como un archivo iCalendar.

```cs
var appointment = new Appointment("Bygget 83",
    DateTime.UtcNow, // fecha de inicio
    DateTime.UtcNow.AddHours(1), // fecha de fin
    new MailAddress("TintinStrom@from.com", "Tintin Strom"), // organizador
    new MailAddress("AinaMartensson@to.com", "Aina Martensson")) // asistente
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
     <p class=""text"">Hola, me alegra invitarte a nuestra fiesta.</p>
    </body>
    </html>"
};
```
### **Crear una Solicitud de Cita en Borrador**

Se mostró en nuestros artículos anteriores cómo crear y guardar una cita en formato ICS. A menudo es necesario crear una solicitud de cita en modo borrador, de modo que se añada la información básica y luego la misma cita en borrador sea reenviada a otros usuarios para los cambios necesarios según usos individuales. Para guardar una cita en modo borrador, la [Propiedad MethodType](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/methodtype/) de la clase Appointment debe ser establecida a [AppointmentMethodType.Publish](https://reference.aspose.com/email/net/aspose.email.calendar/appointmentmethodtype/). El siguiente fragmento de código muestra cómo crear una solicitud de cita en borrador.

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

// Guardar la cita como borrador.
msg.Save(dstDraft);

Console.WriteLine(Environment.NewLine + "Borrador guardado en " + dstDraft);
```

### **Creación de una Cita Borrador desde Texto**

El siguiente fragmento de código te muestra cómo crear una cita borrador desde Texto. 

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

### **Establecer el Estado de Participantes de los Asistentes a la Cita**

Aspose.Email para .NET API te permite establecer el estado de los asistentes a la cita mientras se formula un mensaje de respuesta. Esto añade la propiedad PARTSTAT al archivo ICS.

```cs
DateTime startDate = new DateTime(2011, 12, 10, 10, 12, 11),
         endDate = new DateTime(2012, 11, 13, 13, 11, 12);
MailAddress organizer = new MailAddress("aaa@amail.com", "Organizador");
MailAddressCollection attendees = new MailAddressCollection();
MailAddress attendee1 = new MailAddress("bbb@bmail.com", "Primer asistente");
MailAddress attendee2 = new MailAddress("ccc@cmail.com", "Segundo asistente");

attendee1.ParticipationStatus = ParticipationStatus.Accepted;
attendee2.ParticipationStatus = ParticipationStatus.Declined;
attendees.Add(attendee1);
attendees.Add(attendee2);

Appointment target = new Appointment(location, startDate, endDate, organizer, attendees);
```

### **Personalizar el Identificador de Producto para iCalendar**

Aspose.Email para .NET API permite obtener o establecer el identificador de producto que creó el objeto iCalendar.

```cs
string description = "Descripción de Prueba";
Appointment app = new Appointment("ubicación", "cita de prueba", description, DateTime.Today,
DateTime.Today.AddDays(1), "first@test.com", "second@test.com");

IcsSaveOptions saveOptions = IcsSaveOptions.Default;
saveOptions.ProductId = "Corporación de Prueba";
app.Save(dataDir + "ChangeProdIdOfICS.ics", saveOptions);
```

## **Cargar y Guardar una Cita en Formato ICS**

Además, la [Clase de Cita](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) puede ser utilizada para cargar una cita desde un archivo ICS.

### **Cargar una Cita en Formato ICS**

Para cargar una cita en formato ICS, se requieren los siguientes pasos:

1. Crea una instancia de la [Clase de Cita](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) .
1. Llama al [método Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load/) proporcionando la ruta del archivo ICS.
1. Lee cualquier propiedad para obtener información de la cita (archivo ICS).

El siguiente fragmento de código te muestra cómo cargar una cita en formato ICS.

```cs
// Cargar una cita recién creada y guardada en el disco y mostrar sus detalles.
Appointment loadedAppointment = Appointment.Load(dstEmail);
Console.WriteLine(Environment.NewLine + "Los detalles de la cita cargada son los siguientes:");
// Mostrar la información de la cita en pantalla
Console.WriteLine("Resumen: " + loadedAppointment.Summary);
Console.WriteLine("Ubicación: " + loadedAppointment.Location);
Console.WriteLine("Descripción: " + loadedAppointment.Description);
Console.WriteLine("Fecha de inicio: " + loadedAppointment.StartDate);
Console.WriteLine("Fecha de fin: " + loadedAppointment.EndDate);
Console.WriteLine("Organizador: " + appointment.Organizer);
Console.WriteLine("Asistentes: " + appointment.Attendees);
Console.WriteLine(Environment.NewLine + "Cita cargada exitosamente desde " + dstEmail);
```

### **Cargar y Convertir un Archivo ICS a un Formato de Mensaje**

La API te permite convertir fácilmente una cita a un objeto mensaje. El siguiente ejemplo de código muestra cómo convertir una solicitud de cita en un MailMessage o MapiMessage:

```cs
var appointment = Appointment.Load("appRequest.ics");

var eml = appointment.ToMailMessage();
var msg = appointment.ToMapiMessage();
```

## **Leer Múltiples Eventos de un Archivo ICS**

```cs
List<Appointment> appointments = new List<Appointment>();
CalendarReader reader = new CalendarReader(dataDir + "US-Holidays.ics");

while (reader.NextEvent())
{
    appointments.Add(reader.Current);
}
//trabajando con las citas...
```

## **Escribir Múltiples Eventos en un Archivo ICS**

```cs
IcsSaveOptions saveOptions = new IcsSaveOptions();
saveOptions.Action = AppointmentAction.Create;
using (CalendarWriter writer = new CalendarWriter(dataDir + "WriteMultipleEventsToICS_out.ics", saveOptions))
{
    for (int i = 0; i < 10; i++)
    {
        Appointment app = new Appointment(string.Empty, DateTime.Now, DateTime.Now, "sender@domain.com", "receiver@domain.com");
        app.Description = "Cuerpo de prueba " + i;
        app.Summary = "Resumen de prueba:" + i;
        writer.Write(app);
    }
}
```

## **Determinar la Versión de la Cita**

Para determinar la versión de una cita, puedes usar la propiedad [Appointment.Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/#appointmentversion-property) de la [Clase de Cita](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class). Esta propiedad ayuda a determinar en qué versión se basan sus archivos, asegurando la integración con otros sistemas y aplicaciones.

El siguiente ejemplo de código muestra cómo implementar esta propiedad en tu proyecto:

```cs
var app = Appointment.Load("meeting.ics");

if (app.Version == 1.0)
{
    // hacer algo
}
```