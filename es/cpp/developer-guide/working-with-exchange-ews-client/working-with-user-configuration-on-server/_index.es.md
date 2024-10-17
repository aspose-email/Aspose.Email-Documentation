---
title: "Trabajar con la Configuración del Usuario en el Servidor"
url: /es/cpp/working-with-user-configuration-on-server/
weight: 110
type: docs
---

## **Gestionando la Configuración del Usuario**
La API de Aspose.Email se puede utilizar para gestionar la configuración del usuario en un servidor de Exchange con la clase [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/). Esta clase utiliza los servicios web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo, veremos cómo leer, crear, actualizar y eliminar configuraciones de usuario en Exchange Server 2010. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funciones descritas en este artículo. El siguiente fragmento de código muestra cómo conectarse a Exchange Server 2010 en todos los ejemplos de este artículo.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
### **Lectura de la Configuración del Usuario**
Para obtener la información de configuración del usuario de una carpeta específica del servidor de Exchange:

1. Conéctese al servidor de Exchange utilizando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al método [GetUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a33a6fd6cd562b05c84b656a3c2515111) para obtener la configuración del usuario para una carpeta.
1. Muestre las propiedades de configuración del usuario como ID, nombre y elementos del diccionario como pares clave-valor.

El siguiente fragmento de código muestra cómo leer la configuración del usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cpp" >}}
### **Creación de Configuraciones de Usuario**
Para crear la configuración del usuario para una carpeta específica en el servidor de Exchange:

1. Conéctese al servidor de Exchange utilizando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al método [CreateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a5dfcc5761b64ed0d0da8a6e45fc768db) para crear la configuración del usuario para una carpeta.

El siguiente fragmento de código muestra cómo crear configuraciones de usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cpp" >}}
### **Actualización de la Configuración del Usuario**
Para actualizar la configuración del usuario para una carpeta específica en el servidor de Exchange:

1. Conéctese al servidor de Exchange utilizando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al método [UpdateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a0abf4f3032f63918fca528cbf1d4418e) para actualizar la configuración del usuario para una carpeta.

El siguiente fragmento de código muestra cómo actualizar la configuración del usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateUserConfiguration-UpdateUserConfiguration.cpp" >}}
### **Eliminación de la Configuración del Usuario**
Para eliminar la configuración del usuario para una carpeta específica en el servidor de Exchange:

1. Conéctese al servidor de Exchange utilizando [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al método [DeleteUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7e0d6d6b432cf8db13af6638b639806c) para eliminar la configuración del usuario para una carpeta.

El siguiente fragmento de código muestra cómo eliminar la configuración del usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cpp" >}}