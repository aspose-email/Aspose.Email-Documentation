---
title: "Trabajando con la Configuración de Usuario en el Servidor"
url: /es/java/working-with-user-configuration-on-server/
weight: 110
type: docs
---


## **Gestionando la Configuración de Usuario**
Aspose.Email para Java se puede utilizar para gestionar la configuración de usuario en un Exchange Server con la clase [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Esta clase utiliza Exchange Web Services, que solo están disponibles en Exchange Server 2007 y versiones posteriores. En este artículo, veremos cómo leer, crear, actualizar y eliminar configuraciones de usuario en Exchange Server 2010. Se requiere Microsoft Exchange Server 2010 Service Pack 1 para todas las funciones descritas en este artículo. El siguiente fragmento de código muestra cómo conectarse a Exchange Server 2010 en todos los ejemplos de este artículo.



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
### **Leyendo la Configuración de Usuario**
Para obtener la información de la configuración de usuario de una carpeta específica del Exchange Server:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.getUserConfiguration() para obtener la configuración de usuario para una carpeta.
1. Muestre las propiedades de la configuración de usuario como ID, nombre y elementos del diccionario como pares clave-valor.

El siguiente fragmento de código muestra cómo leer la configuración de usuario.



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
### **Creando Configuraciones de Usuario**
Para crear la configuración de usuario para una carpeta específica en un Exchange Server:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.createUserConfiguration() para crear la configuración de usuario para una carpeta.

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
### **Actualizando la Configuración de Usuario**
Para actualizar la configuración de usuario para una carpeta específica en el Exchange Server:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.updateUserConfiguration() para actualizar la configuración de usuario para una carpeta.

El siguiente fragmento de código muestra cómo actualizar la configuración de usuario.



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
### **Eliminando la Configuración de Usuario**
Para eliminar la configuración de usuario para una carpeta específica en el Exchange Server:

1. Conéctese al Exchange Server utilizando la clase IEWSClient.
1. Llame al método IEWSClient.deleteUserConfiguration() para eliminar la configuración de usuario para una carpeta.

El siguiente fragmento de código muestra cómo eliminar la configuración de usuario.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Delete User Configuration
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
client.deleteUserConfiguration(userConfigName);
~~~