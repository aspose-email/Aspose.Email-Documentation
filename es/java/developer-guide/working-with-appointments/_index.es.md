---
title: "Trabajando con citas"
url: /es/java/working-with-appointments/
weight: 20
type: docs
---

## **Cargar y guardar una cita en formato ICS**

The [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) La clase en Aspose.Email para Java se puede usar para cargar una cita en formato ICS, así como para crear una nueva cita y guardarla en un disco en formato ICS. En este artículo, primero creamos una cita y la guardamos en un disco en formato ICS y luego la cargamos.

### **Cargar una cita en formato ICS**

Para cargar una cita en formato ICS, se requieren los siguientes pasos:

1. Crea una instancia del [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) class.
1. Llame al [Load()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#load-java.io.InputStream-) método proporcionando la ruta del archivo ICS.
1. Lea cualquier propiedad para obtener información de la cita (archivo ICS).

Los siguientes fragmentos de código muestran cómo cargar una cita en formato ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-LoadAppointment.java" >}}

### **Crear una cita y guardarla en el disco en formato ICS**

Los pasos siguientes son necesarios para crear una cita y guardarla en formato ICS.

1. Crea una instancia del [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) clase e inicialícela con este constructor.
1. Pase los siguientes argumentos en el constructor anterior
   1. Attendees
   1. Description
   1. Fecha de finalización
   1. Location
   1. Organizer
   1. Fecha de inicio
   1. Summary
   1. Fecha de creación
   1. Fecha de última modificación 
1. Llame al [Save()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#save-java.io.OutputStream-) método y especifique el nombre y el formato del archivo en los argumentos.

La cita se puede abrir en Microsoft Outlook o en cualquier programa que pueda cargar un archivo ICS. Si el archivo se abre en Microsoft Outlook, agrega automáticamente la cita al calendario de Outlook.

Los siguientes fragmentos de código muestran cómo crear y guardar una cita en un disco en formato ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-CreateAppointment.java" >}}

## **Guardar citas en formato MSG**

Aspose.Email permite guardar citas directamente en archivos.msg. Las siguientes clases públicas están disponibles para personalizar el proceso de guardar las citas:

- [AppointmentMsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentmsgsaveoptions/) clase con opciones adicionales para guardar citas en formato msg.
- [AppointmentIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmenticssaveoptions/) clase con opciones adicionales para guardar la cita en formato ics. Se agregó para reemplazar el obsoleto ICSSaveOptions.

El ejemplo de código que aparece a continuación muestra cómo cargar una cita desde un archivo y, a continuación, guardarla en dos formatos diferentes: .ics y .msg.

```java
Appointment appointment = Appointment.load("fileName");
appointment.save("fileName.ics", new AppointmentIcsSaveOptions());
appointment.save("fileName.msg", new AppointmentMsgSaveOptions());
```

## **Crear una cita con contenido HTML**

Es una práctica habitual utilizar el encabezado X-ALT-DESC en formato iCalendar (RFC 5545). Es una propiedad extendida que proporciona una descripción alternativa legible por humanos de un elemento o evento del calendario. Este encabezado se suele utilizar para incluir una representación en texto plano o HTML de la descripción del evento, lo que puede resultar útil para garantizar la compatibilidad con el software de calendario anterior o para proporcionar una versión simplificada de la descripción. En los casos en que la aplicación de calendario del destinatario no admite la descripción principal o no la muestra correctamente, se utiliza el encabezado X-ALT-DESC para proporcionar una descripción alternativa del evento. Permite al remitente incluir diferentes representaciones de la descripción del evento para garantizar una mejor compatibilidad y accesibilidad en los diferentes programas y plataformas de calendario. Para crear una cita con contenido HTML, defina la [HtmlDescription](https://reference.aspose.com/email/java/com.aspose.email/appointment/#setHtmlDescription-java.lang.String-) propiedad a «verdadera». Prueba el siguiente ejemplo de código, que muestra cómo crear y definir un objeto de cita con detalles y ajustes específicos, como la fecha, la hora, la ubicación, el organizador, los asistentes y una descripción formateada:

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

## **Crear un borrador de solicitud de cita**

Para guardar una cita en modo borrador, el [Method](https://reference.aspose.com/email/java/com.aspose.email/appointment/#getMethodType--) propiedad del [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) la clase debe configurarse en **Publish**. El siguiente ejemplo de código muestra el uso de esta propiedad como ejemplo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-CreateADraftAppointmentRequest.java" >}}

### **Creación de borradores de citas a partir del texto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-DraftAppointmentCreationFromText.java" >}}

## **Agregar y eliminar archivos adjuntos de los elementos del calendario**

Aspose.Email proporciona una colección de archivos adjuntos que se puede usar para agregar y recuperar los archivos adjuntos asociados a los elementos del calendario. En este artículo se muestra cómo:

1. Crear y añadir archivos adjuntos a un [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) objeto de clase.
1. Recupere la información de los archivos adjuntos de una cita.
1. Extraiga los archivos adjuntos de una cita.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-AddAndRetrieveAttachmentFromCalendarItems-.java" >}}

## **Formateo de citas**

Los ejemplos de programación que aparecen a continuación muestran cómo utilizar el [AppointmentFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentformattingoptions/) clase para formatear texto y HTML.

#### **Ejemplo de programación: formato de texto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-TextFormatting.java" >}}

#### **Ejemplo de programación: formato HTML**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-HtmlFormatting.java" >}}

## **Leer varios eventos del archivo ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ReadMultipleEventsfromICSFile-ReadMultipleEventsfromICSFile.java" >}}

## **Escribir varios eventos desde un archivo ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-WriteMultipleEventsToICS.java" >}}

## **Establecer el estado de los participantes de los asistentes a la cita**

La API Aspose.Email para .NET le permite establecer el estado de los asistentes a la cita mientras formula un mensaje de respuesta. Esto agrega la propiedad PARTSTAT al archivo ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees.java" >}}

## **Personalice el identificador de producto para iCalendar**

La API Aspose.Email para Java permite obtener o establecer el identificador del producto que creó el objeto iCalendar.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-ICSSaveOptions.cs" >}}

## **Cómo evitar la validación de direcciones al intentar cargar citas**

La API Aspose.Email para Java permite evitar el error de validación del correo electrónico configurando el [IgnoreSmtpAddressCheck](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#getIgnoreSmtpAddressCheck--) opción en el [AppointmentLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#setIgnoreSmtpAddressCheck(boolean)) objeto y pasarlo a la llamada de carga.

~~~Java
AppointmentLoadOptions lo = new AppointmentLoadOptions();
lo.setIgnoreSmtpAddressCheck(true);
Appointment appointment = Appointment.load("app.ics", lo);
~~~