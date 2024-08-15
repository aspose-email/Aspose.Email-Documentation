---
title: "Trabajar con listas de distribución en Exchange Server"
url: /es/net/working-with-distribution-lists-on-exchange-server/
weight: 70
type: docs
---


## **Trabajando con listas de distribución**

La API Aspose.Email ofrece la capacidad de crear y leer listas de distribuciones desde el servidor Exchange. Las listas de distribución se pueden crear en el servidor y se pueden agregar miembros a él mediante el [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/). En este artículo se muestra cómo trabajar con las listas de distribución en el servidor Exchange.

### **Creación de una lista de distribución**

El siguiente fragmento de código muestra cómo crear una lista de distribución.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatePrivateDistributionList-CreatePrivateDistributionList.cs" >}}

#### **Obtenga la lista de distribución privada**

El siguiente fragmento de código muestra cómo obtener una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-FetchPrivateDistributionList-FetchPrivateDistributionList.cs" >}}

#### **Crear dirección de correo a partir del identificador de la lista de distribución**

El siguiente fragmento de código muestra cómo crear MailAddress a partir del identificador de la lista de distribución.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange-CreateMailAddressFromDistributionListId-CreateMailAddressFromDistributionListId.cs" >}}

#### **Ampliar la lista de distribución pública**

El siguiente fragmento de código muestra cómo ampliar la lista de distribución pública.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ExpandPublicDistributionList-ExpandPublicDistributionList.cs" >}}

### **Añadir miembros**

#### **Agregar miembros a la lista de distribución privada**

El siguiente fragmento de código muestra cómo agregar miembros a una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AddMembersToPrivateDistributionList-AddMembersToPrivateDistributionList.cs" >}}

#### **Añadir miembros sin incluir en la lista**

En el siguiente fragmento de código, se muestra cómo añadir miembros sin incluir en la lista.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-AddMembersWithoutListing-AddMembersWithoutListing.cs" >}}

#### **Enviar a la lista de distribución privada**

El siguiente fragmento de código muestra cómo enviar un mensaje a una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-SendEmailToPrivateDistributionList-SendEmailToPrivateDistributionList.cs" >}}

### **Eliminar miembros**

#### **Eliminar miembros de la lista de distribución privada**

El siguiente fragmento de código muestra cómo eliminar miembros de una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteMembersFromPrivateDistributionList-DeleteMembersFromPrivateDistributionList.cs" >}}

#### **Eliminar miembros sin incluir en la lista**

En el siguiente fragmento de código, se muestra cómo eliminar miembros sin incluirlos en la lista.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteMembersWithoutListing-DeleteMembersWithoutListing.cs" >}}

#### **Eliminar lista de distribución privada**

El siguiente fragmento de código muestra cómo eliminar una lista de distribución privada.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeletePrivateDistributionList-DeletePrivateDistributionList.cs" >}}

#### **Eliminar sin incluir en la lista**

En el siguiente fragmento de código, se muestra cómo eliminar sin incluir en la lista.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteWithoutListing-DeleteWithoutListing.cs" >}}
