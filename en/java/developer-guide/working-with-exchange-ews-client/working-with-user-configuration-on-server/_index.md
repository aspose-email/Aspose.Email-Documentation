---
title: Working with User Configuration on Server
type: docs
weight: 110
url: /java/working-with-user-configuration-on-server/
---


## **Managing User Configuration**
Aspose.Email for Java can be used to manage user configuration on an Exchange Server with the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class. This class uses Exchange Web Services, which are only available in Exchange Server 2007 and later releases. In this article, we will see how to read, create, update, and delete user configurations on Exchange Server 2010. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features described in this article. The following code snippet shows you how to connect to Exchange Server 2010 in all the examples in this article.



~~~Java
private static IEWSClient getExchangeEWSClient() {
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String domain = "";
    final String username = "username@ASE305.onmicrosoft.com";
    final String password = "password";
    NetworkCredential credentials = new NetworkCredential(username, password, domain);
    IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
    return client;
}
~~~
### **Reading User Configuration**
To get the user configuration information of a specific folder from the Exchange Server:

1. Connect to Exchange Server using the IEWSClient class.
1. Call the IEWSClient.getUserConfiguration() method to get the user configuration for a folder.
1. Display the user configuration properties like ID, name and dictionary items as key-value pairs.

The following code snippet shows you how to read user configuration.



~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Connected to Exchange 2010");

// Get the User Configuration for Inbox folder
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = client.getUserConfiguration(userConfigName);

System.out.println("Configuration Id: " + userConfig.getId());
System.out.println("Configuration Name: " + userConfig.getUserConfigurationName().getName());
System.out.println("Key value pairs:");
// foreach to while statements conversion
for (Object key : userConfig.getDictionary().keySet()) {
    System.out.println(key + ": " + userConfig.getDictionary().get(key).toString());
}
~~~
### **Creating User Configurations**
To create the user configuration for a specific folder on an Exchange Server:

1. Connect to the Exchange Server using the IEWSClient class.
1. Call the IEWSClient.createUserConfiguration() method to create the user configuration for a folder.

The following code snippet shows you how to creating user configurations.



~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Connected to Exchange 2010");

// Create the User Configuration for Inbox folder
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = new UserConfiguration(userConfigName);
userConfig.getDictionary().put("key1", "value1");
userConfig.getDictionary().put("key2", "value2");
userConfig.getDictionary().put("key3", "value3");
client.createUserConfiguration(userConfig);
~~~
### **Updating User Configuration**
To update the user configuration for a specific folder in the Exchange Server:

1. Connect to the Exchange Server using the IEWSClient class.
1. Call the IEWSClient.updateUserConfiguration() method to update the user configuration for a folder.

The following code snippet shows you how to update user configuration.



~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Connected to Exchange 2010");

// Create the User Configuration for Inbox folder
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = client.getUserConfiguration(userConfigName);
userConfig.setId(null);

// Update User Configuration
userConfig.getDictionary().put("key1", "new-value1");
client.updateUserConfiguration(userConfig);
~~~
### **Deleting User Configuration**
To delete the user configuration for a specific folder in the Exchange Server:

1. Connect to the Exchange Server using the IEWSClient class.
1. Call the IEWSClient.deleteUserConfiguration() method to delete the user configuration for a folder.

The following code snippet shows you how to delete user configuration.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Delete User Configuration
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
client.deleteUserConfiguration(userConfigName);
~~~