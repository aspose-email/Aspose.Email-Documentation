---
title: "Работа с конфигурацией пользователя на сервере"
url: /ru/java/working-with-user-configuration-on-server/
weight: 110
type: docs
---


## **Управление конфигурацией пользователя**
Aspose.Email для Java можно использовать для управления конфигурацией пользователя на Exchange Server с помощью класса [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient). Этот класс использует Exchange Web Services, которые доступны только в Exchange Server 2007 и более поздних версиях. В этой статье мы рассмотрим, как читать, создавать, обновлять и удалять конфигурации пользователя на Exchange Server 2010. Для всех функций, описанных в этой статье, требуется Microsoft Exchange Server 2010 Service Pack 1. Следующий кодовый фрагмент показывает, как подключиться к Exchange Server 2010 во всех примерах этой статьи.


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
### **Чтение конфигурации пользователя**
Чтобы получить информацию о конфигурации пользователя для конкретной папки из Exchange Server:

1. Подключитесь к Exchange Server, используя класс IEWSClient.
1. Вызовите метод IEWSClient.getUserConfiguration(), чтобы получить конфигурацию пользователя для папки.
1. Отобразите свойства конфигурации пользователя, такие как ID, имя и элементы словаря в виде пар ключ-значение.

Следующий кодовый фрагмент показывает, как читать конфигурацию пользователя.


~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Подключено к Exchange 2010");

// Получить конфигурацию пользователя для папки "Входящие"
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = client.getUserConfiguration(userConfigName);

System.out.println("Идентификатор конфигурации: " + userConfig.getId());
System.out.println("Имя конфигурации: " + userConfig.getUserConfigurationName().getName());
System.out.println("Пары ключ-значение:");
// преобразование foreach в while
for (Object key : userConfig.getDictionary().keySet()) {
    System.out.println(key + ": " + userConfig.getDictionary().get(key).toString());
}
~~~
### **Создание конфигураций пользователя**
Чтобы создать конфигурацию пользователя для конкретной папки на Exchange Server:

1. Подключитесь к Exchange Server, используя класс IEWSClient.
1. Вызовите метод IEWSClient.createUserConfiguration(), чтобы создать конфигурацию пользователя для папки.

Следующий кодовый фрагмент показывает, как создавать конфигурации пользователя.


~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Подключено к Exchange 2010");

// Создать конфигурацию пользователя для папки "Входящие"
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = new UserConfiguration(userConfigName);
userConfig.getDictionary().put("key1", "value1");
userConfig.getDictionary().put("key2", "value2");
userConfig.getDictionary().put("key3", "value3");
client.createUserConfiguration(userConfig);
~~~
### **Обновление конфигурации пользователя**
Чтобы обновить конфигурацию пользователя для конкретной папки в Exchange Server:

1. Подключитесь к Exchange Server, используя класс IEWSClient.
1. Вызовите метод IEWSClient.updateUserConfiguration(), чтобы обновить конфигурацию пользователя для папки.

Следующий кодовый фрагмент показывает, как обновить конфигурацию пользователя.


~~~Java
IEWSClient client = getExchangeEWSClient();
System.out.println("Подключено к Exchange 2010");

// Создать конфигурацию пользователя для папки "Входящие"
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
UserConfiguration userConfig = client.getUserConfiguration(userConfigName);
userConfig.setId(null);

// Обновить конфигурацию пользователя
userConfig.getDictionary().put("key1", "new-value1");
client.updateUserConfiguration(userConfig);
~~~
### **Удаление конфигурации пользователя**
Чтобы удалить конфигурацию пользователя для конкретной папки в Exchange Server:

1. Подключитесь к Exchange Server, используя класс IEWSClient.
1. Вызовите метод IEWSClient.deleteUserConfiguration(), чтобы удалить конфигурацию пользователя для папки.

Следующий кодовый фрагмент показывает, как удалить конфигурацию пользователя.


~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);
System.out.println("Подключено к Exchange 2010");

// Удалить конфигурацию пользователя
UserConfigurationName userConfigName = new UserConfigurationName("inbox.config", client.getMailboxInfo().getInboxUri());
client.deleteUserConfiguration(userConfigName);
~~~