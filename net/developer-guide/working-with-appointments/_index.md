---
title: Working with Appointments
type: docs
weight: 20
url: /net/working-with-appointments/
---

## **Load and Save Appointment in ICS Format**
The [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment) class in Aspose.Email for .NET can be used to load an appointment in ICS format as well as create a new appointment and save it to disk in ICS format. In this article, we first create an appointment and save it to disk in ICS format, and then we load it.
### **Create Appointment and Save to Disk in ICS Format**
Following steps are required to create an appointment and save it in ICS format.

1. Create an instance of the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment) class and initialize it with this constructor.
1. Pass the following arguments in the above constructor
   1. Location
   1. Summary
   1. Description
   1. Start Date
   1. End Date
   1. Organizer
   1. Attendees
1. Call the [Save()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/methods/save/index) method and specify the file name and format in the arguments.

The appointment can be opened in Microsoft Outlook or any program that can load an ICS file. If the file is opened in Microsoft Outlook it automatically adds the appointment in the Outlook calendar.

The following code snippet shows you how to create and save an appointment to disk in ICS format.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-AppointmentInICSFormat-CreateAppointment.cs" >}}
### **Load Appointment ICS Format**
To load an appointment in ICS format, the following steps are required:

1. Create an instance of the [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment) class.
1. Call the [Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/methods/load/index) method by providing the path of the ICS file.
1. Read any property to get any information from the appointment (ICS file).

The following code snippet shows you how to load an appointment in ICS format.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-AppointmentInICSFormat-LoadAppointment.cs" >}}
## **Read Multiple Events from ICS File**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-ReadMultilpleEventsFromICS-ReadMultilpleEventsFromICS.cs" >}}
## **Write Multiple Events to ICS File**
{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-WriteMultipleEventsToICS-WriteMultipleEventsToICS.cs" >}}
## **Create a Draft Appointment Request**
It was shown in our earlier articles how to create and save an appointment in ICS format. It is often required to create an Appointment request in Draft mode, so as the basic information is added and then the same draft Appointment be forwarded to other users for necessary changes according to individual users. In order to save an Appointment in Draft mode, the [MethodType](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/properties/methodtype) property of Appointment class should be set to [AppointmentMethodType.Publish](https://reference.aspose.com/email/net/aspose.email.calendar/appointmentmethodtype). The following code snippet shows you how to create a draft appointment request.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DraftAppointmentRequest-DraftAppointmentRequest.cs" >}}
### **Draft Appointment Creation from Text**
The following code snippet shows you how to create a draft appointment from Text. 

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-DraftAppointmentCreation-DraftAppointmentCreation.cs" >}}
## **Set Participants Status of Appointment Attendees**
Aspose.Email for .NET API lets you set the status of appointment attendees while formulating a reply message. This adds the PARTSTAT property to the ICS file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Email-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.cs" >}}
## **Customize Product Identifier for ICalendar**
Aspose.Email for .NET API allows to get or set the product identifier that created iCalendar object.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ChangeProdIdOfICS-1.cs" >}}
