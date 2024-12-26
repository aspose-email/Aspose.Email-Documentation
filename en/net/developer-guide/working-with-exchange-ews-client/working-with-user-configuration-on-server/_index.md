---
title: Manage User Configurations on Exchange Server Using EWS in C#
ArticleTitle: Manage User Configurations on Exchange Server with EWS
type: docs
weight: 110
url: /net/manage-user-configuration-on--exchange-server/
---


Aspose.Email for .NET can be used to manage user configuration on an Exchange Server with the [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/) class. This class uses Exchange Web Services, which are only available in Exchange Server 2007 and later releases. In this article, we will see how to read, create, update, and delete user configurations on Exchange Server 2010. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features described in this article. The following code snippet shows you how to connect to Exchange Server 2010 in all the examples in this article.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cs" >}}

## **Read User Configurations**

To get the user configuration information of a specific folder from the Exchange Server:

1. Connect to Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Call the [IEWSClient.GetUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/getuserconfiguration/#getuserconfiguration) method to get the user configuration for a folder.
1. Display the user configuration properties like ID, name and dictionary items as key-value pairs.

The following code snippet shows you how to read user configuration.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-ReadUserConfiguration-ReadUserConfiguration.cs" >}}

## **Create User Configurations**

To create the user configuration for a specific folder on an Exchange Server:

1. Connect to the Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Call the [IEWSClient.CreateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/createuserconfiguration/#createuserconfiguration) method to create the user configuration for a folder.

The following code snippet shows you how to create user configurations.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-CreatUserConfigurations-CreatUserConfigurations.cs" >}}

## **Update User Configurations**

To update the user configuration for a specific folder in the Exchange Server:

1. Connect to the Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Call the [IEWSClient.UpdateUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/updateuserconfiguration/#updateuserconfiguration) method to update the user configuration for a folder.

The following code snippet shows you how to update user configuration.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-UpdateUserConfiguration-UpdatUserConfiguration.cs" >}}

## **Delete User Configurations**

To delete the user configuration for a specific folder in the Exchange Server:

1. Connect to the Exchange Server using the [IEWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/) interface.
1. Call the [IEWSClient.DeleteUserConfiguration()](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/deleteuserconfiguration/#deleteuserconfiguration) method to delete the user configuration for a folder.

The following code snippet shows you how to delete user configuration.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Exchange_EWS-DeleteUserConfiguration-DeleteUserConfiguration.cs" >}}
