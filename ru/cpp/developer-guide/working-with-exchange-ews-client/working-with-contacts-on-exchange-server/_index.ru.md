---
title: "Работа с контактами на Exchange Server"
url: /ru/cpp/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---

{{% alert color="primary" %}} Учетные записи Exchange Server содержат не только электронные сообщения. В дополнение к получению, перемещению, отправке и удалению электронных сообщений с Exchange Server, Aspose.Email позволяет работать с контактами. Эта статья объясняет, как получить информацию о контактах, используя Exchange Web Services. Также в статье показано, как вы можете перечислить контакты из папки "Контакты" или разрешить контакты на основе имени контакта. {{% /alert %}} 
## **Получение контактов с помощью EWS**
Aspose.Email предоставляет класс [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) для подключения к Microsoft Exchange Server с использованием Exchange Web Services. Следующие фрагменты кода используют Exchange Web Services для чтения всех контактов. Следующий фрагмент кода показывает вам, как получить контакты с EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cpp" >}}
## **Разрешить контакты с помощью имени контакта**
Следующий фрагмент кода показывает вам, как получить контакты, используя имя контакта.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cpp" >}}
## **Определение формата заметок контакта**
[Contact->get_NotesFormat](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) указывает тип формата текста заметок контактов, определенный перечислением [TextFormat](https://apireference.aspose.com/email/cpp/namespace/aspose.email.personal_info).
## **Получение контакта по Id**
Конкретный контакт может быть извлечен с сервера, используя его идентификатор контакта, как показано в следующем фрагменте кода.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cpp" >}}
## **Добавление контактов**
Метод [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класса [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) можно использовать для добавления информации о контакте на Exchange Server. Метод [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) принимает объект [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) в качестве входного параметра.

Чтобы добавить контакты на Exchange Server:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) с адресом и учетными данными.
1. Инициализируйте объект [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) с необходимыми свойствами.
1. Вызовите метод [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) и передайте контакт для добавления на Exchange Server.

Следующий фрагмент кода демонстрирует добавление контактов на Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddContactsToExchangeServerUsingEWS-1.cpp" >}}
## **Обновление контактов**
Информация о контактах может быть обновлена с помощью Microsoft Outlook. Aspose.Email также может обновить информацию о контактах на Exchange Server с использованием Exchange Web Service (EWS). Метод [IEWSClient->UpdateContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) может обновить информацию о контактах на Exchange Server.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cpp" >}}
## **Удаление контактов**
Класс [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) предоставляет метод [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) для доступа к удалению контактов из папки контактов Exchange Server. Этот метод принимает идентификатор контакта или [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) в качестве входного параметра.

Чтобы удалить контакты с Exchange Server:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) с адресом и учетными данными.
1. Удалите контакт, используя его идентификатор.
1. Удалите контакт, вызвав метод [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) с объектом [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) в качестве входного параметра.

Следующий фрагмент кода показывает вам, как удалить контакты с сервера Exchange, используя [IEWSClient->DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cpp" >}}