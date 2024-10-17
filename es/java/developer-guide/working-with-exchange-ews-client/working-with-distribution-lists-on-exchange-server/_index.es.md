---
title: "Trabajando con Listas de Distribución en Exchange Server"
url: /es/java/trabajando-con-listas-de-distribucion-en-exchange-server/
weight: 70
type: docs
---

## **Trabajando con Listas de Distribución**
Aspose.Email API proporciona la capacidad de crear y leer listas de distribución desde el servidor de Exchange. Las listas de distribución se pueden crear en el servidor y también se pueden agregar miembros utilizando el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Este artículo muestra cómo trabajar con listas de distribución en el servidor de Exchange.
### **Creando una Lista de Distribución**
El siguiente fragmento de código muestra cómo crear una lista de distribución.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setDisplayName("lista privada de prueba");
MailAddressCollection members = new MailAddressCollection();
members.add("address1@host.com");
members.add("address2@host.com");
members.add("address3@host.com");
client.createDistributionList(distributionList, members);
~~~
#### **Obtener Lista de Distribución Privada**
El siguiente fragmento de código muestra cómo obtener una lista de distribución privada.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
for (ExchangeDistributionList distributionList : distributionLists) {
    MailAddressCollection members = client.fetchDistributionList(distributionList);
    for (MailAddress member : (Iterable<MailAddress>) members) {
        System.out.println(member.getAddress());
    }
}
~~~

#### **Expandir Lista de Distribución Pública**
El siguiente fragmento de código muestra cómo expandir la lista de distribución pública.

~~~Java
MailAddressCollection members = client.expandDistributionList(new MailAddress("public.distribution.list@host.com"));
for (MailAddress member : (Iterable<MailAddress>) members) {
    System.out.println(member.getAddress());
}
~~~
### **Agregando miembros**
#### **Agregando miembros a Lista de Distribución Privada**
El siguiente fragmento de código muestra cómo agregar miembros a una lista de distribución privada.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address4@host.com");
newMembers.add("address5@host.com");
client.addToDistributionList(distributionLists[0], newMembers);
~~~
#### **Agregar miembros sin listar**
El siguiente fragmento de código muestra cómo agregar miembros sin listar.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("id de la lista");
distributionList.setChangeKey("clave de cambio de la lista");
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address6@host.com");
client.addToDistributionList(distributionList, newMembers);
~~~
#### **Enviar a Lista de Distribución Privada**
El siguiente fragmento de código muestra cómo enviar un mensaje a una lista de distribución privada.

~~~Java
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddress distributionListAddress = distributionLists[0].toMailAddress();
MailMessage message = new MailMessage(new MailAddress("from@host.com"), distributionListAddress);
message.setSubject("sendToPrivateDistributionList");
client.send(message);
~~~
### **Eliminando miembros**
#### **Eliminando miembros de Lista de Distribución Privada**
El siguiente fragmento de código muestra cómo eliminar miembros de una lista de distribución privada.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection members = client.fetchDistributionList(distributionLists[0]);
MailAddressCollection membersToDelete = new MailAddressCollection();
membersToDelete.addMailAddress(members.get_Item(0));
membersToDelete.addMailAddress(members.get_Item(1));
client.deleteFromDistributionList(distributionLists[0], membersToDelete);
~~~
#### **Eliminar miembros sin listar**
El siguiente fragmento de código muestra cómo eliminar miembros sin listar.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("id de la lista");
distributionList.setChangeKey("clave de cambio de la lista");
MailAddressCollection membersToDelete = new MailAddressCollection();
MailAddress addressToDelete = new MailAddress("address", true);
// addressToDelete.Id.EWSId = "id del miembro";
membersToDelete.addMailAddress(addressToDelete);
client.addToDistributionList(distributionList, membersToDelete);
~~~

#### **Eliminar Lista de Distribución Privada**
El siguiente fragmento de código muestra cómo eliminar una lista de distribución privada.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
client.deleteDistributionList(distributionLists[0], true);
~~~
#### **Eliminar sin listar**
El siguiente fragmento de código muestra cómo eliminar sin listar.

~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("id de la lista");
client.deleteDistributionList(distributionList, true);
~~~