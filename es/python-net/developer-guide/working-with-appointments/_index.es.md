---
title: "Trabajando con citas"
url: /es/python-net/working-with-appointments/
weight: 20
type: docs
---


## **Cargar y guardar la cita en formato ICS**
La clase Appointment de la API Aspose.Email se puede usar para cargar una cita en formato ICS, así como para crear una nueva cita y guardarla en el disco en formato ICS. En este artículo, primero creamos una cita y la guardamos en el disco en formato ICS y, a continuación, la cargamos.
### **Crear cita y guardar en disco en formato ICS**
Se requieren los siguientes pasos para crear una cita y guardarla en formato ICS.

1. Crea una instancia de la clase Appointment e inicialízala con este constructor.
1. Pase los siguientes argumentos en el constructor anterior
   1. Attendees
   1. Description
   1. Fecha de finalización
   1. Location
   1. Organizer
   1. Fecha de inicio
   1. Summary
1. Llame al método Save () y especifique el nombre y el formato del archivo en los argumentos.

La cita se puede abrir en Microsoft Outlook o en cualquier programa que pueda cargar un archivo ICS. Si el archivo se abre en Microsoft Outlook, agrega automáticamente la cita al calendario de Outlook.

Los siguientes fragmentos de código muestran cómo crear y guardar una cita en el disco en formato ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointment-CreateAppointment.py" >}}
### **Cargar formato ICS de citas**
Para cargar una cita en formato ICS, se requieren los siguientes pasos:

1. Crea una instancia de la clase Appointment.
1. Llame al método Load () proporcionando la ruta del archivo ICS.
1. Lea cualquier propiedad para obtener información de la cita (archivo ICS).

Los siguientes fragmentos de código muestran cómo cargar una cita en formato ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-LoadAppointment-LoadAppointment.py" >}}
## **Leer varios eventos del archivo ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-ReadMultipleEventsFromICS-ReadMultipleEventsFromICS.py" >}}
## **Escribir varios eventos en un archivo ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-WriteMultipleEventsToICS-WriteMultipleEventsToICS.py" >}}
## **Crear un borrador de solicitud de cita**
En nuestros artículos anteriores se mostró cómo crear y guardar una cita en formato ICS. A menudo es necesario crear una solicitud de cita en modo borrador, de modo que se agrega la información básica y, a continuación, el mismo borrador de cita se envía a otros usuarios para que hagan los cambios necesarios según los usuarios individuales. Para guardar una cita en modo borrador, el **Method** la propiedad de la clase Appointment debe establecerse en **Publish**. El siguiente fragmento de código muestra cómo crear un borrador de solicitud de cita.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-DraftAppointmentRequest-DraftAppointmentRequest.py" >}}
### **Creación de borradores de citas a partir del texto**
El siguiente fragmento de código muestra cómo crear un borrador de cita desde Text. 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointmentFromString-CreateAppointmentFromString.py" >}}
## **Establecer el estado de los participantes de los asistentes a la cita**
La API Aspose.Email para .NET le permite establecer el estado de los asistentes a la cita mientras formula un mensaje de respuesta. Esto agrega la propiedad PARTSTAT al archivo ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.py" >}}
