---
title: Working with Appointments
type: docs
weight: 20
url: /java/working-with-appointments/
---

## **Load and Save an Appointment in ICS Format**

The [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) class in Aspose.Email for Java can be used to load an appointment in ICS format as well as to create a new appointment and save it to a disk in ICS format. In this article, we first create an appointment and save it to a disk in ICS format and then we load it.

### **Load an Appointment in ICS Format**

To load an appointment in ICS format, the following steps are required:

1. Create an instance of the [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) class.
1. Call the [Load()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#load-java.io.InputStream-) method by providing the path of the ICS file.
1. Read any property to get any information from the appointment (ICS file).

The following code snippets show how to load an appointment in ICS format.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-LoadAppointment.java" >}}

### **Create an Appointment and Save to Disk in ICS Format**

The following steps are required to create an appointment and save it in ICS format.

1. Create an instance of the [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) class and initialize it with this constructor.
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
1. Call the [Save()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#save-java.io.OutputStream-) method and specify the file name and format in the arguments.

The appointment can be opened in Microsoft Outlook or any program that can load an ICS file. If the file is opened in Microsoft Outlook it automatically adds the appointment in the Outlook calendar.

The following code snippets show how to create and save an appointment to a disk in ICS format.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-CreateAppointment.java" >}}

## **Saving Appointments to MSG Format**

Aspose.Email makes it possible to save appointments directly to .msg files. The following public classes are available for customizing the saving process of apppointments:

- [AppointmentMsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentmsgsaveoptions/) class with additional options to save appointments in msg format.
- [AppointmentIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmenticssaveoptions/) class with additional options to save appointment in ics format. It was added to replace the obsolete IcsSaveOptions.

The code sample below shows how to load an appointment from a file, and then save it in two different formats: .ics and .msg. 

```java
Appointment appointment = Appointment.load("fileName");
appointment.save("fileName.ics", new AppointmentIcsSaveOptions());
appointment.save("fileName.msg", new AppointmentMsgSaveOptions());
```

## **Create an Appointment with HTML Content**

It's a common practice to use the X-ALT-DESC header in iCalendar (RFC 5545) format. It is an extended property that provides an alternative human-readable description of a calendar item or event. This header is often used to include a plain text or HTML representation of the event description, which can be useful for compatibility with older calendar software or for providing a simplified version of the description. In cases, when the primary description is not supported or displayed correctly by the recipient's calendar application, X-ALT-DESC header is used to provide an alternative description of the event. It allows the sender to include different representations of the event description to ensure better compatibility and accessibility across different calendar software and platforms. To create an appointment with HTML content, set the [HtmlDescription](https://reference.aspose.com/email/java/com.aspose.email/appointment/#setHtmlDescription-java.lang.String-) property to 'true'. Try the following code sample that demonstrates how to create and define an appointment object with specific details and settings, including the date, time, location, organizer, attendees, and a formatted description:

```java
Date startDate = new Date();
Appointment appointment = new Appointment("Bygget 83",
        startDate, // start date
        addHours(startDate, 1), // end date
        new MailAddress("TintinStrom@from.com", "Tintin Strom"), // organizer
        MailAddressCollection.to_MailAddressCollection(
                new MailAddress("AinaMartensson@to.com", "Aina Martensson"))); // attendee
appointment.setHtmlDescription("<html>\n"
        + "     <style type=\"\"text/css\"\">\n"
        + "      .text {\n"
        + "             font-family:'Comic Sans MS';\n"
        + "             font-size:16px;\n"
        + "            }\n"
        + "     </style>\n"
        + "    <body>\n"
        + "     <p class=\"\"text\"\">Hi, I'm happy to invite you to our party.</p>\n"
        + "    </body>\n"
        + "    </html>");
```

## **Create a Draft Appointment Request**

In order to save an appointment in a draft mode, the [Method](https://reference.aspose.com/email/java/com.aspose.email/appointment/#getMethodType--) property of the [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) class should be set to **Publish**. The following code sample demonstrates the use of this property as an example.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-CreateADraftAppointmentRequest.java" >}}

### **Draft Appointment Creation from Text**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-DraftAppointmentCreationFromText.java" >}}

## **Adding and Removing Attachments from Calendar Items**

Aspose.Email provides an attachments collection that can be used to add and retrieve attachments associated with calendar items. This article shows how to:

1. Create and add attachments to an [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) class object.
1. Retrieve attachments information from an appointment.
1. Extract attachments from an appointment.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-AddAndRetrieveAttachmentFromCalendarItems-.java" >}}

## **Formatting Appointments**

The programming samples below demonstrate how to use the [AppointmentFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentformattingoptions/) class to format text and HTML.

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

Aspose.Email for Java API allows to get around the email validation error by setting the [IgnoreSmtpAddressCheck](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#getIgnoreSmtpAddressCheck--) option on the [AppointmentLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#setIgnoreSmtpAddressCheck(boolean)) object and passing it in to the load call.

~~~Java
AppointmentLoadOptions lo = new AppointmentLoadOptions();
lo.setIgnoreSmtpAddressCheck(true);
Appointment appointment = Appointment.load("app.ics", lo);
~~~