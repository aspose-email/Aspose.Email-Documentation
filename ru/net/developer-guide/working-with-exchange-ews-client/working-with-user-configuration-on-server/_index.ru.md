---
title: "Работа с пользовательской конфигурацией на сервере"
url: /ru/net/working-with-user-configuration-on-server/
weight: 110
type: docs
---


## **Управление пользовательской конфигурацией**

Aspose.Email for .NET можно использовать для управления пользовательской конфигурацией на сервере Exchange с помощью [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) класс. В этом классе используются веб-службы Exchange, доступные только в Exchange Server 2007 и более поздних версиях. В этой статье мы рассмотрим, как читать, создавать, обновлять и удалять пользовательские конфигурации в Exchange Server 2010. Для всех функций, описанных в этой статье, требуется пакет обновления 1 для Microsoft Exchange Server 2010. В следующем фрагменте кода показано, как подключиться к Exchange Server 2010 во всех примерах этой статьи.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cs" >}}

### **Чтение пользовательской конфигурации**

Чтобы получить информацию о пользовательской конфигурации определенной папки с сервера Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.GetUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getuserconfiguration/#getuserconfiguration) метод получения пользовательской конфигурации папки.
1. Отображайте свойства пользовательской конфигурации, такие как идентификатор, имя и элементы словаря, в виде пар ключ-значение.

В следующем фрагменте кода показано, как читать конфигурацию пользователя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cs" >}}

### **Создание пользовательских конфигураций**

Чтобы создать пользовательскую конфигурацию для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.CreateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createuserconfiguration/#createuserconfiguration) метод создания пользовательской конфигурации для папки.

В следующем фрагменте кода показано, как создавать пользовательские конфигурации.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cs" >}}

### **Обновление пользовательской конфигурации**

Чтобы обновить конфигурацию пользователя для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.UpdateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateuserconfiguration/#updateuserconfiguration) метод обновления пользовательской конфигурации папки.

В следующем фрагменте кода показано, как обновить конфигурацию пользователя.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateUserConfiguration-UpdatUserConfiguration.cs" >}}

### **Удаление пользовательской конфигурации**

Чтобы удалить пользовательскую конфигурацию для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Позвоните [IEWSClient.DeleteUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteuserconfiguration/#deleteuserconfiguration) метод удаления пользовательской конфигурации папки.

В следующем фрагменте кода показано, как удалить пользовательскую конфигурацию.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cs" >}}
