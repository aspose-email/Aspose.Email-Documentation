---
title: Managing Appointments in Python
ArticleTitle: Managing Appointments in Python
type: docs
weight: 20
url: /python-net/managing-appointments-in-python/
---


## **Creating and Saving Appointments**

The [Appointment](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/) class in Aspose.Email API can be used to load an appointment in ICS format as well as create a new one and save it to disk in ICS format. 

### **Create an Appointment and Save as ICS**

The following code snippets shows you how to create and save an appointment to disk in ICS format:

1. Create an instance of [MailAddressCollection](https://reference.aspose.com/email/python-net/aspose.email/mailaddresscollection/#mailaddresscollection-class) to store email addresses of the attendees and add an attendee's email to the [MailAddressCollection](https://reference.aspose.com/email/python-net/aspose.email/mailaddresscollection/#mailaddresscollection-class) using the `append()` method.
2. Use the [Appointment](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#constructors) constructor to create a new appointment with details such as location, start time, end date, organizer email, and list of attendees.
3. Set appointment properties - summary and description - to describe the meeting specifics.
4. Save the appointment in ICS format using the [save()](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) method specifying the file path and the format.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointment-CreateAppointment.py" >}}

The appointment can be opened in Microsoft Outlook or any program that can load an ICS file. If the file is opened in Microsoft Outlook it automatically adds the appointment in the Outlook calendar.

## **Create a Draft Appointment Request**

It is often required to create an Appointment request in Draft mode, so as the basic information is added and then the same draft Appointment can be forwarded to other users for necessary changes according to individual requests. In order to save an Appointment in Draft mode, the [method_type](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#properties) property of [Appointment](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#appointment-class) class should be set to 'publish'. The following code snippet shows you how to create a draft appointment request.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-DraftAppointmentRequest-DraftAppointmentRequest.py" >}}

### **Draft Appointment from Text**

The following code snippet shows you how to create a draft appointment from Text. 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointmentFromString-CreateAppointmentFromString.py" >}}

## **Loading and Reading Appointments**

### **Load Appointments from ICS Files**

The following code snippet shows you how to load an appointment in ICS format:

1. Use the [Appointment.load()](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) method to load an appointment from an existing ICS file specifying the path.
2. Retrieve and display appointment details: summary, location, description, start date, end date, organizer, and attendees.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-LoadAppointment-LoadAppointment.py" >}}

### **Read Multiple Events from ICS Files**

With Aspose.Email, you can read all the events from a given ICS file and store them in a list, then output the total number of appointments. The following code sample demonstrates how to perform this task:

1. Use the [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) class to initialize a reader that will process an ICS file containing calendar events. Specify the location of the ICS file in the constructor.
2. Create an empty list named 'appointments' to store the events read from the ICS file.
3. Iterate through each event in the ICS file using the [reader.next_event()](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/#methods).
4. Append the current event (reader.current) to the appointments list.
5. Print the total number of appointments.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-ReadMultipleEventsFromICS-ReadMultipleEventsFromICS.py" >}}

## **Writing and Updating Appointments**

### **Write Multiple Events to ICS Files**

Create and save multiple events into an ICS file, with each event containing specific details, such as attendees, location, time, and descriptive information. The following code sample will show you how to create and save multiple appointment events into an ICS calendar file:

1. Create an instance of [IcsSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.calendar/icssaveoptions/) to specify how the calendar events will be saved.
2. Set the action property to AppointmentAction.CREATE to indicate that the appointments should be created in the ICS file.
3. Use the [CalendarWriter](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarwriter/) class to set up a writer for outputting events into an ICS file providing the output file path and the previously defined save options.
4. Create a [MailAddressCollection](https://reference.aspose.com/email/python-net/aspose.email/mailaddresscollection/) to manage the list of attendees for each appointment. Add a specific email address to this collection using the append method.
5. Iterate 10 times using a for loop, corresponding to the creation of 10 appointment events. For each iteration, create an [Appointment](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment) instance with specified details such as location, start time, end date, organizer email, and attendees.
5. Add event details: description and summary properties.
6. Use the [write](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarwriter/#methods) method of the writer to output the appointment to the ICS file.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-WriteMultipleEventsToICS-WriteMultipleEventsToICS.py" >}}

## **Set Participant Status for Appointment Attendees**

Aspose.Email for .NET API allows you to set the statuses of the appointment attendees while formulating a reply message. By assigning these statuses to each attendee, the application or system working with the Appointment object can handle event-related logic, such as showing confirmed attendees, tracking changes, or managing notifications accordingly. 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.py" >}}
