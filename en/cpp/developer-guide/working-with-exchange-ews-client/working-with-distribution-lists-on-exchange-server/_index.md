---
title: Manage Distribution Lists on Exchange Server with EWS in C++
ArticleTitle: Manage Distribution Lists on Exchange Server with EWS
type: docs
weight: 70
url: /cpp/manage-distribution-lists-on-exchange-server-ews/
description: Learn how to create, fetch, expand, update, and delete Exchange distribution lists using Aspose.Email and EWS.
---

**Aspose.Email for C++** provides full support for creating, reading, updating, and deleting Exchange distribution lists through the [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client). Using EWS, you can manage private and public distribution lists, add or remove members, fetch list details, and send messages to distribution lists programmatically.


## **Create a Distribution List**

Use [CreateDistributionList()](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a90be45117ca5a575fd8d01ca33ee1f46) to create a new private distribution list and define its members.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatePrivateDistributionList-CreatePrivateDistributionList.cpp" >}}
## **Fetch a Private Distribution List**
The following code snippet shows you how to retrieve all private lists and enumerate their members.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FetchPrivateDistributionList-FetchPrivateDistributionList.cpp" >}}

## **Expand a Public Distribution List**                                                                                                                                                                           
The following code snippet shows you how to expand public lists by supplying their email address.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ExpandPublicDistributionList-ExpandPublicDistributionList.cpp" >}}
## **Add Members to a Private Distribution List**
### **Add after Listing**
The following code snippet shows you how to add members to a private distribution list.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddMembersToPrivateDistributionList-AddMembersToPrivateDistributionList.cpp" >}}
### **Add without Listing**
The following code snippet shows you how to add members without listing.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-AddMembersWithoutListing-AddMembersWithoutListing.cpp" >}}
### **Send Email to a Private Distribution List**
The following code snippet shows you how to send emails to a private distribution list.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-SendEmailToPrivateDistributionList-SendEmailToPrivateDistributionList.cpp" >}}
## **Delete Members from a Private Distribution List**
### **Delete after Listing**
The following code snippet shows you how to delete members from a private distribution list.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMembersFromPrivateDistributionList-DeleteMembersFromPrivateDistributionList.cpp" >}}
### **Delete without Listing**
The following code snippet shows you how to delete members without listing.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteMembersWithoutListing-DeleteMembersWithoutListing.cpp" >}}
## **Delete a Private Distribution List**
### **Delete after Listing**
The following code snippet shows you how to delete a private distribution list.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeletePrivateDistributionList-DeletePrivateDistributionList.cpp" >}}
### **Delete without Listing**
The following code snippet shows you how to delete without listing.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteWithoutListing-DeleteWithoutListing.cpp" >}}
