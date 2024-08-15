---
title: "Cancelación de convocatorias de reunión con calendario"
url: /es/net/cancelling-meeting-requests-with-calendar/
weight: 270
type: docs
---


Puede enviar una solicitud de cancelación de reunión con Aspose.Email mediante el objeto Appointment Class. Debe tener la información original de la solicitud de reunión para cancelar la solicitud. En el ejemplo de este artículo, primero se envía una convocatoria de reunión, se guarda la información en una base de datos y, a continuación, se cancela la convocatoria en función del identificador del mensaje.
## **Envío de convocatorias de reunión**
Antes de que podamos [cancelar convocatorias de reunión](#cancelling-meeting-request), tenemos que enviar algunos:

1. En primer lugar, cree una instancia de tipo SMTPClient para enviar el mensaje.
1. Para recopilar información sobre los asistentes, hemos creado una cuadrícula de datos para que los usuarios puedan introducir los nombres y direcciones de las personas a las que se les debe enviar la invitación.
1. Tras realizar un bucle para cada uno de los conjuntos Rows de la cuadrícula, guarde toda la información de los asistentes en la colección MailAddressCollection.
1. Crea una instancia de la clase MailMessage y las propiedades necesarias, como From, To y Subject.
1. Cree una instancia de tipo Cita e indique la ubicación, la hora de inicio, la hora de finalización, los organizadores y los asistentes.
1. Guarde toda la información en una base de datos de SQL Server. El trabajo relacionado con la base de datos se está realizando con el método SaveInToDB.

El siguiente fragmento de código muestra cómo enviar convocatorias de reunión.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendMeetingRequests-SendMeetingRequests.cs" >}}
## **Cancelación de la solicitud de reunión**
Para cancelar una convocatoria de reunión, primero obtenga el ID de mensaje del mensaje de correo electrónico. Como hemos guardado esta información en una base de datos para este ejemplo, podemos volver a obtenerla fácilmente. Hemos utilizado una cuadrícula para cargar todos los mensajes enviados. La captura de pantalla del formulario es la siguiente:

![todo:image_alt_text](cancelling-meeting-requests-with-calendar_1.png)

1. Seleccionar la fila a la que enviar la solicitud de cancelación.
1. Click **Enviar solicitud de cancelación** para enviar la solicitud.
1. El código obtiene el identificador de la fila seleccionada de la cuadrícula y consulta la base de datos para obtener la información relacionada con los asistentes, los mensajes y el calendario.
1. Cree una instancia de la clase Calendar y [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage)
   clases de clase que utilizan la información recuperada de la base de datos.
1. Utilice el método Appointment.cancelAppointment () para enviar la solicitud de cancelación.
1. Envíe el correo mediante el [SMTP](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient).

El siguiente fragmento de código muestra cómo cancelar la convocatoria de reunión.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CancelMeetingRequest-CancelMeetingRequest.cs" >}}
