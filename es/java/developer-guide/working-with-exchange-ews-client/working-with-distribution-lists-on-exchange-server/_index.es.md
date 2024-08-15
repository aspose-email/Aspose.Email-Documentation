---
title: "Trabajar con listas de distribución en Exchange Server"
url: /es/java/working-with-distribution-lists-on-exchange-server/
weight: 70
type: docs
---


## **Trabajando con listas de distribución**
La API Aspose.Email ofrece la capacidad de crear y leer listas de distribuciones desde el servidor Exchange. Las listas de distribución se pueden crear en el servidor y se pueden agregar miembros a él mediante el [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). En este artículo se muestra cómo trabajar con las listas de distribución en el servidor Exchange.
### **Creación de una lista de distribución**
El siguiente fragmento de código muestra cómo crear una lista de distribución.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setDisplayName("test private list");
MailAddressCollection members = new MailAddressCollection();
members.add("address1@host.com");
members.add("address2@host.com");
members.add("address3@host.com");
client.createDistributionList(distributionList, members);
~~~
#### **Obtenga la lista de distribución privada**
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


#### **Ampliar la lista de distribución pública**
El siguiente fragmento de código muestra cómo ampliar la lista de distribución pública.



~~~Java
MailAddressCollection members = client.expandDistributionList(new MailAddress("public.distribution.list@host.com"));
for (MailAddress member : (Iterable<MailAddress>) members) {
    System.out.println(member.getAddress());
}
~~~
### **Añadir miembros**
#### **Agregar miembros a la lista de distribución privada**
El siguiente fragmento de código muestra cómo agregar miembros a una lista de distribución privada.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address4@host.com");
newMembers.add("address5@host.com");
client.addToDistributionList(distributionLists[0], newMembers);
~~~
#### **Añadir miembros sin incluir en la lista**
En el siguiente fragmento de código, se muestra cómo añadir miembros sin incluir en la lista.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("list's id");
distributionList.setChangeKey("list's change key");
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address6@host.com");
client.addToDistributionList(distributionList, newMembers);
~~~
#### **Enviar a la lista de distribución privada**
El siguiente fragmento de código muestra cómo enviar un mensaje a una lista de distribución privada.



~~~Java
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddress distributionListAddress = distributionLists[0].toMailAddress();
MailMessage message = new MailMessage(new MailAddress("from@host.com"), distributionListAddress);
message.setSubject("sendToPrivateDistributionList");
client.send(message);
~~~
### **Eliminar miembros**
#### **Eliminar miembros de la lista de distribución privada**
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
#### **Eliminar miembros sin incluir en la lista**
En el siguiente fragmento de código, se muestra cómo eliminar miembros sin incluirlos en la lista.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("list's id");
distributionList.setChangeKey("list's change key");
MailAddressCollection membersToDelete = new MailAddressCollection();
MailAddress addressToDelete = new MailAddress("address", true);
// addressToDelete.Id.EWSId = "member's id";
membersToDelete.addMailAddress(addressToDelete);
client.addToDistributionList(distributionList, membersToDelete);
~~~


#### **Eliminar lista de distribución privada**
El siguiente fragmento de código muestra cómo eliminar una lista de distribución privada.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
client.deleteDistributionList(distributionLists[0], true);
~~~
#### **Eliminar sin incluir en la lista**
En el siguiente fragmento de código, se muestra cómo eliminar sin incluir en la lista.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("list's id");
client.deleteDistributionList(distributionList, true);
~~~