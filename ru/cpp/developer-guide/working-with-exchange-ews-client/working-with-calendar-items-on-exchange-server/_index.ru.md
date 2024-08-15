---
title: "Работа с элементами календаря на сервере Exchange"
url: /ru/cpp/working-with-calendar-items-on-exchange-server/
weight: 50
type: docs
---

## **Отправка приглашений на собрание**
В этой статье показано, как отправить приглашение на собрание нескольким получателям с помощью веб-служб Exchange и Aspose.Email.

1. Создайте приглашение на собрание, используя [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) класс и определите место, время и участников.
1. Создайте экземпляр [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) класс и назначьте встречу, используя [MailMessage->AddAlternateView()](https://docs.aspose.com/email/ru/cppfilter-messages-from-exchange-mailbox/) method.
1. Подключитесь к серверу Exchange и отправьте приглашение на собрание, используя [IEWSClient->Send(MailMessage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) method.

The [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс можно использовать для подключения к серверам Exchange с поддержкой веб-служб Exchange (EWS). Чтобы это работало, необходимо использовать сервер Exchange Server 2007 или более поздней версии. В следующем фрагменте кода показано, как использовать EWS для отправки приглашений на собрания.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cpp" >}}
## **Работа с элементами календаря с помощью EWS**
Aspose.Email предоставляет возможность добавлять, обновлять и отменять встречи с помощью клиента Exchange Web Service (EWS). [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), и [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) методы позволяют манипулировать элементами календаря с помощью EWS. В этой статье представлен подробный пример кода работы с элементами календаря. В следующем примере кода показано, как:

1. Назначьте встречу.
1. Обновите встречу.
1. Удалить/отменить встречу.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cpp" >}}
## **Составление списков встреч с помощью пейджинговой поддержки**
The [ListAppointments](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод, представленный [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) API получает полный список встреч с сервера Exchange. Если на сервере Exchange много встреч, это может занять некоторое время. API предоставляет перегруженные методы [ListAppointmentsByPage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод, обеспечивающий пейджинговую поддержку операции. Его также можно использовать в различных комбинациях с функцией запросов. Доступны следующие перегруженные методы для списка встреч с Exchange Server с поддержкой пейджинга.

- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

В следующем фрагменте кода показано, как составить список встреч с поддержкой пейджинга.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cpp" >}}
## **Добавление события в папку дополнительного календаря на сервере Exchange**
API Aspose.Email позволяет создать дополнительную папку календаря на сервере Exchange с помощью [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Затем встречи можно добавлять, обновлять или отменять из дополнительного календаря, используя [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), и [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) methods. 

В следующем фрагменте кода показано, как добавить событие во дополнительную папку календаря на сервере Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cpp" >}}
## **Приглашение поделиться календарем**
Сервер Microsoft Exchange предоставляет возможность совместного использования календарей, отправляя приглашения в календарь другим пользователям, зарегистрированным на том же сервере Exchange. API Aspose.Email предоставляет ту же возможность, позволяя делиться календарем с помощью API EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cpp" >}}
## **Получение информации о дополнительных атрибутах из элементов календаря**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cpp" >}}
