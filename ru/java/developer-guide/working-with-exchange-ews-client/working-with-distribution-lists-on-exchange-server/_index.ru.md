---
title: "Работа со списками рассылки на сервере Exchange"
url: /ru/java/working-with-distribution-lists-on-exchange-server/
weight: 70
type: docs
---


## **Работа со списками рассылки**
Aspose.Email API предоставляет возможность создавать и читать списки рассылки с сервера Exchange. Списки рассылки можно создавать на сервере, а также добавлять в него участников с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). В этой статье показано, как работать со списками рассылки на сервере Exchange.
### **Создание списка рассылки**
В следующем фрагменте кода показано, как создать список рассылки.



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
#### **Получите список частных рассылок**
В следующем фрагменте кода показано, как получить частный список рассылки.



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


#### **Расширить публичный список рассылки**
В следующем фрагменте кода показано, как расширить список общедоступной рассылки.



~~~Java
MailAddressCollection members = client.expandDistributionList(new MailAddress("public.distribution.list@host.com"));
for (MailAddress member : (Iterable<MailAddress>) members) {
    System.out.println(member.getAddress());
}
~~~
### **Добавление участников**
#### **Добавление участников в частный список рассылки**
В следующем фрагменте кода показано, как добавить участников в частный список рассылки.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address4@host.com");
newMembers.add("address5@host.com");
client.addToDistributionList(distributionLists[0], newMembers);
~~~
#### **Добавить участников без объявления**
В следующем фрагменте кода показано, как добавлять участников без объявления.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("list's id");
distributionList.setChangeKey("list's change key");
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address6@host.com");
client.addToDistributionList(distributionList, newMembers);
~~~
#### **Отправить в частный список рассылки**
В следующем фрагменте кода показано, как отправить сообщение в частный список рассылки.



~~~Java
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddress distributionListAddress = distributionLists[0].toMailAddress();
MailMessage message = new MailMessage(new MailAddress("from@host.com"), distributionListAddress);
message.setSubject("sendToPrivateDistributionList");
client.send(message);
~~~
### **Удаление участников**
#### **Удаление участников из частного списка рассылки**
В следующем фрагменте кода показано, как удалить участников из частного списка рассылки.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection members = client.fetchDistributionList(distributionLists[0]);
MailAddressCollection membersToDelete = new MailAddressCollection();
membersToDelete.addMailAddress(members.get_Item(0));
membersToDelete.addMailAddress(members.get_Item(1));
client.deleteFromDistributionList(distributionLists[0], membersToDelete);
~~~
#### **Удалить участников без объявления**
В следующем фрагменте кода показано, как удалять участников без объявления.



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


#### **Удалить частный список рассылки**
В следующем фрагменте кода показано, как удалить частный список рассылки.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
client.deleteDistributionList(distributionLists[0], true);
~~~
#### **Удалить без объявления**
В следующем фрагменте кода показано, как удалить файл без добавления в список.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("list's id");
client.deleteDistributionList(distributionList, true);
~~~