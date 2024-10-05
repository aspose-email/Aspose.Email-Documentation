---
title: "Работа с пользовательской конфигурацией на сервере"
url: /ru/cpp/working-with-user-configuration-on-server/
weight: 110
type: docs
---

## **Управление пользовательской конфигурацией**
API Aspose.Email может быть использован для управления пользовательской конфигурацией на сервере Exchange с помощью класса [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/). Этот класс использует службы веб Exchange, которые доступны только в Exchange Server 2007 и более поздних версиях. В этой статье мы рассмотрим, как читать, создавать, обновлять и удалять пользовательские конфигурации на Exchange Server 2010. Для всех функций, описанных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1. Следующий фрагмент кода показывает, как подключиться к Exchange Server 2010 во всех примерах этой статьи.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
### **Чтение пользовательской конфигурации**
Чтобы получить информацию о пользовательской конфигурации конкретной папки с сервера Exchange:

1. Подключитесь к серверу Exchange, используя [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Вызовите метод [GetUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a33a6fd6cd562b05c84b656a3c2515111), чтобы получить пользовательскую конфигурацию для папки.
1. Отобразите свойства пользовательской конфигурации, такие как ID, имя и элементы словаря в виде пар ключ-значение.

Следующий фрагмент кода показывает, как читать пользовательскую конфигурацию.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cpp" >}}
### **Создание пользовательских конфигураций**
Чтобы создать пользовательскую конфигурацию для конкретной папки на сервере Exchange:

1. Подключитесь к серверу Exchange, используя [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Вызовите метод [CreateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a5dfcc5761b64ed0d0da8a6e45fc768db), чтобы создать пользовательскую конфигурацию для папки.

Следующий фрагмент кода показывает, как создавать пользовательские конфигурации.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cpp" >}}
### **Обновление пользовательской конфигурации**
Чтобы обновить пользовательскую конфигурацию для конкретной папки на сервере Exchange:

1. Подключитесь к серверу Exchange, используя [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Вызовите метод [UpdateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a0abf4f3032f63918fca528cbf1d4418e), чтобы обновить пользовательскую конфигурацию для папки.

Следующий фрагмент кода показывает, как обновлять пользовательскую конфигурацию.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateUserConfiguration-UpdateUserConfiguration.cpp" >}}
### **Удаление пользовательской конфигурации**
Чтобы удалить пользовательскую конфигурацию для конкретной папки на сервере Exchange:

1. Подключитесь к серверу Exchange, используя [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Вызовите метод [DeleteUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7e0d6d6b432cf8db13af6638b639806c), чтобы удалить пользовательскую конфигурацию для папки.

Следующий фрагмент кода показывает, как удалять пользовательскую конфигурацию.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cpp" >}}