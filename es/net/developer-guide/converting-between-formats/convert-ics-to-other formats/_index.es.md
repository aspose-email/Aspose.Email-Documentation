---
title: "Convertir ICS a otros formatos"
url: /es/net/converting-between-formats/convert-ics-to-other-formats
weight: 60
type: docs
---

## **Convertir ICS a EML**

Para la representación de un evento de calendario o cita, Aspose.Email tiene la clase [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class). El siguiente fragmento de código demuestra el proceso de conversión de ICS a EML:

1. Cargar el archivo ICS a convertir usando el método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crear un nuevo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para contener los datos del calendario.
3. Agregar la cita del archivo ICS al EML como una vista alternativa usando el método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Guardar el archivo EML con los datos convertidos utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) con las opciones [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/emlsaveoptions/#emlsaveoptions-constructor) especificando el tipo de guardado como EmlFormat.


```cs
// cargar el archivo ICS a convertir
var ics = Calendar.Appointment.Load("Mi Archivo.ics");
// crear un EML
var eml = new MailMessage();
// agregar cita al EML
eml.AlternateViews.Add(ics.RequestApointment());
// guardar el EML
eml.Save("Archivo Guardado.eml", new EmlSaveOptions(MailMessageSaveType.EmlFormat));
```

## **Convertir ICS a EMLX**

Para convertir un archivo ICS a formato EMLx, siga las instrucciones del artículo [Convertir ICS a EML](#convert-ics-to-eml) y guarde el archivo .emlx como se muestra en la siguiente línea de código:

```cs
// guardar como un EMLX
eml.Save("Archivo Guardado.emlx", new EmlSaveOptions(MailMessageSaveType.EmlxFormat));
```

## **Convertir ICS a HTML**

El siguiente fragmento de código demuestra el proceso de conversión:

1. Cargar el archivo ICS a convertir usando el método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crear un nuevo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para contener los datos del calendario.
3. Agregar la cita del archivo ICS al EML como una vista alternativa usando el método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Guardar el archivo EML con los datos convertidos utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) con las opciones [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) para proporcionar opciones de formato para el archivo HTML guardado. En este caso específico, se utiliza [HtmlFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) para incluir el encabezado HTML en el archivo de salida, mientras que [HtmlFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) se utiliza para renderizar cualquier evento de calendario contenido en el mensaje EML en un formato adecuado para su visualización.

```cs
// cargar el archivo ICS a convertir
var ics = Aspose.Email.Calendar.Appointment.Load("Mi Archivo.ics");
// crear un EML
var eml = new MailMessage();
// agregar cita al EML
eml.AlternateViews.Add(ics.RequestApointment());
// guardar EML como un HTML
eml.Save("Archivo Guardado.html", new HtmlSaveOptions { HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderCalendarEvent });
```

Utilice otros valores y propiedades de la enumeración [HtmlFormatOptions](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) y la clase [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) para establecer opciones de formato según sea necesario.

## **Convertir ICS a MBOX**

El siguiente fragmento de código demuestra el proceso de conversión de ICS a MBOX. Carga un archivo ICS, crea un mensaje EML, agrega los detalles de la cita desde el archivo ICS al mensaje EML y luego escribe el mensaje EML en un archivo de almacenamiento MBOX.

1. Cargar el archivo ICS a convertir usando el método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crear un nuevo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para contener los datos del calendario.
3. Agregar la cita del archivo ICS al EML como una vista alternativa usando el método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Crear un nuevo objeto MboxrdStorageWriter.
5. Agregar el mensaje EML al almacenamiento escribiendo el contenido del mensaje en formato MBOX en el archivo MBOX especificado.

```cs
// cargar el archivo ICS a convertir
var ics = Aspose.Email.Calendar.Appointment.Load("Mi Archivo.ics");
// crear un EML
var eml = new MailMessage();
// agregar cita al EML
eml.AlternateViews.Add(ics.RequestApointment());
// crear un almacenamiento MBOX
using var mboxStorage = new MboxrdStorageWriter("Archivo Guardado.mbox", false);
// agregar EML al almacenamiento MBOX
mboxStorage.WriteMessage(eml);
```

## **Convertir ICS a MHTML**

El siguiente fragmento de código demuestra la representación de todos estos pasos en el proceso de conversión utilizando la biblioteca Aspose.Email para .NET:

1. Cargar el archivo ICS a convertir usando el método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crear un nuevo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para contener los datos convertidos.
3. Agregar la cita del archivo ICS al EML como una vista alternativa usando el método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Guardar el archivo EML con los datos convertidos utilizando el método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) con [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) para proporcionar opciones de guardado para el archivo MHTML. En este caso específico, se utiliza [MhtFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) para incluir el encabezado del mensaje de correo electrónico en el archivo de salida, mientras que [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) se utiliza para renderizar cualquier evento de calendario contenido en el mensaje EML en un formato adecuado para su visualización.

```cs
// cargar el archivo ICS a convertir
var ics = Aspose.Email.Calendar.Appointment.Load("Mi Archivo.ics");
// crear un EML
var eml = new MailMessage();
// agregar cita al EML
eml.AlternateViews.Add(ics.RequestApointment());
// guardar EML como un MHTML
eml.Save("Archivo Guardado.mht", new MhtSaveOptions { MhtFormatOptions = MhtFormatOptions.WriteHeader | MhtFormatOptions.RenderCalendarEvent });
```

Este enfoque asegura que el archivo MHTML convertido retenga los detalles y el formato del evento del calendario, permitiendo un intercambio y visualización eficientes a través de diversas plataformas y clientes de correo electrónico.

Siéntase libre de usar otros valores y propiedades de la enumeración [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) y de la clase [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) para establecer opciones de formato según sea necesario.

## **Convertir ICS a MSG**

Convertir archivos ICS (iCalendar) a formato MSG es razonable para una mejor compatibilidad con Microsoft Outlook, ya que los archivos MSG se utilizan comúnmente para almacenar mensajes de correo electrónico, citas y otros datos relacionados con Outlook. El siguiente fragmento de código demuestra cómo cargar un archivo ICS, manipular su contenido y guardarlo como un archivo MSG sin perder ningún dato o formato:

1. Cargar el archivo ICS usando [Calendar.Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) y crear un objeto [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) a partir de los datos del calendario almacenados en el archivo.
2. Llamar al método [Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) en el objeto Appointment para convertir y guardar los datos de la cita cargada del archivo ICS en un archivo MSG en la ubicación especificada.

```cs
// cargar el archivo ICS a convertir
// guardar ICS como un MSG
Aspose.Email.Calendar.Appointment.Load("Mi Archivo.ics").Save("Archivo Guardado.msg", AppointmentSaveFormat.Msg);
```

## **Convertir ICS a OFT**

El proceso implica cargar archivos ICS y guardarlos como archivos MSG con una posterior conversión a formato OFT:

1. Crear un nuevo objeto de flujo para almacenar los datos de la cita en memoria.
2. Cargar los datos de la cita desde el archivo ICS. Guardar los datos de la cita en el objeto de flujo en formato MSG usando el método Save().
3. Cargar los datos de la cita desde el flujo creando un nuevo objeto MapiMessage usando el método [MapiMessage.Load()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load).
4. Guardar los datos del MapiMessage cargado como un archivo de plantilla de Outlook utilizando el método [Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) con las opciones de formato proporcionadas SaveOptions.DefaultOft.

```cs
// cargar el archivo ICS a convertir
// guardar ICS como un MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("Mi Archivo.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// guardar MSG como un OFT
MapiMessage.Load(ms).Save("Archivo Guardado.oft", SaveOptions.DefaultOft);
```

## **Convertir ICS a OST**

Aspose.Email proporciona funcionalidad para cargar un archivo ICS, guardarlo como un archivo MSG, luego abrir un archivo OST, acceder a las carpetas del calendario dentro del archivo y agregar fácilmente archivos MSG a la carpeta del calendario:

1. Crear un flujo para almacenar los datos de la cita.
2. Cargar los datos de la cita desde un archivo ICS usando el método [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) y guardarlo en el flujo en formato MSG con el método [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4).
3. Cargar el archivo de almacenamiento personal usando el método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) de la clase [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
4. Recuperar la carpeta del calendario del archivo de Almacenamiento Personal usando el método [PersoanlStorage.GetPredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getpredefinedfolder/) .
5. Usar el método [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) para agregar el mensaje de cita a la carpeta de calendario en el archivo OST.

```cs
// cargar el archivo ICS a convertir
// guardar ICS como un MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("Mi Archivo.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// abrir un archivo OST
using var pst = PersonalStorage.FromFile("Archivo Guardado.ost");
// obtener una carpeta de calendario
var calendarFolder = pst.GetPredefinedFolder(StandardIpmFolder.Appointments);
// agregar MSG a la carpeta de calendario
calendarFolder.AddMessage(MapiMessage.Load(msgStream));
```

## **Convertir ICS a PST**

El siguiente fragmento de código demuestra el proceso de conversión:

1. Crear un flujo para contener los datos de la cita.
2. Cargar los datos de la cita desde un archivo ICS usando el método [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) y guardarlo en el flujo en formato MSG con el método [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4).
3. Crear un nuevo archivo PST con el nombre del archivo usando el método [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4).
4. Crear una carpeta de calendario dentro del archivo PST para almacenar citas usando el método [CreatePredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/createpredefinedfolder/#createpredefinedfolder).
5. Agregar el mensaje de cita a la carpeta de calendario dentro del archivo PST usando el método [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) .

```cs
// cargar el archivo ICS a convertir
// guardar ICS como un MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("Mi Archivo.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// crear un archivo PST
using var pst = PersonalStorage.Create("Archivo Guardado.pst", FileFormatVersion.Unicode);
// crear una carpeta de calendario
var calendarFolder = pst.CreatePredefinedFolder("Calendario", StandardIpmFolder.Appointments);
// agregar MSG a la carpeta de calendario
calendarFolder.AddMessage(MapiMessage.Load(msgStream));
```