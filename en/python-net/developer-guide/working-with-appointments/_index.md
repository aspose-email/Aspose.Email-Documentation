---
title: Working with  Appointments
ArticleTitle: Working with  Appointments
type: docs
weight: 20
url: /python-net/working-with-appointments/
---


## **Load and Save Appointment in ICS Format**
The Appointment class in Aspose.Email API can be used to load an appointment in ICS format as well as create a new appointment and save it to disk in ICS format. In this article, we first create an appointment and save it to disk in ICS format, and then we load it.
### **Create Appointment and Save to Disk in ICS Format**
Following steps are required to create an appointment and save it in ICS format.

1. Create an instance of the Appointment class and initialize it with this constructor.
1. Pass the following arguments in the above constructor
   1. Attendees
   1. Description
   1. End Date
   1. Location
   1. Organizer
   1. Start Date
   1. Summary
1. Call the Save() method and specify the file name and format in the arguments.

The appointment can be opened in Microsoft Outlook or any program that can load an ICS file. If the file is opened in Microsoft Outlook it automatically adds the appointment in the Outlook calendar.

The following code snippets shows you how to create and save an appointment to disk in ICS format.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointment-CreateAppointment.py" >}}
### **Load Appointment ICS Format**
To load an appointment in ICS format, the following steps are required:

1. Create an instance of the Appointment class.
1. Call the Load() method by providing the path of the ICS file.
1. Read any property to get any information from the appointment (ICS file).

The following code snippets shows you how to load an appointment in ICS format.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-LoadAppointment-LoadAppointment.py" >}}
## **Read Multiple Events from ICS File**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-ReadMultipleEventsFromICS-ReadMultipleEventsFromICS.py" >}}
## **Write Multiple Events to ICS File**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-WriteMultipleEventsToICS-WriteMultipleEventsToICS.py" >}}
## **Create a Draft Appointment Request**
It was shown in our earlier articles how to create and save an appointment in ICS format. It is often required to create an Appointment request in Draft mode, so as the basic information is added and then the same draft Appointment be forwarded to other users for necessary changes according to individual users. In order to save an Appointment in Draft mode, the **Method** property of Appointment class should be set to **Publish**. The following code snippet shows you how to create a draft appointment request.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-DraftAppointmentRequest-DraftAppointmentRequest.py" >}}
### **Draft Appointment Creation from Text**
The following code snippet shows you how to create a draft appointment from Text. 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointmentFromString-CreateAppointmentFromString.py" >}}
## **Set Participants Status of Appointment Attendees**
Aspose.Email for .NET API lets you set status of appointment attendees while formulating a reply message. This adds the PARTSTAT property to the ICS file.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.py" >}}
