---
title: Working with Distribution Lists on Exchange Server
type: docs
weight: 70
url: /java/working-with-distribution-lists-on-exchange-server/
---


## **Working with Distribution Lists**
Aspose.Email API provides the capability to create and read distributions lists from the Exchange server. Distribution lists can be created on the server as well as members can be added to it using the [IEWSClient](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient). This article shows how to work with distribution lists on the Exchange server.
### **Creating Distribution List**
The following code snippet shows you how to create a distribution list.



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
#### **Fetch Private Distribution List**
The following code snippet shows you how to fetch a private distribution list.



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


#### **Expand Public Distribution List**
The following code snippet shows you how to expand the public distribution List.



~~~Java
MailAddressCollection members = client.expandDistributionList(new MailAddress("public.distribution.list@host.com"));
for (MailAddress member : (Iterable<MailAddress>) members) {
    System.out.println(member.getAddress());
}
~~~
### **Adding members**
#### **Adding members to Private Distribution List**
The following code snippet shows you how to add members to a private distribution list.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address4@host.com");
newMembers.add("address5@host.com");
client.addToDistributionList(distributionLists[0], newMembers);
~~~
#### **Add members without listing**
The following code snippet shows you how to add members without listing.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("list's id");
distributionList.setChangeKey("list's change key");
MailAddressCollection newMembers = new MailAddressCollection();
newMembers.add("address6@host.com");
client.addToDistributionList(distributionList, newMembers);
~~~
#### **Send to Private Distribution List**
The following code snippet shows you how to send a message to a private distribution list.



~~~Java
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddress distributionListAddress = distributionLists[0].toMailAddress();
MailMessage message = new MailMessage(new MailAddress("from@host.com"), distributionListAddress);
message.setSubject("sendToPrivateDistributionList");
client.send(message);
~~~
### **Deleting members**
#### **Deleting members from Private Distribution List**
The following code snippet shows you how to delete members from a private distribution list.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
MailAddressCollection members = client.fetchDistributionList(distributionLists[0]);
MailAddressCollection membersToDelete = new MailAddressCollection();
membersToDelete.addMailAddress(members.get_Item(0));
membersToDelete.addMailAddress(members.get_Item(1));
client.deleteFromDistributionList(distributionLists[0], membersToDelete);
~~~
#### **Delete members without listing**
The following code snippet shows you how to delete members without listing.



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


#### **Delete Private Distribution List**
The following code snippet shows you how to delete a private distribution list.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList[] distributionLists = client.listDistributionLists();
client.deleteDistributionList(distributionLists[0], true);
~~~
#### **Delete without Listing**
The following code snippet shows you how to delete without listing.



~~~Java
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
ExchangeDistributionList distributionList = new ExchangeDistributionList();
distributionList.setId("list's id");
client.deleteDistributionList(distributionList, true);
~~~