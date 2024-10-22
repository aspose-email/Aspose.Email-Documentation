---
title: "Trabajando con Listas de Distribución en Exchange Server"
url: /es/net/working-with-distribution-lists-on-exchange-server/
weight: 70
type: docs
---


## **Trabajando con Listas de Distribución**

La API Aspose.Email proporciona la capacidad de crear y leer listas de distribución desde el servidor de Exchange. Las listas de distribución se pueden crear en el servidor y los miembros se pueden añadir a ellas utilizando el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). Este artículo muestra cómo trabajar con listas de distribución en el servidor de Exchange.

### **Creando una Lista de Distribución**

El siguiente fragmento de código muestra cómo crear una lista de distribución.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatePrivateDistributionList-CreatePrivateDistributionList.cs" >}}

#### **Obtener Lista de Distribución Privada**

El siguiente fragmento de código muestra cómo obtener una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FetchPrivateDistributionList-FetchPrivateDistributionList.cs" >}}

#### **Crear MailAddress a partir del Id de la Lista de Distribución**

El siguiente fragmento de código muestra cómo crear MailAddress a partir del Id de la lista de distribución.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateMailAddressFromDistributionListId-CreateMailAddressFromDistributionListId.cs" >}}

#### **Expandir Lista de Distribución Pública**

El siguiente fragmento de código muestra cómo expandir la lista de distribución pública.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExpandPublicDistributionList-ExpandPublicDistributionList.cs" >}}

### **Añadiendo miembros**

#### **Añadiendo miembros a una Lista de Distribución Privada**

El siguiente fragmento de código muestra cómo añadir miembros a una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AddMembersToPrivateDistributionList-AddMembersToPrivateDistributionList.cs" >}}

#### **Añadir miembros sin listar**

El siguiente fragmento de código muestra cómo añadir miembros sin listar.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AddMembersWithoutListing-AddMembersWithoutListing.cs" >}}

#### **Enviar a Lista de Distribución Privada**

El siguiente fragmento de código muestra cómo enviar un mensaje a una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendEmailToPrivateDistributionList-SendEmailToPrivateDistributionList.cs" >}}

### **Eliminando miembros**

#### **Eliminando miembros de una Lista de Distribución Privada**

El siguiente fragmento de código muestra cómo eliminar miembros de una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteMembersFromPrivateDistributionList-DeleteMembersFromPrivateDistributionList.cs" >}}

#### **Eliminar miembros sin listar**

El siguiente fragmento de código muestra cómo eliminar miembros sin listar.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteMembersWithoutListing-DeleteMembersWithoutListing.cs" >}}

#### **Eliminar Lista de Distribución Privada**

El siguiente fragmento de código muestra cómo eliminar una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeletePrivateDistributionList-DeletePrivateDistributionList.cs" >}}

#### **Eliminar sin Listar**

El siguiente fragmento de código muestra cómo eliminar sin listar.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteWithoutListing-DeleteWithoutListing.cs" >}}