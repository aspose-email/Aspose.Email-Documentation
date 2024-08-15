---
title: "Работа с пользовательской конфигурацией на сервере"
url: /ru/cpp/working-with-user-configuration-on-server/
weight: 110
type: docs
---

## **Управление пользовательской конфигурацией**
API Aspose.Email можно использовать для управления пользовательской конфигурацией на сервере Exchange с помощью [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) класс. В этом классе используются веб-службы Exchange, доступные только в Exchange Server 2007 и более поздних версиях. В этой статье мы рассмотрим, как читать, создавать, обновлять и удалять пользовательские конфигурации в Exchange Server 2010. Для всех функций, описанных в этой статье, требуется пакет обновления 1 для Microsoft Exchange Server 2010. В следующем фрагменте кода показано, как подключиться к Exchange Server 2010 во всех примерах этой статьи.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
### **Чтение пользовательской конфигурации**
Чтобы получить информацию о пользовательской конфигурации определенной папки с сервера Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Позвоните [GetUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a33a6fd6cd562b05c84b656a3c2515111) метод получения пользовательской конфигурации папки.
1. Отображайте свойства пользовательской конфигурации, такие как идентификатор, имя и элементы словаря, в виде пар ключ-значение.

В следующем фрагменте кода показано, как читать конфигурацию пользователя.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cpp" >}}
### **Создание пользовательских конфигураций**
Чтобы создать пользовательскую конфигурацию для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Позвоните [CreateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a5dfcc5761b64ed0d0da8a6e45fc768db) метод создания пользовательской конфигурации для папки.

В следующем фрагменте кода показано, как создавать пользовательские конфигурации.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cpp" >}}
### **Обновление пользовательской конфигурации**
Чтобы обновить конфигурацию пользователя для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Позвоните [UpdateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a0abf4f3032f63918fca528cbf1d4418e) метод обновления пользовательской конфигурации папки.

В следующем фрагменте кода показано, как обновить конфигурацию пользователя.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateUserConfiguration-UpdateUserConfiguration.cpp" >}}
### **Удаление пользовательской конфигурации**
Чтобы удалить пользовательскую конфигурацию для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Позвоните [DeleteUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7e0d6d6b432cf8db13af6638b639806c) метод удаления пользовательской конфигурации папки.

В следующем фрагменте кода показано, как удалить пользовательскую конфигурацию.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cpp" >}}
