---
title: "Trabajar con elementos del calendario en Exchange Server"
url: /es/cpp/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---

## **Envío de convocatorias de reunión**
En este artículo se muestra cómo enviar una convocatoria de reunión a varios destinatarios mediante Exchange Web Services y Aspose.Email.

1. Cree una convocatoria de reunión mediante el [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) clase y establece el lugar, la hora y los asistentes.
1. Crea una instancia del [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) clase y programe la cita usando el [MailMessage->AddAlternateView()](https://docs.aspose.com/email/es/cppfilter-messages-from-exchange-mailbox/) method.
1. Conéctese al servidor Exchange y envíe la convocatoria de reunión mediante [IEWSClient->Send(MailMessage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method.

The [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) La clase se puede usar para conectarse a un servidor Exchange con soporte para Exchange Web Services (EWS). Para que esto funcione, el servidor debe ser Exchange Server 2007 o posterior. El siguiente fragmento de código muestra cómo usar EWS para enviar las convocatorias de reunión.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cpp" >}}
## **Cómo trabajar con elementos del calendario mediante EWS**
Aspose.Email ofrece la capacidad de agregar, actualizar y cancelar citas mediante el cliente Exchange Web Service (EWS). El [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), y [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) los métodos permiten manipular los elementos del calendario mediante EWS. Este artículo proporciona un ejemplo de código detallado sobre cómo trabajar con elementos del calendario. En el siguiente ejemplo de código se muestra cómo:

1. Crea una cita.
1. Actualiza una cita.
1. Eliminar o cancelar una cita.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cpp" >}}
## **Listar citas con soporte de paginación**
The [ListAppointments](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método expuesto por el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) La API recupera la lista completa de citas del servidor Exchange. Esto puede llevar tiempo si hay un gran número de citas en el servidor de Exchange. La API proporciona métodos sobrecargados de [ListAppointmentsByPage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) método que brinda soporte de paginación a la operación. También se puede usar en diferentes combinaciones con la función de consulta. Los siguientes métodos sobrecargados están disponibles para enumerar las citas de Exchange Server con soporte de paginación.

- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

En el siguiente fragmento de código, se muestra cómo enumerar las citas con soporte de paginación.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cpp" >}}
## **Agregar un evento a la carpeta de calendario secundaria en Exchange Server**
La API Aspose.Email le permite crear una carpeta de calendario secundaria en Exchange Server mediante el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). A continuación, se pueden añadir, actualizar o cancelar citas desde el calendario secundario mediante el [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), y [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) methods. 

El siguiente fragmento de código muestra cómo agregar un evento a una carpeta de calendario secundaria en el servidor de Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cpp" >}}
## **Invitación de calendario para compartir**
El servidor Microsoft Exchange ofrece la capacidad de compartir calendarios mediante el envío de invitaciones de calendario a otros usuarios registrados en el mismo servidor de Exchange. La API Aspose.Email ofrece la misma capacidad al permitir compartir el calendario mediante la API EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cpp" >}}
## **Recuperación de la información de atributos extendidos de los elementos del calendario**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cpp" >}}
