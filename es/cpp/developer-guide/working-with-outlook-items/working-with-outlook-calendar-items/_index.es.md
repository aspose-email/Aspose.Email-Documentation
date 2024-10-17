---
title: "Trabajando con elementos del calendario de Outlook usando la biblioteca de correo C++"
description: "Usando la API de la biblioteca de correo C++, puedes crear y guardar elementos del calendario de Outlook como MSG, agregar y recuperar archivos adjuntos de los archivos de calendario, y establecer recordatorios con citas añadiendo etiquetas."
url: /es/cpp/working-with-outlook-calendar-items/
weight: 80
type: docs
linktitle: "Trabajando con elementos del calendario de Outlook"
---

## **Trabajando con MapiCalendar**
La clase MapiCalendar de Aspose.Email proporciona métodos y atributos para establecer varias propiedades de un elemento de calendario. Este artículo proporciona ejemplos de código para:

- Crear y guardar elementos de calendario
- Establecer recordatorios para elementos de MapiCalendar
- Agregar/Recuperar archivos adjuntos del calendario
- Recuperar el estado de los destinatarios de solicitudes de reunión
- Crear un objeto MapiCalendar TimeZone a partir de una zona horaria estándar

### **Crear y guardar elementos de calendario**
El siguiente fragmento de código te muestra cómo crear y guardar un elemento de calendario en formato ICS usando la biblioteca o API de análisis de correo C++.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateAndSaveCalendaritems-CreateAndSaveCalendaritems.cpp" >}}

### **Guardar el elemento del calendario como MSG**
El siguiente fragmento de código te muestra cómo guardar el elemento del calendario como MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SavingTheCalendarItemAsMSG-SavingTheCalendarItemAsMSG.cpp" >}}

### **Agregar recordatorio de visualización a un calendario**
El siguiente fragmento de código te muestra cómo agregar un recordatorio de visualización a un calendario.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddDisplayReminderToACalendar-AddDisplayReminderToACalendar.cpp" >}}

### **Agregar recordatorio de audio a un calendario**
El siguiente fragmento de código te muestra cómo agregar un recordatorio de audio a un calendario.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddAudioReminderToCalendar-AddAudioReminderToCalendar.cpp" >}}

### **Agregar/Recuperar archivos adjuntos de archivos de calendario**
El siguiente fragmento de código te muestra cómo agregar/recuperar archivos adjuntos de archivos de calendario.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ManageAttachmentsFromCalendarFiles-GetAttachmentsFromCalendar.cpp" >}}

### **Estado de los destinatarios de una solicitud de reunión**
El siguiente fragmento de código te muestra cómo obtener el estado de los destinatarios de una solicitud de reunión.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-DisplayRecipientsStatusFromMeetingRequest-DisplayRecipientsStatusFromMeetingRequest.cpp" >}}

### **Crear MapiCalendarTimeZone a partir de una zona horaria estándar**
El siguiente fragmento de código te muestra cómo crear MapiCalendarTimeZone a partir de una zona horaria estándar.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateMapiCalendarTimeZoneFromStandardTimezone-CreateMapiCalendarTimeZoneFromStandardTimezone.cpp" >}}

## **Establecer recordatorio con la cita creada**
Un recordatorio puede ser añadido cuando se crea una cita. Estas alarmas pueden activarse en base a diferentes criterios como n minutos antes de que comience el horario, repetir n veces a intervalos de n. Se pueden usar diferentes etiquetas para crear estos disparadores en el script encerrado por BEGIN:VALARM y END:VALARM dentro de una cita. Hay varias variantes en las que se puede establecer un recordatorio en una cita.

### **Establecer un recordatorio añadiendo etiquetas**
El siguiente fragmento de código te muestra cómo establecer un recordatorio añadiendo etiquetas.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetReminderByAddingTags-SetReminderByAddingTags.cpp" >}}