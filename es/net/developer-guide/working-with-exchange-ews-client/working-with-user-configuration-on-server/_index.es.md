---
title: "Trabajando con la Configuración del Usuario en el Servidor"
url: /es/net/working-with-user-configuration-on-server/
weight: 110
type: docs
---

## **Gestionando la Configuración del Usuario**

Aspose.Email para .NET se puede usar para gestionar la configuración del usuario en un servidor Exchange con la clase [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/). Esta clase utiliza Servicios Web de Exchange, que están disponibles solo en Exchange Server 2007 y versiones posteriores. En este artículo, veremos cómo leer, crear, actualizar y eliminar configuraciones de usuario en Exchange Server 2010. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las características descritas en este artículo. El siguiente fragmento de código te muestra cómo conectarte a Exchange Server 2010 en todos los ejemplos de este artículo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cs" >}}

### **Leyendo la Configuración del Usuario**

Para obtener la información de configuración del usuario de una carpeta específica del servidor Exchange:

1. Conéctate al servidor Exchange usando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llama al método [IEWSClient.GetUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getuserconfiguration/#getuserconfiguration) para obtener la configuración del usuario para una carpeta.
1. Muestra las propiedades de configuración del usuario como ID, nombre y elementos del diccionario como pares clave-valor.

El siguiente fragmento de código te muestra cómo leer la configuración del usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cs" >}}

### **Creando Configuraciones de Usuario**

Para crear la configuración del usuario para una carpeta específica en un servidor Exchange:

1. Conéctate al servidor Exchange usando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llama al método [IEWSClient.CreateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createuserconfiguration/#createuserconfiguration) para crear la configuración del usuario para una carpeta.

El siguiente fragmento de código te muestra cómo crear configuraciones de usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cs" >}}

### **Actualizando la Configuración del Usuario**

Para actualizar la configuración del usuario para una carpeta específica en el servidor Exchange:

1. Conéctate al servidor Exchange usando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llama al método [IEWSClient.UpdateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateuserconfiguration/#updateuserconfiguration) para actualizar la configuración del usuario para una carpeta.

El siguiente fragmento de código te muestra cómo actualizar la configuración del usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateUserConfiguration-UpdatUserConfiguration.cs" >}}

### **Eliminando la Configuración del Usuario**

Para eliminar la configuración del usuario para una carpeta específica en el servidor Exchange:

1. Conéctate al servidor Exchange usando la interfaz [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/).
1. Llama al método [IEWSClient.DeleteUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteuserconfiguration/#deleteuserconfiguration) para eliminar la configuración del usuario para una carpeta.

El siguiente fragmento de código te muestra cómo eliminar la configuración del usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cs" >}}