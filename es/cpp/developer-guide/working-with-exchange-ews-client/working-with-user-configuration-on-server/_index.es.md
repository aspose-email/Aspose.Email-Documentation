---
title: "Trabajando con la configuración de usuario en el servidor"
url: /es/cpp/working-with-user-configuration-on-server/
weight: 110
type: docs
---

## **Administración de la configuración de usuario**
La API Aspose.Email se puede usar para administrar la configuración de los usuarios en un servidor Exchange con [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) clase. Esta clase usa los servicios web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo, veremos cómo leer, crear, actualizar y eliminar las configuraciones de usuario en Exchange Server 2010. Todas las funciones descritas en este artículo requieren el Service Pack 1 de Microsoft Exchange Server 2010. El siguiente fragmento de código muestra cómo conectarse a Exchange Server 2010 en todos los ejemplos de este artículo.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
### **Lectura de la configuración del usuario**
Para obtener la información de configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese a Exchange Server mediante [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al [GetUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a33a6fd6cd562b05c84b656a3c2515111) método para obtener la configuración de usuario de una carpeta.
1. Muestre las propiedades de configuración del usuario, como el ID, el nombre y los elementos del diccionario, como pares clave-valor.

El siguiente fragmento de código muestra cómo leer la configuración del usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cpp" >}}
### **Creación de configuraciones de usuario**
Para crear la configuración de usuario para una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al [CreateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a5dfcc5761b64ed0d0da8a6e45fc768db) método para crear la configuración de usuario para una carpeta.

El siguiente fragmento de código muestra cómo crear configuraciones de usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cpp" >}}
### **Actualización de la configuración de usuario**
Para actualizar la configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al [UpdateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a0abf4f3032f63918fca528cbf1d4418e) método para actualizar la configuración de usuario de una carpeta.

El siguiente fragmento de código muestra cómo actualizar la configuración del usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateUserConfiguration-UpdateUserConfiguration.cpp" >}}
### **Eliminar la configuración de usuario**
Para eliminar la configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Llame al [DeleteUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7e0d6d6b432cf8db13af6638b639806c) método para eliminar la configuración de usuario de una carpeta.

El siguiente fragmento de código muestra cómo eliminar la configuración de usuario.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cpp" >}}
