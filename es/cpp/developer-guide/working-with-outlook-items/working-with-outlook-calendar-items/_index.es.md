---
title: "Trabajar con los elementos del calendario de Outlook mediante la biblioteca de correo electrónico de C++"
description: "Con la API de biblioteca de correo electrónico de C++, puede crear y guardar elementos del calendario de Outlook como MSG, agregar y recuperar archivos adjuntos de los archivos de calendario y establecer recordatorios con citas agregando etiquetas."
url: /es/cpp/working-with-outlook-calendar-items/
weight: 80
type: docs
linktitle: "Trabajar con los elementos del calendario de Outlook"
---

## **Trabajando con MapiCalendar**
La clase MapiCalendar de Aspose.Email proporciona métodos y atributos para establecer varias propiedades de un elemento del calendario. En este artículo se proporcionan ejemplos de código para:

- Crear y guardar elementos del calendario
- Configurar recordatorios para los elementos de MapiCalendar
- Añadir/recuperar archivos adjuntos del calendario
- Recuperación del estado de los destinatarios de las convocatorias de reunión
- Creación de un objeto MapiCalendar TimeZone a partir de una zona horaria estándar

### **Creación y almacenamiento de elementos del calendario**
El siguiente fragmento de código muestra cómo crear y guardar un elemento del calendario en formato ICS con la biblioteca o API del analizador de correo electrónico de C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cpp" >}}

### **Guardar el elemento del calendario como MSG**
El siguiente fragmento de código muestra cómo guardar el elemento del calendario como MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cpp" >}}

### **Añadir un recordatorio de pantalla a un calendario**
En el siguiente fragmento de código, se muestra cómo añadir un recordatorio de pantalla a un calendario.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cpp" >}}

### **Añadir un recordatorio de audio a un calendario**
El siguiente fragmento de código muestra cómo añadir un recordatorio de audio a un calendario.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cpp" >}}

### **Añadir/recuperar archivos adjuntos de archivos de calendario**
El siguiente fragmento de código muestra cómo añadir o recuperar archivos adjuntos de los archivos de calendario.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cpp" >}}

### **Estado de los destinatarios de una convocatoria de reunión**
El siguiente fragmento de código muestra cómo determinar el estado de los destinatarios de una convocatoria de reunión.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cpp" >}}

### **Crear MapiCalendarTimezone a partir de una zona horaria estándar**
El siguiente fragmento de código muestra cómo crear MapiCalendarTimezone a partir de una zona horaria estándar.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cpp" >}}

## **Configurar un recordatorio con la cita creada**
Se puede agregar un recordatorio cuando se crea una cita. Estas alarmas pueden activarse en función de diferentes criterios, como n minutos antes de que comience la programación o repetirse n veces a intervalos de n. Se pueden usar diferentes etiquetas para crear estos activadores en el script incluido entre BEGIN:VALARM y END:VALARM dentro de una cita. Hay varias variantes en las que se puede configurar el recordatorio en una cita.

### **Establecer un recordatorio añadiendo etiquetas**
El siguiente fragmento de código muestra cómo configurar un recordatorio añadiendo etiquetas.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cpp" >}}
