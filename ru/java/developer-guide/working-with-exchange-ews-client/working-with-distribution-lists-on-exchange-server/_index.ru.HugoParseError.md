---
title: Работа с рассылками на Exchange Server
type: docs
weight: 70
url: /java/working-with-distribution-lists-on-exchange-server/
---


## **Работа с рассылками**
Aspose.Email API предоставляет возможность создавать и читать списки рассылки с сервера Exchange. Списки рассылки могут быть созданы на сервере, а также члены могут быть добавлены в них с помощью [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient). Эта статья описывает, как работать с рассылками на сервере Exchange.
### **Создание списка рассылки**
Следующий фрагмент кода показывает, как создать список рассылки.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setDisplayName("тестовый частный список");
MailAddressCollection members = new MailAddressCollection();
members.add("address1@host.com");
members.add("address2@host.com");
members.add("address3@host.com");
client.createDistributionList(distributionList, members);
~~~
#### **Получение частного списка рассылки**
Следующий фрагмент кода показывает, как получить частный список рассылки.



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


#### **Расширение публичного списка рассылки**
Следующий фрагмент кода показывает, как расширить публичный список рассылки.



~~~Java
MailAddressCollection members = client.expandDistributionList(new MailAddress("public.distribution.list@host.com"));
for (MailAddress member : (Iterable<MailAddress>) members) {
    System.out.println(member.getAddress());
}
~~~
### **Добавление членов**
#### **Добавление членов в частный список рассылки**
Следующий фрагмент кода показывает, как добавить членов в частный список рассылки.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address4@host.com");
newMembers.add("address5@host.com");
client.addToDistributionList(distributionLists[0], newMembers);
~~~
#### **Добавление членов без списка**
Следующий фрагмент кода показывает, как добавить членов без списка.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("идентификатор списка");
distributionList.setChangeKey("ключ изменения списка");
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address6@host.com");
client.addToDistributionList(distributionList, newMembers);
~~~
#### **Отправить в частный список рассылки**
Следующий фрагмент кода показывает, как отправить сообщение в частный список рассылки.



~~~Java
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddress distributionListAddress = distributionLists[0].toMailAddress();
MailMessage message = new MailMessage(new MailAddress("from@host.com"), distributionListAddress);
message.setSubject("sendToPrivateDistributionList");
client.send(message);
~~~
### **Удаление членов**
#### **Удаление членов из частного списка рассылки**
Следующий фрагмент кода показывает, как удалить членов из частного списка рассылки.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection members = client.fetchDistributionList(distributionLists[0]);
MailAddressCollection membersToDelete = new MailAddressCollection();
membersToDelete.addMailAddress(members.get_Item(0));
membersToDelete.addMailAddress(members.get_Item(1));
client.deleteFromDistributionList(distributionLists[0], membersToDelete);
~~~
#### **Удаление членов без списка**
Следующий фрагмент кода показывает, как удалить членов без списка.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("идентификатор списка");
distributionList.setChangeKey("ключ изменения списка");
MailAddressCollection membersToDelete = new MailAddressCollection();
MailAddress addressToDelete = new MailAddress("address", true);
// addressToDelete.Id.EWSId = "идентификатор члена";
membersToDelete.addMailAddress(addressToDelete);
client.addToDistributionList(distributionList, membersToDelete);
~~~


#### **Удаление частного списка рассылки**
Следующий фрагмент кода показывает, как удалить частный список рассылки.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
client.deleteDistributionList(distributionLists[0], true);
~~~
#### **Удаление без списка**
Следующий фрагмент кода показывает, как удалить без списка.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("идентификатор списка");
client.deleteDistributionList(distributionList, true);
~~~