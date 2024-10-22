---
title: "Trabajando con Citas"
url: /es/java/working-with-appointments/
weight: 20
type: docs
---

## **Cargar y Guardar una Cita en Formato ICS**

La clase [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) en Aspose.Email para Java se puede usar para cargar una cita en formato ICS, así como para crear una nueva cita y guardarla en un disco en formato ICS. En este artículo, primero creamos una cita y la guardamos en un disco en formato ICS y luego la cargamos.

### **Cargar una Cita en Formato ICS**

Para cargar una cita en formato ICS, se requieren los siguientes pasos:

1. Crear una instancia de la clase [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).
2. Llamar al método [Load()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#load-java.io.InputStream-) proporcionando la ruta del archivo ICS.
3. Leer cualquier propiedad para obtener información de la cita (archivo ICS).

Los siguientes fragmentos de código muestran cómo cargar una cita en formato ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-LoadAppointment.java" >}}

### **Crear una Cita y Guardar en Disco en Formato ICS**

Se requieren los siguientes pasos para crear una cita y guardarla en formato ICS.

1. Crear una instancia de la clase [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) e inicializarla con este constructor.
2. Pasar los siguientes argumentos en el constructor anterior:
   1. Asistentes
   1. Descripción
   1. Fecha de Finalización
   1. Ubicación
   1. Organizador
   1. Fecha de Inicio
   1. Resumen
   1. Fecha de Creación
   1. Fecha de Última Modificación
3. Llamar al método [Save()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#save-java.io.OutputStream-) y especificar el nombre y formato del archivo en los argumentos.

La cita se puede abrir en Microsoft Outlook o cualquier programa que pueda cargar un archivo ICS. Si el archivo se abre en Microsoft Outlook, automáticamente agrega la cita al calendario de Outlook.

Los siguientes fragmentos de código muestran cómo crear y guardar una cita en un disco en formato ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-CreateAppointment.java" >}}

## **Guardar Citas en Formato MSG**

Aspose.Email permite guardar citas directamente en archivos .msg. Las siguientes clases públicas están disponibles para personalizar el proceso de guardado de citas:

- La clase [AppointmentMsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentmsgsaveoptions/) con opciones adicionales para guardar citas en formato msg.
- La clase [AppointmentIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmenticssaveoptions/) con opciones adicionales para guardar citas en formato ics. Se añadió para reemplazar la obsoleta IcsSaveOptions.

El siguiente ejemplo de código muestra cómo cargar una cita desde un archivo, y luego guardarla en dos formatos diferentes: .ics y .msg. 

```java
Appointment appointment = Appointment.load("fileName");
appointment.save("fileName.ics", new AppointmentIcsSaveOptions());
appointment.save("fileName.msg", new AppointmentMsgSaveOptions());
```

## **Crear una Cita con Contenido HTML**

Es una práctica común usar el encabezado X-ALT-DESC en formato iCalendar (RFC 5545). Es una propiedad extendida que proporciona una descripción alternativa en formato legible por humanos de un elemento o evento del calendario. Este encabezado se utiliza a menudo para incluir una representación en texto simple o HTML de la descripción del evento, lo que puede ser útil para la compatibilidad con software de calendario más antiguo o para proporcionar una versión simplificada de la descripción. En casos en los que la descripción principal no es compatible o no se muestra correctamente en la aplicación de calendario del destinatario, se utiliza el encabezado X-ALT-DESC para proporcionar una descripción alternativa del evento. Permite al remitente incluir diferentes representaciones de la descripción del evento para asegurar una mejor compatibilidad y accesibilidad entre diferentes softwares y plataformas de calendario. Para crear una cita con contenido HTML, establezca la propiedad [HtmlDescription](https://reference.aspose.com/email/java/com.aspose.email/appointment/#setHtmlDescription-java.lang.String-) en 'true'. Pruebe el siguiente ejemplo de código que demuestra cómo crear y definir un objeto cita con detalles y configuraciones específicas, incluyendo la fecha, hora, ubicación, organizador, asistentes y una descripción formateada:

```java
Date startDate = new Date();
Appointment appointment = new Appointment("Bygget 83",
        startDate, // fecha de inicio
        addHours(startDate, 1), // fecha de finalización
        new MailAddress("TintinStrom@from.com", "Tintin Strom"), // organizador
        MailAddressCollection.to_MailAddressCollection(
                new MailAddress("AinaMartensson@to.com", "Aina Martensson"))); // asistente
appointment.setHtmlDescription("<html>\n"
        + "     <style type=\"\"text/css\"\">\n"
        + "      .text {\n"
        + "             font-family:'Comic Sans MS';\n"
        + "             font-size:16px;\n"
        + "            }\n"
        + "     </style>\n"
        + "    <body>\n"
        + "     <p class=\"\"text\"\">Hola, estoy feliz de invitarte a nuestra fiesta.</p>\n"
        + "    </body>\n"
        + "    </html>");
```

## **Crear una Solicitud de Cita Borrador**

Para guardar una cita en modo borrador, la propiedad [Method](https://reference.aspose.com/email/java/com.aspose.email/appointment/#getMethodType--) de la clase [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) debe establecerse en **Publicar**. El siguiente ejemplo de código demuestra el uso de esta propiedad como ejemplo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-CreateADraftAppointmentRequest.java" >}}

### **Creación de Cita Borrador desde Texto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-DraftAppointmentCreationFromText.java" >}}

## **Agregar y Quitar Adjuntos de Elementos del Calendario**

Aspose.Email proporciona una colección de adjuntos que se puede usar para agregar y recuperar adjuntos asociados con elementos del calendario. Este artículo muestra cómo:

1. Crear y agregar adjuntos a un objeto de clase [Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).
2. Recuperar información de adjuntos de una cita.
3. Extraer adjuntos de una cita.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-AddAndRetrieveAttachmentFromCalendarItems-.java" >}}

## **Formatear Citas**

Los ejemplos de programación a continuación demuestran cómo usar la clase [AppointmentFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentformattingoptions/) para formatear texto y HTML.

#### **Ejemplo de Programación - Formateo de Texto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-TextFormatting.java" >}}

#### **Ejemplo de Programación - Formateo HTML**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-HtmlFormatting.java" >}}

## **Leer Múltiples Eventos de un Archivo ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ReadMultipleEventsfromICSFile-ReadMultipleEventsfromICSFile.java" >}}

## **Escribir Múltiples Eventos en un Archivo ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-WriteMultipleEventsToICS.java" >}}

## **Establecer el Estado de los Participantes de los Asistentes a la Cita**

Aspose.Email para .NET API permite establecer el estado de los asistentes a la cita mientras se formula un mensaje de respuesta. Esto agrega la propiedad PARTSTAT al archivo ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees.java" >}}

## **Personalizar el Identificador del Producto para iCalendar**

Aspose.Email para Java API permite obtener o establecer el identificador del producto que creó el objeto iCalendar.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-ICSSaveOptions.cs" >}}

## **Cómo evitar la Validación de Direcciones al intentar Cargar Citas**

Aspose.Email para Java API permite eludir el error de validación de correo electrónico estableciendo la opción [IgnoreSmtpAddressCheck](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#getIgnoreSmtpAddressCheck--) en el objeto [AppointmentLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#setIgnoreSmtpAddressCheck(boolean)) y pasándolo a la llamada de carga.

~~~Java
AppointmentLoadOptions lo = new AppointmentLoadOptions();
lo.setIgnoreSmtpAddressCheck(true);
Appointment appointment = Appointment.load("app.ics", lo);
~~~