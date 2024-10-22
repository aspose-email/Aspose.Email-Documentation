---
title: "Trabajando con elementos de calendario en Exchange Server"
url: /es/cpp/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---

## **Enviando Solicitudes de Reunión**
Este artículo muestra cómo enviar una solicitud de reunión a múltiples destinatarios utilizando Exchange Web Services y Aspose.Email.

1. Cree una solicitud de reunión utilizando la clase [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) y establezca la ubicación, la hora y los asistentes.
1. Cree una instancia de la clase [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) y establezca la cita utilizando el método [MailMessage->AddAlternateView()](https://docs.aspose.com/email/es/cppfilter-messages-from-exchange-mailbox/) .
1. Conéctese al Exchange Server y envíe la solicitud de reunión utilizando el método [IEWSClient->Send(MailMessage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) .

La clase [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) se puede utilizar para conectarse a servidores de Exchange con soporte para Exchange Web Services (EWS). Para que esto funcione, el servidor debe ser Exchange Server 2007 o posterior. El siguiente fragmento de código muestra cómo utilizar EWS para enviar las solicitudes de reunión.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cpp" >}}
## **Trabajando con elementos de calendario usando EWS**
Aspose.Email proporciona la capacidad de agregar, actualizar y cancelar citas utilizando el cliente de Exchange Web Service (EWS). Los métodos [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) y [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) permiten manipular elementos de calendario utilizando EWS. Este artículo proporciona un ejemplo de código detallado sobre cómo trabajar con elementos de calendario. El siguiente ejemplo de código muestra cómo:

1. Crear una cita.
1. Actualizar una cita.
1. Eliminar/Cancela una cita.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cpp" >}}
## **Listando Citas con Soporte de Paginación**
El método [ListAppointments](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) expuesto por la API [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) recupera la lista completa de citas del servidor de Exchange. Esto puede tomar tiempo si hay un gran número de citas en el servidor de Exchange. La API proporciona métodos sobrecargados del método [ListAppointmentsByPage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) que brinda soporte de paginación a la operación. Esto se puede utilizar en diferentes combinaciones con la función de consulta también. Los siguientes métodos sobrecargados están disponibles para listar citas desde el servidor de Exchange con soporte de paginación.

- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

El siguiente fragmento de código muestra cómo listar citas con soporte de paginación.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cpp" >}}
## **Agregando Evento a la Carpeta de Calendario Secundaria en Exchange Server**
La API de Aspose.Email le permite crear una carpeta de calendario secundaria en el servidor de Exchange utilizando el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Las citas pueden ser agregadas, actualizadas o canceladas desde el calendario secundario utilizando los métodos [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) y [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). 

El siguiente fragmento de código muestra cómo agregar un evento a una carpeta de calendario secundaria en el servidor de exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cpp" >}}
## **Compartiendo Invitaciones de Calendario**
El servidor Microsoft Exchange proporciona la capacidad de compartir calendarios enviando invitaciones de calendario a otros usuarios, registrados en el mismo servidor de Exchange. La API de Aspose.Email proporciona la misma capacidad al permitir compartir el calendario utilizando la API de EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cpp" >}}
## **Recuperando Información de Atributos Extendidos de los Elementos de Calendario**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cpp" >}}
