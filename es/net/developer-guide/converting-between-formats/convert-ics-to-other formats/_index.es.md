---
title: "Convertir ICS a otros formatos"
url: /es/net/converting-between-formats/convert-ics-to-other-formats
weight: 60
type: docs
---

## **Convertir ICS a EML**

Para una representación de calendario, evento o cita, Aspose.Email tiene la [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) clase. El siguiente ejemplo de código muestra el proceso de conversión de ICS a EML:

1. Cargue el archivo ICS que se va a convertir mediante el [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Crear un nuevo [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) objeto para almacenar los datos del calendario.
3. Agregue la cita del archivo ICS a la EML como una vista alternativa mediante el [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Guarde el archivo EML con los datos convertidos mediante el [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método con el [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/emlsaveoptions/#emlsaveoptions-constructor) especificar el tipo de guardado como EMLFormat.


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

## **Convertir ICS a EMLX**

Para convertir un archivo ICS al formato eMLX, siga las instrucciones de [Convertir ICS a EML](#convert-ics-to-eml) y guarde el archivo.emlx como se muestra en la siguiente línea de código:

```cs
// save as a EMLX
eml.Save("Saved File.emlx", new EmlSaveOptions(MailMessageSaveType.EmlxFormat));
```

## **Convertir ICS a HTML**

El siguiente ejemplo de código muestra el proceso de conversión:

1. Cargue el archivo ICS que se va a convertir mediante el [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Crear un nuevo [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) objeto para almacenar los datos del calendario.
3. Agregue la cita del archivo ICS a la EML como una vista alternativa mediante el [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Guarde el archivo EML con los datos convertidos mediante el [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método con el [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) para proporcionar opciones de formato para el archivo HTML guardado. En este caso específico, el [HtmlFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) se usa para incluir el encabezado HTML en el archivo de salida, mientras que [HtmlFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) se usa para representar cualquier evento del calendario contenido en el mensaje EML en un formato adecuado para su visualización.

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

Utilice otros valores y propiedades del [HtmlFormatOptions](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) enumeración y [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) clase para establecer las opciones de formato según sea necesario.


## **Convertir ICS a MBOX**

El siguiente ejemplo de código muestra el proceso de conversión de ICS a MBOX. Carga un archivo ICS, crea un mensaje EML, agrega los detalles de la cita del archivo ICS al mensaje EML y, a continuación, escribe el mensaje EML en un archivo de almacenamiento MBOX.

1. Cargue el archivo ICS que se va a convertir mediante el [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Crear un nuevo [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) objeto para almacenar los datos del calendario.
3. Agregue la cita del archivo ICS a la EML como una vista alternativa mediante el [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Cree un nuevo objeto mboxRDStorageWriter.
5. Agregue el mensaje EML al almacenamiento escribiendo el contenido del mensaje en formato MBOX en el archivo MBOX especificado.


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

## **Convertir ICS a MHTML**

El siguiente ejemplo de código muestra la representación de todos estos pasos en el proceso de conversión mediante la biblioteca Aspose.Email for .NET:

1. Cargue el archivo ICS que se va a convertir mediante el [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Crear un nuevo [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) objeto para contener los datos convertidos.
3. Agregue la cita del archivo ICS a la EML como una vista alternativa mediante el [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Guarde el archivo EML con los datos convertidos mediante el [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) método con [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) para proporcionar opciones para guardar el archivo MHTML. En este caso específico, el [MhtFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) se usa para incluir el encabezado del mensaje de correo electrónico en el archivo de salida, mientras [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) se usa para representar cualquier evento del calendario contenido en el mensaje EML en un formato adecuado para su visualización.


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

Este enfoque garantiza que el archivo MHTML convertido conserve los detalles y el formato de los eventos del calendario, lo que permite compartir y ver de manera eficiente en varias plataformas y clientes de correo electrónico.

Siéntase libre de usar otros valores y propiedades del [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) enumeración y [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) clase para establecer las opciones de formato según sea necesario.

## **Convertir ICS a MSG**

La conversión de archivos ICS (iCalendar) al formato MSG es razonable para una mejor compatibilidad con Microsoft Outlook, ya que los archivos MSG se utilizan normalmente para almacenar mensajes de correo electrónico, citas y otros datos relacionados con Outlook. El siguiente ejemplo de código muestra cómo cargar un archivo ICS, manipular su contenido y guardarlo como un archivo MSG sin perder ningún dato ni formato:

1. Cargue el archivo ICS mediante el [Calendar.Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) y crea un [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) objeto de los datos del calendario almacenados en el archivo.
2. Llame al [Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) método del objeto Appointment para convertir y guardar los datos de citas cargados del archivo ICS en un archivo MSG en la ubicación especificada.

```cs
// load the ICS file to be converted
// save ICS as a MSG
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save("Saved File.msg", AppointmentSaveFormat.Msg);
```

## **Convertir ICS a OFT**

El proceso implica cargar archivos ICS y guardarlos como archivos MSG con una posterior conversión al formato OFT:

1. Cree un nuevo objeto de transmisión para almacenar los datos de las citas en la memoria.
2. Cargue los datos de la cita desde el archivo ICS. Guarde los datos de la cita en el objeto de transmisión en formato MSG mediante el método Save ().
3. Cargue los datos de las citas de la transmisión creando un nuevo objeto MAPIMessage mediante el [MapiMessage.Load()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load) method.
4. Guarde los datos de MapiMessage cargados como un archivo de plantilla de Outlook mediante el [Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) método con las opciones de formato proporcionadas SaveOptions.DefaultOft.

```cs
// load the ICS file to be converted
// save ICS as a MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// save MSG as an OFT
MapiMessage.Load(ms).Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Convertir ICS a OST**

Aspose.Email ofrece la funcionalidad de cargar un archivo ICS, guardarlo como archivo MSG y, a continuación, abrir un archivo OST, acceder a las carpetas de calendario dentro del archivo y agregar fácilmente archivos MSG a la carpeta de calendario:

1. Crea una transmisión para almacenar los datos de las citas.
2. Cargue los datos de la cita desde un archivo ICS mediante el [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) método y guárdalo en la transmisión en formato MSG con el [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) method.
3. Cargue el archivo de almacenamiento personal mediante el [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) método del [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.
4. Recupere la carpeta de calendario del archivo de almacenamiento personal con [PersoanlStorage.GetPredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getpredefinedfolder/) method.
5. Usa el [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) método para agregar el mensaje de la cita a la carpeta de calendario del archivo OST.

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

## **Convertir ICS a PST**


El siguiente ejemplo de código muestra el proceso de conversión:

1. Crea una secuencia para guardar los datos de la cita.
2. Cargue los datos de la cita desde un archivo ICS mediante el [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) método y guárdalo en la transmisión en formato MSG con el [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) method.
3. Cree un nuevo archivo PST con el nombre del archivo mediante el [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method.
4. Cree una carpeta de calendario dentro del archivo PST para almacenar las citas mediante el [CreatePredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/createpredefinedfolder/#createpredefinedfolder) method.
5. Agregue el mensaje de la cita a la carpeta de calendario del archivo PST mediante el [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method.

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
