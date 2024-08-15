---
title: "Trabajando con la configuración de usuario en el servidor"
url: /es/java/working-with-user-configuration-on-server/
weight: 110
type: docs
---


## **Administración de la configuración de usuario**
Aspose.Email para Java se puede usar para administrar la configuración de usuario en un servidor de Exchange con [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) clase. Esta clase usa los servicios web de Exchange, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo, veremos cómo leer, crear, actualizar y eliminar las configuraciones de usuario en Exchange Server 2010. Todas las funciones descritas en este artículo requieren el Service Pack 1 de Microsoft Exchange Server 2010. El siguiente fragmento de código muestra cómo conectarse a Exchange Server 2010 en todos los ejemplos de este artículo.



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
### **Lectura de la configuración del usuario**
Para obtener la información de configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese a Exchange Server mediante la clase IewsClient.
1. Llame al método IewsClient.getUserConfiguration () para obtener la configuración de usuario de una carpeta.
1. Muestre las propiedades de configuración del usuario, como el ID, el nombre y los elementos del diccionario, como pares clave-valor.

El siguiente fragmento de código muestra cómo leer la configuración del usuario.



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
### **Creación de configuraciones de usuario**
Para crear la configuración de usuario para una carpeta específica en un servidor Exchange:

1. Conéctese al servidor Exchange mediante la clase IEWSClient.
1. Llame al método IewsClient.createUserConfiguration () para crear la configuración de usuario para una carpeta.

El siguiente fragmento de código muestra cómo crear configuraciones de usuario.



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
### **Actualización de la configuración de usuario**
Para actualizar la configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante la clase IEWSClient.
1. Llame al método IewsClient.UpdateUserConfiguration () para actualizar la configuración de usuario de una carpeta.

El siguiente fragmento de código muestra cómo actualizar la configuración del usuario.



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
### **Eliminar la configuración de usuario**
Para eliminar la configuración de usuario de una carpeta específica del servidor Exchange:

1. Conéctese al servidor Exchange mediante la clase IEWSClient.
1. Llame al método IewsClient.deleteUserConfiguration () para eliminar la configuración de usuario de una carpeta.

El siguiente fragmento de código muestra cómo eliminar la configuración de usuario.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Delete User Configuration
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
client.deleteUserConfiguration(userConfigName);
~~~