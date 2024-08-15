---
title: "Работа с пользовательской конфигурацией на сервере"
url: /ru/java/working-with-user-configuration-on-server/
weight: 110
type: docs
---


## **Управление пользовательской конфигурацией**
Aspose.Email для Java можно использовать для управления пользовательской конфигурацией на сервере Exchange с помощью [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) класс. В этом классе используются веб-службы Exchange, доступные только в Exchange Server 2007 и более поздних версиях. В этой статье мы рассмотрим, как читать, создавать, обновлять и удалять пользовательские конфигурации в Exchange Server 2010. Для всех функций, описанных в этой статье, требуется пакет обновления 1 для Microsoft Exchange Server 2010. В следующем фрагменте кода показано, как подключиться к Exchange Server 2010 во всех примерах этой статьи.



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
### **Чтение пользовательской конфигурации**
Чтобы получить информацию о пользовательской конфигурации определенной папки с сервера Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.getUserConfiguration (), чтобы получить пользовательскую конфигурацию папки.
1. Отображайте свойства пользовательской конфигурации, такие как идентификатор, имя и элементы словаря, в виде пар ключ-значение.

В следующем фрагменте кода показано, как читать конфигурацию пользователя.



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
### **Создание пользовательских конфигураций**
Чтобы создать пользовательскую конфигурацию для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.createUserConfiguration (), чтобы создать пользовательскую конфигурацию папки.

В следующем фрагменте кода показано, как создавать пользовательские конфигурации.



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
### **Обновление пользовательской конфигурации**
Чтобы обновить конфигурацию пользователя для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.updateUserConfiguration (), чтобы обновить пользовательскую конфигурацию папки.

В следующем фрагменте кода показано, как обновить конфигурацию пользователя.



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
### **Удаление пользовательской конфигурации**
Чтобы удалить пользовательскую конфигурацию для определенной папки на сервере Exchange, выполните следующие действия:

1. Подключитесь к серверу Exchange с помощью класса IEWSClient.
1. Вызовите метод IEWSClient.deleteUserConfiguration (), чтобы удалить пользовательскую конфигурацию папки.

В следующем фрагменте кода показано, как удалить пользовательскую конфигурацию.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Connected to Exchange 2010");

// Delete User Configuration
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
client.deleteUserConfiguration(userConfigName);
~~~