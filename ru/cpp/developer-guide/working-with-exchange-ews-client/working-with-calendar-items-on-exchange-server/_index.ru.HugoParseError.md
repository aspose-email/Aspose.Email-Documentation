---
title: Работа с элементами календаря на Exchange Server
type: docs
weight: 50
url: /cpp/working-with-calendar-items-on-exchange-server/
---

## **Отправка запросов на встречу**
В этой статье показано, как отправить запрос на встречу нескольким получателям с использованием Exchange Web Services и Aspose.Email.

1. Создайте запрос на встречу с использованием класса [Appointment](https://apireference.aspose.com/email/cpp/class/aspose.email.calendar.appointment) и укажите место, время и участников.
1. Создайте экземпляр класса [MailMessage](https://apireference.aspose.com/email/cpp/class/aspose.email.mail_message) и назначьте встречу с помощью метода [MailMessage->AddAlternateView()](https://docs.aspose.com/email/cppfilter-messages-from-exchange-mailbox/) .
1. Подключитесь к серверу Exchange и отправьте запрос на встречу с помощью метода [IEWSClient->Send(MailMessage)](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) .

Класс [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) можно использовать для подключения к серверам Exchange с поддержкой Exchange Web Services (EWS). Для этого сервер должен быть Exchange Server 2007 или более поздней версии. Следующий фрагмент кода показывает вам, как использовать EWS для отправки запросов на встречи.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendMeetingRequestsUsingEWS-SendMeetingRequestsUsingEWS.cpp" >}}
## **Работа с элементами календаря с использованием EWS**
Aspose.Email предоставляет возможность добавления, обновления и отмены встреч с использованием клиента Exchange Web Service (EWS). Методы [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) и [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) позволяют управлять элементами календаря с помощью EWS. В этой статье приведен подробный образец кода для работы с элементами календаря. Следующий образец кода показывает, как:

1. Создать встречу.
1. Обновить встречу.
1. Удалить/отменить встречу.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS-CreatingUpdatingAndDeletingCalendarItemsUsingEWS.cpp" >}}
## **Список встреч с поддержкой постраничного отображения**
Метод [ListAppointments](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), доступный через API [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), извлекает полный список встреч с сервера Exchange. Это может занять некоторое время, если на сервере Exchange много встреч. API предоставляет перегруженные методы [ListAppointmentsByPage](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) , которые обеспечивают поддержку постраничного отображения для операции. Это можно использовать в различных комбинациях с функцией запросов. Доступны следующие перегруженные методы для списка встреч с сервера Exchange с поддержкой постраничного отображения.

- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).
- [`IEWSClient.ListAppointmentsByPage(string folderUri, MailQuery query, int itemsPerPage, int itemOffset)`](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

Следующий фрагмент кода показывает, как перечислить встречи с поддержкой постраничного отображения.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-PagingSupportForListingAppointments-PagingSupportForListingAppointments.cpp" >}}
## **Добавление события во вторичную папку календаря на Exchange Server**
API Aspose.Email позволяет создать вторичную папку календаря на Exchange Server с использованием [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Встречи затем могут быть добавлены, обновлены или отменены из вторичного календаря с использованием методов [IEWSClient->CreateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), [IEWSClient->UpdateAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) и [IEWSClient->CancelAppointment](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). 

Следующий фрагмент кода показывает, как добавить событие во вторичную папку календаря на сервере exchange.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SecondaryCalendarEvents-SecondaryCalendarEvents.cpp" >}}
## **Обмен приглашениями на календарь**
Сервер Microsoft Exchange предоставляет возможность обмена календарями, отправляя приглашения на календарь другим пользователям, зарегистрированным на том же сервере Exchange. API Aspose.Email предоставляет ту же возможность, позволяя обмениваться календарем с помощью API EWS.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendCalendarInvitation-SendCalendarInvitation.cpp" >}}
## **Извлечение информации о дополнительных атрибутах из элементов календаря**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-RetreiveExtAttributesForCalendarItems-RetreiveExtAttributesForCalendarItems.cpp" >}}
