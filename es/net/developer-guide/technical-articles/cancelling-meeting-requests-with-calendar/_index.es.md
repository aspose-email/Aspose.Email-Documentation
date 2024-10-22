---
title: "Cancelación de Solicitudes de Reunión con el Calendario"
url: /es/net/cancelling-meeting-requests-with-calendar/
weight: 270
type: docs
---


Puedes enviar una solicitud de cancelación de reunión con Aspose.Email usando el objeto de la clase Appointment. Necesitas tener la información de la solicitud de reunión original para cancelar la solicitud. El ejemplo en este artículo primero envía una solicitud de reunión, guarda la información en una base de datos y luego cancela la solicitud basado en el ID del mensaje.
## **Enviando Solicitudes de Reunión**
Antes de que podamos [cancelar solicitudes de reunión](#cancelling-meeting-request), tenemos que enviar algunas:

1. Primero crea una instancia del tipo SmtpClient para enviar el mensaje.
1. Para recopilar la información de los asistentes, hemos creado una cuadrícula de datos para que los usuarios puedan ingresar los nombres y direcciones de las personas a las que se debe enviar la invitación.
1. Después de realizar un bucle for-each en la colección Rows de la cuadrícula, guarda toda la información de los asistentes en la colección MailAddressCollection.
1. Crea una instancia de la clase MailMessage y propiedades necesarias como From, To y Subject.
1. Crea una instancia del tipo Appointment y proporciona la ubicación, hora de inicio, hora de finalización, información de organizadores y asistentes.
1. Guarda toda la información en una base de datos de SQL Server. El trabajo relacionado con la base de datos se realiza en el método SaveIntoDB.

El siguiente fragmento de código te muestra cómo enviar solicitudes de reunión.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-SendMeetingRequests-SendMeetingRequests.cs" >}}
## **Cancelando Solicitud de Reunión**
Para cancelar una solicitud de reunión, primero obtén el ID del mensaje del correo electrónico. Dado que hemos guardado esta información en una base de datos para este ejemplo, podemos recuperarla fácilmente. Hemos utilizado una cuadrícula para cargar todos los mensajes enviados. La captura de pantalla del formulario es la siguiente: 

![todo:image_alt_text](cancelling-meeting-requests-with-calendar_1.png)

1. Selecciona la fila para la cual enviar la solicitud de cancelación.
1. Haz clic en **Enviar Solicitud de Cancelación** para enviar la solicitud.
1. El código obtiene el ID de la fila seleccionada de la cuadrícula y consulta la base de datos para obtener la información relacionada con el asistente, el mensaje y el calendario.
1. Crea instancias de la clase Calendar y de la clase [MailMessage](https://apireference.aspose.com/email/net/aspose.email/mailmessage) utilizando la información recuperada de la base de datos.
1. Utiliza el método Appointment.CancelAppointment() para enviar la solicitud de cancelación.
1. Envía el correo utilizando el [SMTP](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient).

El siguiente fragmento de código te muestra cómo cancelar la solicitud de reunión.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-CancelMeetingRequest-CancelMeetingRequest.cs" >}}