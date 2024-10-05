---
title: Работа с пользовательской конфигурацией на сервере
type: docs
weight: 110
url: /net/working-with-user-configuration-on-server/
---


## **Управление пользовательской конфигурацией**

Aspose.Email для .NET может быть использован для управления пользовательской конфигурацией на сервере Exchange с помощью класса [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Этот класс использует Exchange Web Services, которые доступны только в Exchange Server 2007 и более поздних версиях. В этой статье мы рассмотрим, как читать, создавать, обновлять и удалять пользовательские конфигурации на Exchange Server 2010. Для всех функций, описанных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1. Следующий фрагмент кода показывает, как подключиться к Exchange Server 2010 во всех примерах этой статьи.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cs" >}}

### **Чтение пользовательской конфигурации**

Чтобы получить информацию о пользовательской конфигурации конкретной папки с сервера Exchange:

1. Подключитесь к серверу Exchange с помощью интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.GetUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getuserconfiguration/#getuserconfiguration), чтобы получить пользовательскую конфигурацию для папки.
1. Отобразите свойства пользовательской конфигурации, такие как ID, имя и элементы словаря в виде пар "ключ-значение".

Следующий фрагмент кода показывает, как читать пользовательскую конфигурацию.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cs" >}}

### **Создание пользовательских конфигураций**

Чтобы создать пользовательскую конфигурацию для конкретной папки на сервере Exchange:

1. Подключитесь к серверу Exchange с помощью интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.CreateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createuserconfiguration/#createuserconfiguration), чтобы создать пользовательскую конфигурацию для папки.

Следующий фрагмент кода показывает, как создавать пользовательские конфигурации.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cs" >}}

### **Обновление пользовательской конфигурации**

Чтобы обновить пользовательскую конфигурацию для конкретной папки на сервере Exchange:

1. Подключитесь к серверу Exchange с помощью интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.UpdateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateuserconfiguration/#updateuserconfiguration), чтобы обновить пользовательскую конфигурацию для папки.

Следующий фрагмент кода показывает, как обновить пользовательскую конфигурацию.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateUserConfiguration-UpdatUserConfiguration.cs" >}}

### **Удаление пользовательской конфигурации**

Чтобы удалить пользовательскую конфигурацию для конкретной папки на сервере Exchange:

1. Подключитесь к серверу Exchange с помощью интерфейса [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Вызовите метод [IEWSClient.DeleteUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteuserconfiguration/#deleteuserconfiguration), чтобы удалить пользовательскую конфигурацию для папки.

Следующий фрагмент кода показывает, как удалить пользовательскую конфигурацию.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cs" >}}