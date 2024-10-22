---
title: "Trabajando con Citas"
url: /es/python-net/working-with-appointments/
weight: 20
type: docs
---

## **Cargar y Guardar Cita en Formato ICS**
La clase Appointment en la API de Aspose.Email se puede usar para cargar una cita en formato ICS, así como para crear una nueva cita y guardarla en disco en formato ICS. En este artículo, primero creamos una cita y la guardamos en disco en formato ICS, y luego la cargamos.
### **Crear Cita y Guardar en Disco en Formato ICS**
Los siguientes pasos son necesarios para crear una cita y guardarla en formato ICS.

1. Crear una instancia de la clase Appointment y inicializarla con este constructor.
1. Pasar los siguientes argumentos en el constructor anterior:
   1. Asistentes
   1. Descripción
   1. Fecha de Finalización
   1. Ubicación
   1. Organizador
   1. Fecha de Inicio
   1. Resumen
1. Llamar al método Save() y especificar el nombre del archivo y el formato en los argumentos.

La cita puede abrirse en Microsoft Outlook o cualquier programa que pueda cargar un archivo ICS. Si el archivo se abre en Microsoft Outlook, automáticamente agrega la cita en el calendario de Outlook.

Los siguientes fragmentos de código te muestran cómo crear y guardar una cita en disco en formato ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointment-CreateAppointment.py" >}}
### **Cargar Cita en Formato ICS**
Para cargar una cita en formato ICS, se requieren los siguientes pasos:

1. Crear una instancia de la clase Appointment.
1. Llamar al método Load() proporcionando la ruta del archivo ICS.
1. Leer cualquier propiedad para obtener información de la cita (archivo ICS).

Los siguientes fragmentos de código te muestran cómo cargar una cita en formato ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-LoadAppointment-LoadAppointment.py" >}}
## **Leer Múltiples Eventos desde un Archivo ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-ReadMultipleEventsFromICS-ReadMultipleEventsFromICS.py" >}}
## **Escribir Múltiples Eventos en un Archivo ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-WriteMultipleEventsToICS-WriteMultipleEventsToICS.py" >}}
## **Crear una Solicitud de Cita Borrador**
Se mostró en nuestros artículos anteriores cómo crear y guardar una cita en formato ICS. A menudo es necesario crear una solicitud de cita en modo Borrador, de modo que se añada la información básica y luego el mismo Borrador de cita se reenvíe a otros usuarios para los cambios necesarios según los usuarios individuales. Para guardar una cita en modo Borrador, la **propiedad** Method de la clase Appointment debe establecerse en **Publish**. El siguiente fragmento de código te muestra cómo crear una solicitud de cita borrador.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-DraftAppointmentRequest-DraftAppointmentRequest.py" >}}
### **Creación de Cita Borrador desde Texto**
El siguiente fragmento de código te muestra cómo crear una cita borrador desde Texto.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointmentFromString-CreateAppointmentFromString.py" >}}
## **Establecer el Estado de los Asistentes a la Cita**
Aspose.Email para la API de .NET te permite establecer el estado de los asistentes a la cita mientras formulas un mensaje de respuesta. Esto añade la propiedad PARTSTAT al archivo ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.py" >}}