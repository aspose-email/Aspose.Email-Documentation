---
title: "Trabajando con la configuración de usuario en el servidor"
url: /es/net/working-with-user-configuration-on-server/
weight: 110
type: docs
---


## **Administración de la configuración de usuario**

Aspose.Email para.NET se puede usar para administrar la configuración de usuario en un servidor Exchange con [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) clase. Esta clase usa los servicios web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo, veremos cómo leer, crear, actualizar y eliminar las configuraciones de usuario en Exchange Server 2010. Todas las funciones descritas en este artículo requieren el Service Pack 1 de Microsoft Exchange Server 2010. El siguiente fragmento de código muestra cómo conectarse a Exchange Server 2010 en todos los ejemplos de este artículo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cs" >}}

### **Lectura de la configuración del usuario**

Para obtener la información de configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese a Exchange Server mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.GetUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getuserconfiguration/#getuserconfiguration) método para obtener la configuración de usuario de una carpeta.
1. Muestre las propiedades de configuración del usuario, como el ID, el nombre y los elementos del diccionario, como pares clave-valor.

El siguiente fragmento de código muestra cómo leer la configuración del usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cs" >}}

### **Creación de configuraciones de usuario**

Para crear la configuración de usuario para una carpeta específica en un servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.CreateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createuserconfiguration/#createuserconfiguration) método para crear la configuración de usuario para una carpeta.

El siguiente fragmento de código muestra cómo crear configuraciones de usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cs" >}}

### **Actualización de la configuración de usuario**

Para actualizar la configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.UpdateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateuserconfiguration/#updateuserconfiguration) método para actualizar la configuración de usuario de una carpeta.

El siguiente fragmento de código muestra cómo actualizar la configuración del usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateUserConfiguration-UpdatUserConfiguration.cs" >}}

### **Eliminar la configuración de usuario**

Para eliminar la configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Llame al [IEWSClient.DeleteUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteuserconfiguration/#deleteuserconfiguration) método para eliminar la configuración de usuario de una carpeta.

El siguiente fragmento de código muestra cómo eliminar la configuración de usuario.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cs" >}}
