---
title: Working with Appointments
type: docs
weight: 20
url: /java/working-with-appointments/
---

## **Load and Save Appointment in ICS Format**
The Appointment class in Aspose.Email for Java can be used to load an appointment in ICS format as well as to create a new appointment and save it to disk in ICS format. In this article, we first create an appointment and save it to disk in ICS format and then we load it.
### **Create an Appointment and Save to Disk in ICS Format**
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
   1. Created Date
   1. Last Modified Date 
1. Call the Save() method and specify the file name and format in the arguments.

The appointment can be opened in Microsoft Outlook or any program that can load an ICS file. If the file is opened in Microsoft Outlook it automatically adds the appointment in the Outlook calendar.

The following code snippets shows you how to create and save an appointment to disk in ICS format.



{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-CreateAppointment.java" >}}
### **Load Appointment ICS Format**
To load an appointment in ICS format, the following steps are required:

1. Create an instance of the Appointment class.
1. Call the Load() method by providing the path of the ICS file.
1. Read any property to get any information from the appointment (ICS file).

The following code snippets shows you how to load an appointment in ICS format.



{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-LoadAppointment.java" >}}
## **Create a Draft Appointment Request**
In order to save an appointment in draft mode, the Method property of the [Appointment](http://www.aspose.com/api/java/email/com.aspose.email/classes/Appointment) class should be set to **Publish**. The following code sample demonstrates the use of this property as an example.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-CreateADraftAppointmentRequest.java" >}}
### **Draft Appointment Creation from Text**
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-DraftAppointmentCreationFromText.java" >}}
## **Adding and Removing Attachments from Calendar Items**
Aspose.Email provides an attachments collection that can be used to add and retrieve attachments associated with calendar items. This article shows how to:

1. Create and add attachments to an [Appointment](http://www.aspose.com/api/java/email/com.aspose.email/classes/Appointment) class object.
1. Retrieve attachments information an appointment.
1. Extract attachments from an appointment.



{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-AddAndRetrieveAttachmentFromCalendarItems-.java" >}}
## **Formatting Appointment**
The programming samples below demonstrates how to use the [AppointmentFormattingOptions](http://www.aspose.com/api/java/email/com.aspose.email/classes/AppointmentFormattingOptions) class to format text and HTML.
#### **Programming Sample - Text Formatting**
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-TextFormatting.java" >}}
#### **Programming Sample - HTML Formatting**
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-HtmlFormatting.java" >}}
## **Read Multiple Events from ICS File**
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ReadMultipleEventsfromICSFile-ReadMultipleEventsfromICSFile.java" >}}
## **Write Multiple Events from ICS File**
{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-WriteMultipleEventsToICS.java" >}}
## **Set Participants Status of Appointment Attendees**
Aspose.Email for .NET API lets you set status of appointment attendees while formulating a reply message. This adds the PARTSTAT property to the ICS file.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees.java" >}}
## **Customize Product Identifier for ICalendar**
Aspose.Email for Java API allows to get or set the product identifier that created iCalendar object.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-ICSSaveOptions.cs" >}}

## **How to get around Address Validation when trying to Load Appointments**
Aspose.Email for Java API allows to get around the email validation error by setting the [IgnoreSmtpAddressCheck](https://reference.aspose.com/email/java/com.aspose.email/AppointmentLoadOptions#setIgnoreSmtpAddressCheck\(boolean\)) option on the [AppointmentLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/AppointmentLoadOptions) object and passing it in to the load call.

~~~Java
AppointmentLoadOptions lo = new AppointmentLoadOptions();
lo.setIgnoreSmtpAddressCheck(true);
Appointment appointment = Appointment.load("app.ics", lo);
~~~