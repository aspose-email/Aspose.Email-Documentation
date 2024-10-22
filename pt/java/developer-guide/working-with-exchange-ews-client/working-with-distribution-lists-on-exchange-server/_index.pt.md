---
title: "Trabalhando com Listas de Distribuição no Exchange Server"
url: /pt/java/trabalhando-com-listas-de-distribuicao-no-exchange-server/
weight: 70
type: docs
---


## **Trabalhando com Listas de Distribuição**
A API Aspose.Email fornece a capacidade de criar e ler listas de distribuição do servidor Exchange. As listas de distribuição podem ser criadas no servidor, assim como os membros podem ser adicionados a ela usando o [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Este artigo mostra como trabalhar com listas de distribuição no servidor Exchange.
### **Criando Lista de Distribuição**
O seguinte trecho de código mostra como criar uma lista de distribuição.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setDisplayName("lista privada de teste");
MailAddressCollection members = new MailAddressCollection();
members.add("address1@host.com");
members.add("address2@host.com");
members.add("address3@host.com");
client.createDistributionList(distributionList, members);
~~~
#### **Buscar Lista de Distribuição Privada**
O seguinte trecho de código mostra como buscar uma lista de distribuição privada.



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


#### **Expandir Lista de Distribuição Pública**
O seguinte trecho de código mostra como expandir a lista de distribuição pública.



~~~Java
MailAddressCollection members = client.expandDistributionList(new MailAddress("public.distribution.list@host.com"));
for (MailAddress member : (Iterable<MailAddress>) members) {
    System.out.println(member.getAddress());
}
~~~ 
### **Adicionando membros**
#### **Adicionando membros à Lista de Distribuição Privada**
O seguinte trecho de código mostra como adicionar membros a uma lista de distribuição privada.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address4@host.com");
newMembers.add("address5@host.com");
client.addToDistributionList(distributionLists[0], newMembers);
~~~ 
#### **Adicionar membros sem listagem**
O seguinte trecho de código mostra como adicionar membros sem listagem.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("id da lista");
distributionList.setChangeKey("chave de alteração da lista");
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address6@host.com");
client.addToDistributionList(distributionList, newMembers);
~~~ 
#### **Enviar para Lista de Distribuição Privada**
O seguinte trecho de código mostra como enviar uma mensagem para uma lista de distribuição privada.



~~~Java
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddress distributionListAddress = distributionLists[0].toMailAddress();
MailMessage message = new MailMessage(new MailAddress("from@host.com"), distributionListAddress);
message.setSubject("sendToPrivateDistributionList");
client.send(message);
~~~ 
### **Excluindo membros**
#### **Excluindo membros da Lista de Distribuição Privada**
O seguinte trecho de código mostra como excluir membros de uma lista de distribuição privada.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection members = client.fetchDistributionList(distributionLists[0]);
MailAddressCollection membersToDelete = new MailAddressCollection();
membersToDelete.addMailAddress(members.get_Item(0));
membersToDelete.addMailAddress(members.get_Item(1));
client.deleteFromDistributionList(distributionLists[0], membersToDelete);
~~~ 
#### **Excluir membros sem listagem**
O seguinte trecho de código mostra como excluir membros sem listagem.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("id da lista");
distributionList.setChangeKey("chave de alteração da lista");
MailAddressCollection membersToDelete = new MailAddressCollection();
MailAddress addressToDelete = new MailAddress("address", true);
// addressToDelete.Id.EWSId = "id do membro";
membersToDelete.addMailAddress(addressToDelete);
client.addToDistributionList(distributionList, membersToDelete);
~~~


#### **Excluir Lista de Distribuição Privada**
O seguinte trecho de código mostra como excluir uma lista de distribuição privada.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
client.deleteDistributionList(distributionLists[0], true);
~~~ 
#### **Excluir sem Listagem**
O seguinte trecho de código mostra como excluir sem listagem.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("id da lista");
client.deleteDistributionList(distributionList, true);
~~~