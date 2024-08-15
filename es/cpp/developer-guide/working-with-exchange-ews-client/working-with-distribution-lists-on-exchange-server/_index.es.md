---
title: "Trabajar con listas de distribución en Exchange Server"
url: /es/cpp/working-with-distribution-lists-on-exchange-server/
weight: 70
type: docs
---

## **Trabajando con listas de distribución**
La API Aspose.Email ofrece la capacidad de crear y leer listas de distribuciones desde el servidor Exchange. Las listas de distribución se pueden crear en el servidor y se pueden agregar miembros a él mediante el [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). En este artículo se muestra cómo trabajar con las listas de distribución en el servidor Exchange.
### **Creación de una lista de distribución**
El siguiente fragmento de código muestra cómo crear una lista de distribución.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatePrivateDistributionList-CreatePrivateDistributionList.cpp" >}}
#### **Obtenga la lista de distribución privada**
El siguiente fragmento de código muestra cómo obtener una lista de distribución privada.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchPrivateDistributionList-FetchPrivateDistributionList.cpp" >}}
#### **Ampliar la lista de distribución pública**
El siguiente fragmento de código muestra cómo ampliar la lista de distribución pública.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExpandPublicDistributionList-ExpandPublicDistributionList.cpp" >}}
### **Añadir miembros**
#### **Agregar miembros a una lista de distribución privada**
El siguiente fragmento de código muestra cómo agregar miembros a una lista de distribución privada.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddMembersToPrivateDistributionList-AddMembersToPrivateDistributionList.cpp" >}}
#### **Añadir miembros sin incluir en la lista**
En el siguiente fragmento de código, se muestra cómo añadir miembros sin incluir en la lista.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddMembersWithoutListing-AddMembersWithoutListing.cpp" >}}
#### **Enviar correo electrónico a la lista de distribución privada**
El siguiente fragmento de código muestra cómo enviar correos electrónicos a una lista de distribución privada.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailToPrivateDistributionList-SendEmailToPrivateDistributionList.cpp" >}}
### **Eliminar miembros**
#### **Eliminar miembros de la lista de distribución privada**
El siguiente fragmento de código muestra cómo eliminar miembros de una lista de distribución privada.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMembersFromPrivateDistributionList-DeleteMembersFromPrivateDistributionList.cpp" >}}
#### **Eliminar miembros sin incluir en la lista**
En el siguiente fragmento de código, se muestra cómo eliminar miembros sin incluirlos en la lista.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMembersWithoutListing-DeleteMembersWithoutListing.cpp" >}}
#### **Eliminar lista de distribución privada**
El siguiente fragmento de código muestra cómo eliminar una lista de distribución privada.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeletePrivateDistributionList-DeletePrivateDistributionList.cpp" >}}
#### **Eliminar sin incluir en la lista**
En el siguiente fragmento de código, se muestra cómo eliminar sin incluir en la lista.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteWithoutListing-DeleteWithoutListing.cpp" >}}
