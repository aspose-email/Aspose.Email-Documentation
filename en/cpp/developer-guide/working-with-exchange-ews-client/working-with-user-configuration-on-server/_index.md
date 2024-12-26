---
title: Working with User Configuration on Server
ArticleTitle: Working with User Configuration on Server
type: docs
weight: 110
url: /cpp/working-with-user-configuration-on-server/
---

## **Managing User Configuration**
Aspose.Email API can be used to manage user configuration on an Exchange Server with the [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) class. This class uses Exchange Web Services, which are only available in Exchange Server 2007 and later releases. In this article, we will see how to read, create, update, and delete user configurations on Exchange Server 2010. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features described in this article. The following code snippet shows you how to connect to Exchange Server 2010 in all the examples in this article.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
### **Reading User Configuration**
To get the user configuration information of a specific folder from the Exchange Server:

1. Connect to Exchange Server using [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Call the [GetUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a33a6fd6cd562b05c84b656a3c2515111) method to get the user configuration for a folder.
1. Display the user configuration properties like ID, name and dictionary items as key-value pairs.

The following code snippet shows you how to read user configuration.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cpp" >}}
### **Creating User Configurations**
To create the user configuration for a specific folder on the Exchange Server:

1. Connect to the Exchange Server using [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Call the [CreateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a5dfcc5761b64ed0d0da8a6e45fc768db) method to create the user configuration for a folder.

The following code snippet shows you how to create user configurations.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cpp" >}}
### **Updating User Configuration**
To update the user configuration for a specific folder in the Exchange Server:

1. Connect to the Exchange Server using [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Call the [UpdateUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a0abf4f3032f63918fca528cbf1d4418e) method to update the user configuration for a folder.

The following code snippet shows you how to update user configuration.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-UpdateUserConfiguration-UpdateUserConfiguration.cpp" >}}
### **Deleting User Configuration**
To delete the user configuration for a specific folder in the Exchange Server:

1. Connect to the Exchange Server using [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
1. Call the [DeleteUserConfiguration()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#a7e0d6d6b432cf8db13af6638b639806c) method to delete the user configuration for a folder.

The following code snippet shows you how to delete user configuration.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cpp" >}}
