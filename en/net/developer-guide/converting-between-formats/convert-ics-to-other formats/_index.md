---
title: Convert ICS Other Formats
ArticleTitle: Convert ICS Other Formats
type: docs
weight: 50
url: /net/converting-between-formats/convert-ics-to-other-formats
--- 

## **Convert ICS to EML**

For a calendar event or appointment representation, Aspose.Email has the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) class. The following code sample demonstrates the process of ICS to EML conversion:

1. Load the ICS file to be converted using the [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Create a new [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) object to hold the calendar data. 
3. Add the appointment from the ICS file to the EML as an alternate view using the [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method. 
4. Save the EML file with the converted data using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method with the [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/emlsaveoptions/#emlsaveoptions-constructor) specifying the save type as EmlFormat. 

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

## **Convert ICS to EMLX**

To convert an ICS file to EMLx format, follow the instructions from [Convert ICS to EML](#convert-ics-to-eml) article and save the .emlx file as shown in the following line of code:

```cs
// save as a EMLX
eml.Save("Saved File.emlx", new EmlSaveOptions(MailMessageSaveType.EmlxFormat));
```

## **Convert ICS to HTML**

The following code sample demonstrates the conversion process:

1. Load the ICS file to be converted using the [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Create a new [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) object to hold the calendar data. 
3. Add the appointment from the ICS file to the EML as an alternate view using the [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method. 
4. Save the EML file with the converted data using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method with the [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) to provide formatting options for the saved HTML file. In this specific case, the [HtmlFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) is used to include the HTML header in the output file, while [HtmlFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) is used to render any calendar events contained in the EML message in a format suitable for display. 

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

Use other values and properties of the [HtmlFormatOptions](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) enumeration and [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) class to set format options as required.

## **Convert ICS to MBOX**

The following code sample demonstrates the process of ICS to MBOX conversion. It loads an ICS file, creates an EML message, adds the appointment details from the ICS file to the EML message, and then writes the EML message to an MBOX storage file.

1. Load the ICS file to be converted using the [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Create a new [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) object to hold the calendar data. 
3. Add the appointment from the ICS file to the EML as an alternate view using the [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Create a new MboxrdStorageWriter object.
5. Add the EML message to the storage by writing the message content in MBOX format to the MBOX file specified.


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

## **Convert ICS to MHTML**

The following code sample demonstrates the representation of all these steps in the conversion process using Aspose.Email for .NET library:

1. Load the ICS file to be converted using the [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method.
2. Create a new [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) object to hold the converted data. 
3. Add the appointment from the ICS file to the EML as an alternate view using the [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment) method.
4. Save the EML file with the converted data using the [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) method with [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) to provide saving options for the MHTML file. In this specific case, the [MhtFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) is used to include the email message header in the output file, while [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) is used to render any calendar events contained in the EML message in a format suitable for display.


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

This approach ensures that the converted MHTML file retains the calendar event details and formatting, enabling efficient sharing and viewing across various platforms and email clients.

Feel free to use other values and properties of the [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) enumeration and [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) class to set format options as required.

## **Convert ICS to MSG**

Converting ICS (iCalendar) files to MSG format is reasonable for better compatibility with Microsoft Outlook, as MSG files are commonly used for storing email messages, appointments, and other Outlook-related data. The following code sample demonstrates how to load an ICS file, manipulate its content, and save it as an MSG file without losing any data or formatting:

1. Load the ICS file using the [Calendar.Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) and create an [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) object from the calendar data stored in the file.
2. Call the [Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) method on the Appointment object to convert and save the loaded appointment data from the ICS file to an MSG file at the specified location.

```cs
// load the ICS file to be converted
// save ICS as a MSG
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save("Saved File.msg", AppointmentSaveFormat.Msg);
```

## **Convert ICS to OFT**

The process involves loading ICS files and saving them as MSG files with further conversion to OFT format: 

1. Create a new stream object to store the appointment data in memory.
2. Load the appointment data from the ICS file. Save the appointment data to the stream object in MSG format using the Save() method.
3. Load the appointment data from the stream by creating a new MapiMessage object using the [MapiMessage.Load()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load) method.
4. Save the loaded MapiMessage data as an Outlook template file using the [Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) method with the provided format options SaveOptions.DefaultOft.

```cs
// load the ICS file to be converted
// save ICS as a MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("My File.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// save MSG as an OFT
MapiMessage.Load(ms).Save("Saved File.oft", SaveOptions.DefaultOft);
```

## **Convert ICS to OST**

Aspose.Email provides functionality to load an ICS file, save it as a MSG file, then open an OST file, access calendar folders within the file, and easily add MSG files to the calendar folder:

1. Create a stream to store the appointment data.
2. Load the appointment data from an ICS file using the [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method and save it to the stream in MSG format with the [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) method.
3. Load the Personal Storage file using the [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) method of the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class.
4. Retrieve the calendar folder from the Personal Storage file with the [PersoanlStorage.GetPredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getpredefinedfolder/) method.
5. Use the [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method to add the appointment message to the calendar folder in the OST file.

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

## **Convert ICS to PST**


The following code sample demonstrates the conversion process:

1. Create a stream to hold the appointment data.
2. Load the appointment data from an ICS file using the [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) method and save it to the stream in MSG format with the [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) method.
3. Create a new PST file with the file name using the [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method.
4. Create a calendar folder within the PST file to store appointments using the [CreatePredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/createpredefinedfolder/#createpredefinedfolder) method.
5. Add the appointment message to the calendar folder within the PST file using the [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) method.

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
