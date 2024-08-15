---
title: "Работа с контактами на сервере Exchange"
url: /ru/cpp/working-with-contacts-on-exchange-server/
weight: 60
type: docs
---

{{% alert color="primary" %}} Учетные записи Exchange Server содержат больше, чем просто сообщения электронной почты. Помимо получения, перемещения, отправки и удаления сообщений электронной почты с серверов Exchange, Aspose.Email позволяет работать с контактами. В этой статье объясняется, как получить контактную информацию с помощью веб-служб Exchange. В этой статье также показано, как выводить список контактов из папки «Контакты» или разрешать контакты на основе имени контакта. {{% /alert %}}
## **Получение контактов с EWS**
Aspose.Email предоставляет [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс для подключения к серверу Microsoft Exchange с помощью веб-служб Exchange. Следующие фрагменты кода используют веб-службы Exchange для чтения всех контактов. В следующем фрагменте кода показано, как получить контакты с EWS.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-GettingContactsUsingEWS-GettingContactsUsingEWS.cpp" >}}
## **Разрешайте контакты, используя имя контакта**
В следующем фрагменте кода показано, как получить контакты, используя имя контакта.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ResolveContactsUsingContactName-ResolveContactsUsingContactName.cpp" >}}
## **Определение формата контактных заметок**
The [Contact->get_NotesFormat](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) указывает тип текстового формата заметок контактов, определенный [TextFormat](https://apireference.aspose.com/email/cpp/namespace/aspose.email.personal_info) enumerator.
## **Извлечь контакт с помощью идентификатора**
Конкретный контакт можно получить с сервера, используя его идентификатор контакта, как показано в следующем примере кода.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchContactUsingId-FetchContactUsingId.cpp" >}}
## **Добавление контактов**
The [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класс можно использовать для добавления контактной информации на сервер Exchange. [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод принимает [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) объект в качестве входного параметра.

Чтобы добавить контакты на сервер Exchange, выполните следующие действия:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) с адресом и учетными данными.
1. Инициализируйте [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) объект с желаемыми свойствами.
1. Позвоните [CreateContact()](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод и передайте контакт для добавления на сервер Exchange.

Следующий фрагмент кода демонстрирует добавление контактов на сервер Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddContactsToExchangeServerUsingEWS-1.cpp" >}}
## **Обновление контактов**
Контактную информацию можно обновить с помощью Microsoft Outlook. Aspose.Email также может обновлять контактную информацию на сервере Exchange с помощью веб-службы Exchange (EWS). [IEWSClient->UpdateContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод может обновлять контактную информацию на сервере Exchange.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateContactInformationUsingEWS-UpdateContactInformationUsingEWS.cpp" >}}
## **Удаление контактов**
The [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) класс предоставляет [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) для доступа к контактам и их удаления из папки контактов сервера Exchange. В этом методе используется идентификатор контакта или [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) в качестве входного параметра.

Чтобы удалить контакты с сервера Exchange, выполните следующие действия:

1. Инициализируйте [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) с адресом и учетными данными.
1. Удалите контакт, используя его идентификатор.
1. Удалите контакт, позвонив в [DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) метод с [Contact](https://apireference.aspose.com/email/cpp/class/aspose.email.personal_info.contact) в качестве входного параметра.

В следующем фрагменте кода показано, как удалить контакты с сервера Exchange с помощью [IEWSClient->DeleteContact](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteContactsFromExchangeServerUsingEWS-DeleteContactsFromExchangeServerUsingEWS.cpp" >}}
